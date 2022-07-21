# Integrating an AWS Marketplace for Containers Anywhere product with License Manager<a name="container-anywhere-license-manager-integration"></a>

Follow these instructions to integrate AWS License Manager with an AWS Marketplace for Containers Anywhere product for Amazon EKS Anywhere, Amazon ECS Anywhere, Amazon EC2, or on\-premises infrastructure\. 

For general information about the License Manager integration with AWS Marketplace, including available license models, see [Contract pricing for Container products with AWS License Manager](container-license-manager-integration.md)\. For more information about AWS License Manager, see the [AWS License Manager User Guide](https://docs.aws.amazon.com/license-manager/latest/userguide/license-manager.html) and the [AWS License Manager](https://docs.aws.amazon.com/cli/latest/reference/license-manager/index.html) section of the *AWS CLI Command Reference*\.

## Integrating an AWS Marketplace for Containers Anywhere product with License Manager<a name="containers-anywhere-integrate-with-LM"></a>

Use the following instructions to integrate your AWS Marketplace for Containers Anywhere product with AWS License Manager\.

**To integrate your AWS Marketplace for Containers Anywhere product with License Manager**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. Create a product ID for your container product by performing the following steps\. You will use this ID in your container image for license checks in a later step\.

   1. From the menu bar, expand **Assets**, and choose **Container**\.

   1. Enter a customer\-facing name for your product, and choose **Create**\. You can change this name later\.

   1. Make a note of the **Product ID**\. You will use it when you create or update the product pricing details\.
**Tip**  
If you lose your product ID, you can find it in the AWS Marketplace Management Portal by choosing **Container** from the **Assets** menu\. The **Containers** page shows a list of your products with their associated product IDs\.

1. Download the latest public AWS SDK and then install it in your container application\. You can find installation instructions for your preferred AWS SDK at [Tools to Build on AWS](https://aws.amazon.com/tools/)\.
**Note**  
To call the License Manager API operations from Amazon EKS Anywhere or a Kubernetes cluster that isn't provided by AWS, you must use a supported AWS SDK\. To view a list of supported AWS SDKs, see [Using a supported AWS SDK](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts-minimum-sdk.html)\.

1. Create an AWS License Manager client with a custom credential provider so that it can provide credentials to the container application deployed on AWS as well as on\-premises\. For complete source code for a custom credential provider, `LicenseCredentialProvider`, see the following sections:
   + [`LicenseManagerCredentialsProvider` \- Java implementation](#container-license-manager-cred-provider-java)
   + [`LicenseManagerCredentialsProvider` \- `Golang` implementation](#container-license-manager-cred-provider-golang)

    `LicenseCredentialsProvider` extends the AWS SDK’s default credential provider chain for on\-premises use by adding `LicenseManagerTokenCredentialsProvider`\. This provides credentials by using License Manager OIDC issued identity tokens in on\-premises environments\. You must include the source code for `LicenseCredentialsProvider` in your application classpath\.
**Note**  
Extending the `DefaultCredentialsProvider` allows the same container application to obtain credentials when running on AWS and when running in an on\-premises environment\. If the container application already uses a custom credential provider chain instead of the default, it can also be extended by adding `LicenseManagerTokenCredentialsProvider` to the custom chain\.

   The following code snippet is an example of creating an AWS License Manager client using Java\.

   ```
   LicenseManagerClientBuilder clientBuilder = LicenseManagerClient.builder().credentialsProvider(LicenseCredentialsProvider.create());
   ```

1. Call the `CheckoutLicense` API operation by using the `aws license-manager checkout-license` command from each paid container image in your product offering\. This checks that the buyer is entitled to use a license for your application\. If the buyer is entitled to the application, `CheckoutLicense` succeeds and returns the requested entitlements and their values\. If the buyer isn't entitled to the application, `CheckoutLicense` throws an exception\.

   The following parameters are required when calling the `CheckoutLicense` API operation:
   + `CheckoutType` – The valid values are `PROVISIONAL` or `PERPETUAL`:
     + Use `PERPETUAL` when the quantity of entitlements checked out will be exhausted from the pool\.

       Example: Buyer is entitled to process 500 GB of data\. As they continue to process data, the quantity is drawn down and exhausted from the pool of 500 GB\.
     + Use `PROVISIONAL` for floating license entitlements where the entitlements are checked out of the pool and returned after use\.

       Example: User is entitled to 500 simultaneous users on the application\. As users log in or log out, the users are drawn or returned to the pool of 500 users\. To learn more about floating license entitlements, see [Floating license entitlements with License Manager](#container-LM-floating-license)\.
   + `ClientToken` – A unique, case\-sensitive identifier\. We recommend using a random UUID for each unique request\.
   + `Entitlements` – A list of entitlements to be checked out\.
     + For feature entitlements, provide the `Name` and `Unit` properties as follows\.

       ```
       {
         "Name": "<Entitlement_Name>",
         "Unit": "None"
       }
       ```
     + For counted entitlements, provide the `Name`, `Unit`, and `Count` properties as follows\.

       ```
       {
         "Name": "<Entitlement_Name>",
         "Unit": "<Entitlement_Unit>",
         "Value": <Desired_Count>
       }
       ```
   + `KeyFingerprint` – The key fingerprint for licenses issued by AWS Marketplace is `aws:294406891311:AWS/Marketplace:issuer-fingerprint`\. Using this key fingerprint ensures that the license is issued by AWS Marketplace and not by an unreliable entity\.
   + `ProductSKU` – The Product ID generated on AWS Marketplace Management Portal in previous steps\.

   The following snippet is an example of a call using the `CheckoutLicense` API operation using the AWS CLI\.

   ```
   aws license-manager checkout-license \
   --product-sku "2205b290-19e6-4c76-9eea-377d6bf71a47" \
   --checkout-type "PROVISIONAL" \
   --client-token "79464194dca9429698cc774587a603a1" \
   --entitlements "Name=AWS::Marketplace::Usage/Drawdown/DataConsumption, Value=10, Unit=Gigabytes" \
   --key-fingerprint "aws:294406891311:AWS/Marketplace:issuer-fingerprint"
   ```
**Note**  
To check licenses, container applications require outbound network access to use License Manager\. Applications deployed on\-premises might experience unreliable or slow outbound network access\. These applications should include adequate retries when calling License Manager\. For more information, see [Best practices for integrating with License Manager for on\-premises deployments](#container-LM-best-practices-on-prem)\.

1. Call the `CheckoutLicense` API operation at a regular cadence to identify any changes to customers' licenses due to renewals, upgrades, or cancellations made on AWS Marketplace\. The cadence depends on the application\. We recommend checking licenses once a day to pick up changes automatically without any buyer intervention\.

   An application deployed on\-premises might have unreliable outbound network access to check licenses on a regular cadence\. In such cases, the application should use a cached licenses for sufficient resiliency\. For more information, see [Best practices for integrating with License Manager for on\-premises deployments](#container-LM-best-practices-on-prem)\.

1. After you integrate the `CheckoutLicense` call with your container application, build a new version of your Docker container image with the changes\.

1. Update your application’s Helm chart to accept a Kubernetes secret as optional input that contains configuration to access licenses using License Manager APIs\. The configuration secret will contain an identity token issued by License Manager and an AWS Identity and Access Management role which will be used by the custom credential provider described previously to get AWS credentials for calling License Manager APIs when the container application is deployed on\-premises\. Also, add the AWS Region as an input with a default value of `us-east-1`\.

   Buyers deploying the container application on\-premises can create the Kubernetes secret through the AWS Marketplace buyer experience for container products\. Provide the Kubernetes secret name as input to the `helm install` command\. The configuration secret is configured in the following format\.

   ```
   apiVersion: v1
   kind: Secret
   metadata:
     name: aws-marketplace-license-config
   type: Opaque
   stringData:
     license_token: <token_value> // License Manager issued JWT token
     iam_role: <role_arn> // AWS Identity and Access Management role to assume with license token
   ```

1. Update the application deployment template in the Helm chart for container images integrated with AWS License Manager to include the following:
   + Service account for pod – The service account is required for Helm deployments on Amazon EKS\. It's used to get permissions to call License Manager API operations by setting up IAM roles for the service account on the container image\. For more information about IAM roles for service accounts, see [IAM roles for service accounts](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts.html)\.
   + License access for on\-premises deployments – The license configuration secret is required to provide credentials and appropriate permissions to call License Manager API operations for Helm deployments in on\-premises environments\. Buyers will generate and provide the license secret to Helm from the AWS Marketplace buyer experience\.

   The following code snippet is a sample deployment specification with the service account, license configuration, and image pull secret\.

   ```
   apiVersion: apps/v1
   kind: Deployment
   metadata:
     name: example-app
   spec:
     replicas: 1
     selector:
       matchLabels:
         app: example-app
     template:
       metadata:
         labels:
           app: example-app
   spec:
         // Service account for pod
         serviceAccountName: {{ .Values.serviceAccountName }}
         containers:
           - name: example-app
             image: example-app
             ports:
               - containerPort: 8001
   // Add the following conditional attributes
   {{ - if .Values.awsmp.licenseConfigSecretName }}
             //Mount the license volume to the container image
             volumeMounts:
               - name: awsmp-product-license
                 mountPath: "/var/run/secrets/product-license"
             //Add following environment variable to container for credential
   provider
             env:
               - name: AWS_WEB_IDENTITY_REFRESH_TOKEN_FILE
                 value: "/var/run/secrets/product-license/license_token"
               - name: AWS_ROLE_ARN
                   valueFrom:
                       secretKeyRef:
                       name: {{ .Values.aws.licenseConfigSecretName }}
                       key: iam_role
         //Mount the license secret as a volume to the pod
         volumes:
           - name: awsmp-product-license
             secret:
               secretName: {{ .Values.aws.licenseConfigSecretName }}
               optional: true
   {{ - end }}
   ```
**Note**  
The license configuration secret is optional\. Buyers only use the value for on\-premises deployments\. For AWS deployments, the deployment specification must include a service account for the License Manager integrated images\.

1. Test the License Manager integration locally and on Amazon EKS by performing the steps in the following sections:

   1. [Testing License Manager integration locally](#container-testing-LM-integration-locally)

   1. [Testing License Manager integration on Amazon EKS](#container-testing-LM-integration-EKS)

1. After you successfully verify License Manager integration both on AWS and on\-premises, you can create your container product listing by following the steps in [Creating a container product](container-product-getting-started.md#create-container-product)\.

## Testing License Manager integration locally<a name="container-testing-LM-integration-locally"></a>

You can use minikube or any other setup to test License Manager integration on any Kubernetes cluster locally\. Make sure that the Kubernetes cluster has outbound internet access to call License Manager API operations\.

**To test a License Manager integration locally**

1. Create a test license in a test seller account with desired entitlements\. To set up a test license, see [CreateLicense](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_CreateLicense.html) in the *AWS License Manager API Reference*\. Or, use the following script to create a test license and then create a license grant to a test buyer account to consume the license\. The following script uses test seller account credentials\.

   ```
   read -p 'AWS Account for test buyer: ' TEST_BUYER_ACCOUNT_ID
   read -p 'License entitlements: ' ENTITLEMENTS
   
   # TEST_SELLER_ACCOUNT_ID="109876543210"
   # ENTITLEMENTS="{\"Name\": \"ByData\",\"MaxCount\": 1000,\"Overage\":true,\"Unit\": \"Gigabits\",\"AllowCheckIn\": true}"
   
   # Create License
   
   NOW=$(date +"%Y-%m-%dT00:00:00+00:00")
   
   PRODUCT_NAME="My awesome product"
   PRODUCT_SKU="c97b7825-44c4-4f42-b025-12baa4c171e0"
   
   LICENSE_BENEFICIARY=" arn:aws:iam::$TEST_BUYER_ACCOUNT_ID:root "
   LICENSE_ISSUER_NAME="test-seller"
   LICENSE_NAME="test-seller-license"
   
   CLIENT_TOKEN="b3920968-a94f-4547-af07-3dd232319367"
   CONSUMPTION_TTL=180
   CONSUMPTION_RENEW_TYPE="None"
   
   HOME_REGION="us-east-1"
   
   LICENSE_ARN=$(aws license-manager create-license --license-name "$LICENSE_NAME" --product-name "$PRODUCT_NAME" --product-sku "$PRODUCT_SKU" --issuer Name="$LICENSE_ISSUER_NAME" --home-region "$HOME_REGION" --validity Begin="$NOW" --entitlements "$ENTITLEMENTS" --beneficiary "$LICENSE_BENEFICIARY" --consumption-configuration RenewType="$CONSUMPTION_RENEW_TYPE",ProvisionalConfiguration={MaxTimeToLiveInMinutes=$CONSUMPTION_TTL} --client-token "$CLIENT_TOKEN" | jq -r ".LicenseArn" )
   
   echo "License arn: $LICENSE_ARN"
   
   # Create Grant
   
   GRANT_TOKEN="e9a14140-4fca-4219-8230-57511a6ea6"
   GRANT_NAME="test-grant"
   
   GRANT_ARN=$(aws license-manager create-grant --grant-name "$GRANT_NAME" --license-arn "$LICENSE_ARN" --principals "$LICENSE_BENEFICIARY" --home-region "$HOME_REGION" --client-token "$GRANT_TOKEN" --allowed-operations "CheckoutLicense" "CheckInLicense" "ExtendConsumptionLicense" "CreateToken" | jq -r ".GrantArn")
   
   echo "Grant arn: $GRANT_ARN"
   ```

1. Create a Kubernetes secret with the license token and IAM role using the secret format defined previously\. Use the License Manager `CreateToken` API operation to generate a license token\. Then, use the IAM `CreateRole` API operation to create an IAM role with permissions and a trust policy\. See the example in the following script\. The following script uses test buyer account credentials\.

   ```
   read -p 'AWS Account for test license: ' TEST_ACCOUNT_ID
   read -p 'License Arn' LICENSE_ARN
   # Create IAM Role
   ROLE_NAME="AWSLicenseManagerConsumptionTestRole"
   ROLE_DESCRIPTION="Role to test AWS License Manager integration on-prem"
   ROLE_POLICY_ARN="arn:aws:iam::aws:policy/service-role/AWSLicenseManagerConsumptionPolicy"
   ROLE_TRUST_POLICY="{\"Version\": \"2012-10-17\",\"Statement\": [{ \"Effect\":\"Allow\", \"Principal\": { \"Federated\": \"openid-license-manager.amazonaws.com\" }, \"Action\": \"sts:AssumeRoleWithWebIdentity\",\"Condition\": { \"ForAnyValue:StringLike\": { \"openid-license-manager.amazonaws.com:amr\": \"aws:license-manager:token-issuer-account-id:${TEST_ACCOUNT_ID}\" }}}]}"
   ROLE_SESSION_DURATION=3600
   
   ROLE_ARN=$(aws iam create-role --role-name "$ROLE_NAME" --description "$ROLE_DESCRIPTION" --assume-role-policy-document "$ROLE_TRUST_POLICY" --max-session-duration $ROLE_SESSION_DURATION | jq ".Role" | jq -r ".Arn")
   
   aws iam attach-role-policy --role-name "$ROLE_NAME" --policy-arn "$ROLE_POLICY_ARN"
   
   echo "Role arn: $ROLE_ARN"
   
   # Create Token
   CLIENT_TOKEN="b3920968-a94f-4547-af07-3dd232319367"
   
   TOKEN=$(aws license-manager create-token --license-arn $LICENSE_ARN --role-arns $ROLE_ARN --client-token $CLIENT_TOKEN | jq '.Token')
   
   echo "License access token: $TOKEN"c
   ```

1. Set up any Kubernetes cluster hosted outside AWS\. Use it to test that the container applications can connect to the AWS License Manager API from environments other than AWS and that the custom credential provider is well integrated in the application\.

1. Deploy the license token and IAM role generated previously into the local Kubernetes cluster\.

   ```
   kubectl create secret generic "awsmp-license-access-config" \
   --from-literal=license_token=${TOKEN} \
   --from-literal=iam_role=${ROLE_ARN}
   ```

1. Deploy your application through Helm with the secret name as input and verify that the application can call License Manager API operations to perform entitlement checks\. For Helm and deployment specification changes, refer to Step 9 in [Integrating an AWS Marketplace for Containers Anywhere product with License Manager](#containers-anywhere-integrate-with-LM)\.

## Testing License Manager integration on Amazon EKS<a name="container-testing-LM-integration-EKS"></a>

You can also test License Manager integration on Amazon EKS\. Test to make sure that the application can call License Manager API operations without the license configuration secret\. Also make sure that the service account can be used to set up IAM Roles for Service Accounts \(IRSA\) and provide relevant credentials to the application\.

**To test a License Manager integration on Amazon EKS**

1. Create a test license in a test seller account with the desired entitlements\. See [CreateLicense API reference](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_CreateLicense.html) to set up your test license or use the following script to create one and create a license grant to a test buyer account to consume the license\. The following script uses test seller account credentials\.

   ```
   read -p 'AWS Account for test buyer: ' TEST_BUYER_ACCOUNT_ID
   read -p 'License entitlements: ' ENTITLEMENTS
   
   # TEST_SELLER_ACCOUNT_ID="109876543210"
   # ENTITLEMENTS="{\"Name\": \"ByData\",\"MaxCount\": 1000,\"Overage\": true,\"Unit\": \"Gigabits\",\"AllowCheckIn\": true}"
   
   # Create License
   
   NOW=$(date +"%Y-%m-%dT00:00:00+00:00")
   
   PRODUCT_NAME="My awesome product"
   PRODUCT_SKU="c97b7825-44c4-4f42-b025-12baa4c171e0"
   
   LICENSE_BENEFICIARY=" arn:aws:iam::$TEST_BUYER_ACCOUNT_ID:root "
   LICENSE_ISSUER_NAME="test-seller"
   LICENSE_NAME="test-seller-license"
   
   CLIENT_TOKEN="b3920968-a94f-4547-af07-3dd232319367"
   CONSUMPTION_TTL=180
   CONSUMPTION_RENEW_TYPE="None"
   
   HOME_REGION="us-east-1"
   
   LICENSE_ARN=$(aws license-manager create-license --license-name "$LICENSE_NAME" --product-name "$PRODUCT_NAME" --product-sku "$PRODUCT_SKU" --issuer Name="$LICENSE_ISSUER_NAME" --home-region "$HOME_REGION" --validity Begin="$NOW" --entitlements "$ENTITLEMENTS" --beneficiary "$LICENSE_BENEFICIARY" --consumption-configuration RenewType="$CONSUMPTION_RENEW_TYPE",ProvisionalConfiguration={MaxTimeToLiveInMinutes=$CONSUMPTION_TTL} --client-token "$CLIENT_TOKEN" | jq -r ".LicenseArn" )
   
   echo "License arn: $LICENSE_ARN"
   
   # Create Grant
   
   GRANT_TOKEN="e9a14140-4fca-4219-8230-57511a6ea6"
   GRANT_NAME="test-grant"
   
   GRANT_ARN=$(aws license-manager create-grant --grant-name "$GRANT_NAME" --license-arn "$LICENSE_ARN" --principals "$LICENSE_BENEFICIARY" --home-region "$HOME_REGION" --client-token "$GRANT_TOKEN" --allowed-operations "CheckoutLicense" "CheckInLicense" "ExtendConsumptionLicense" "CreateToken" | jq -r ".GrantArn")
   
   echo "Grant arn: $GRANT_ARN"
   ```

1. Create a test Amazon EKS cluster of desired configurations, or run the following commands to use a default configuration\.

   ```
   aws ec2 create-key-pair --region us-west-2 --key-name eks-key-pair
   ```

   ```
   eksctl create cluster \
   --name awsmp-eks-test-example \
   --region us-west-2 \
   --with-oidc \
   --ssh-access \
   --ssh-public-key eks-key-pair
   ```

1. Create a service account for an existing cluster and associate it with an IAM role\. The following command creates an IAM role with the `AWSLicenseManagerConsumptionPolicy`\. Then, the command attaches it to the `test_sa` service account of the Amazon EKS cluster where the License Manager integrated images should be deployed\. As a result, the service account can get appropriate credentials to call License Manager API operations\.

   ```
   eksctl create iamserviceaccount \
   --name test_sa \
   --namespace test_namespace \
   --cluster awsmp-eks-test-example \
   --attach-policy-arn "arn:aws:iam::aws:policy/service-role/AWSLicenseManagerConsumptionPolicy" \
   --approve \
   --override-existing-serviceaccounts
   ```

1. Deploy the application through Helm in the service account where the IAM role is associated from the previous command\. Verify that the application can call License Manager API operations to perform entitlement checks\.

## Floating license entitlements with License Manager<a name="container-LM-floating-license"></a>

With floating licenses, as users log into the application, a license is drawn from the pool of available licenses\. As users log out, the licenses are added back to the pool of available licenses\.

For floating licenses, the application uses the `CheckoutLicense` API operation to check out entitlements from the entitlements pool when the resource is being used\. The response of the `CheckoutLicense` API operation includes a license consumption token which is a unique identifier for the checkout\. The license consumption token can perform additional actions on the entitlements that are checked out, such as checking them back into the license pool or extending the checkout\.

When the resource is no longer in use, the application uses the `CheckInLicense` API operation to check the entitlement back into the pool\.

```
aws license-manager check-in-license \
--license-consumption-token "f1603b3c1f574b7284db84a9e771ee12"
```

If checking a license back into the pool fails, for example, if the application crashes during the operation, the entitlement is checked back into the pool automatically after 60 minutes\. Because of this, if the resource is in use longer than 60 minutes, it's a best practice to keep the entitlement checked out of the pool\. To do this, use the `ExtendLicenseConsumption` API operation as long as the resource is being used\.

```
aws license-manager extend-license-consumption \
--license-consumption-token "f1603b3c1f574b7284db84a9e771ee12"
```

## Best practices for integrating with License Manager for on\-premises deployments<a name="container-LM-best-practices-on-prem"></a>

Container application deployments in an on\-premises environment might encounter unreliable outbound network access\. Use the following best practices to add resiliency to avoid service disruption to buyers due to potential issues caused by poor internet connectivity:
+ **Adequate retry** – Transient network issues can keep your application from connecting to AWS License Manager\. Implement retries for up to 30 minutes, with exponential back off\. This can help avoid short\-term outages or network issues\.
+ **Avoid hard limit** – Applications deployed in connected clusters can regularly check licenses to identify any changes due to upgrades or renewals\. With unreliable outbound access, the application might not be able to identify those changes\. Whenever possible, the application should avoid disruption of service to buyers due to inability to check licenses through License Manager\. Applications can fall back on a free\-trial or open\-source experience when the license expires and they can’t check if a license is valid\.
+ **Notify customers** – When using a cached license, any changes to the license \(including renewal or upgrades\) are not automatically reflected on the running workload\. Notify your customers \( that they must allow outbound access to the application again temporarily so the application can update its cached license\. For example, notify customers through the application itself or through its documentation\. Similarly, when falling back to a lower set of functionalities, notify customers that their entitlements are exhausted or the license is expired\. Then, they can choose to either upgrade or renew\.

## `LicenseManagerCredentialsProvider` \- Java implementation<a name="container-license-manager-cred-provider-java"></a>

`LicenseCredentialsProvider` extends the AWS SDK’s default credential provider chain for on\-premises use by adding `LicenseManagerTokenCredentialsProvider`\. 

**`LicenseCredentialsProvider`**

```
package com.amazon.awsmp.license;

import software.amazon.awssdk.auth.credentials.AwsCredentials;
import software.amazon.awssdk.auth.credentials.AwsCredentialsProvider;
import software.amazon.awssdk.auth.credentials.AwsCredentialsProviderChain;
import software.amazon.awssdk.auth.credentials.DefaultCredentialsProvider;
import software.amazon.awssdk.auth.credentials.internal.LazyAwsCredentialsProvider;
import software.amazon.awssdk.utils.SdkAutoCloseable;

public class LicenseCredentialsProvider implements AwsCredentialsProvider, SdkAutoCloseable {
    private static final LicenseCredentialsProvider CREDENTIALS_PROVIDER = new LicenseCredentialsProvider();
    private final LazyAwsCredentialsProvider providerChain;

    private LicenseCredentialsProvider() {
        this.providerChain = createChain();
    }

    public static LicenseCredentialsProvider create() {
        return CREDENTIALS_PROVIDER;
    }

    @Override
    public AwsCredentials resolveCredentials() {
        return this.providerChain.resolveCredentials();
    }

    @Override
    public void close() {
        this.providerChain.close();
    }

    private LazyAwsCredentialsProvider createChain() {
        return LazyAwsCredentialsProvider.create(() -> {
            AwsCredentialsProvider[] credentialsProviders = new AwsCredentialsProvider[]{
                    DefaultCredentialsProvider.create(),
                    LicenseManagerTokenCredentialsProvider.create()};

            return AwsCredentialsProviderChain.builder().reuseLastProviderEnabled(true)
                    .credentialsProviders(credentialsProviders).build();
        });
    }
}
```

**`LicenseManagerTokenCredentialsProvider`**

`LicenseManagerTokenCredentialsProvider` provides credentials by using License Manager OIDC issued identity tokens in on\-premises environments\. You must include the source code for `LicenseCredentialsProvider` in your application classpath\.

```
package com.amazon.awsmp.license;

import software.amazon.awssdk.auth.credentials.AnonymousCredentialsProvider;
import software.amazon.awssdk.auth.credentials.AwsCredentials;
import software.amazon.awssdk.auth.credentials.AwsCredentialsProvider;
import software.amazon.awssdk.core.SdkSystemSetting;
import software.amazon.awssdk.core.client.config.ClientOverrideConfiguration;
import software.amazon.awssdk.core.retry.RetryPolicyContext;
import software.amazon.awssdk.core.retry.conditions.OrRetryCondition;
import software.amazon.awssdk.core.retry.conditions.RetryCondition;
import software.amazon.awssdk.regions.Region;
import software.amazon.awssdk.regions.providers.DefaultAwsRegionProviderChain;
import software.amazon.awssdk.services.licensemanager.LicenseManagerClient;
import software.amazon.awssdk.services.licensemanager.model.GetAccessTokenRequest;
import software.amazon.awssdk.services.licensemanager.model.GetAccessTokenResponse;
import software.amazon.awssdk.services.sts.StsClient;
import software.amazon.awssdk.services.sts.auth.StsAssumeRoleWithWebIdentityCredentialsProvider;
import software.amazon.awssdk.services.sts.model.AssumeRoleWithWebIdentityRequest;
import software.amazon.awssdk.services.sts.model.IdpCommunicationErrorException;
import software.amazon.awssdk.utils.IoUtils;
import software.amazon.awssdk.utils.SdkAutoCloseable;
import software.amazon.awssdk.utils.StringUtils;
import software.amazon.awssdk.utils.SystemSetting;

import java.io.IOException;
import java.io.InputStream;
import java.io.UncheckedIOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.time.Duration;
import java.util.function.Supplier;

public class LicenseManagerTokenCredentialsProvider implements AwsCredentialsProvider, SdkAutoCloseable {

    private final StsAssumeRoleWithWebIdentityCredentialsProvider credentialsProvider;
    private final RuntimeException loadException;

    private Path licenseAccessTokenFile;
    private String roleArn;
    private String roleSessionName;
    private StsClient stsClient;
    private LicenseManagerClient lmClient;

    public static LicenseManagerTokenCredentialsProvider create() {
        return new Builder().build();
    }

    @Override
    public AwsCredentials resolveCredentials() {
        if (this.loadException != null) {
            throw this.loadException;
        }
        return this.credentialsProvider.resolveCredentials();
    }

    @Override
    public void close() {
        IoUtils.closeQuietly(this.credentialsProvider, null);
        IoUtils.closeQuietly(this.stsClient, null);
        IoUtils.closeIfCloseable(this.lmClient, null);
    }

    private LicenseManagerTokenCredentialsProvider(Builder builder) {
        StsAssumeRoleWithWebIdentityCredentialsProvider credentialsProvider = null;
        RuntimeException loadException = null;

        try {
            this.licenseAccessTokenFile = Paths.get(StringUtils.trim(LicenseSystemSetting.AWS_WEB_IDENTITY_REFRESH_TOKEN_FILE.getStringValueOrThrow()));
            this.roleArn = SdkSystemSetting.AWS_ROLE_ARN.getStringValueOrThrow();
            this.roleSessionName = SdkSystemSetting.AWS_ROLE_SESSION_NAME.getStringValue().orElse("aws-sdk-java-" + System.currentTimeMillis());
            this.stsClient = builder.stsClient != null ? builder.stsClient : StsClientFactory.create();
            this.lmClient = builder.lmClient != null ? builder.lmClient : LicenseManagerClientFactory.create();

            AssumeRoleWithWebIdentityRequest request = AssumeRoleWithWebIdentityRequest.builder()
                    .roleArn(this.roleArn).roleSessionName(this.roleSessionName).build();

            Supplier<AssumeRoleWithWebIdentityRequest> supplier = new AssumeRoleRequestSupplier(request,
                    this.licenseAccessTokenFile, this.lmClient);

            credentialsProvider = StsAssumeRoleWithWebIdentityCredentialsProvider.builder()
                    .stsClient(this.stsClient).refreshRequest(supplier).build();
        } catch (RuntimeException ex) {
            loadException = ex;
        }

        this.credentialsProvider = credentialsProvider;
        this.loadException = loadException;
    }

    public static final class Builder {
        private Path licenseAccessTokenFile;
        private String roleArn;
        private String roleSessionName;
        private StsClient stsClient;
        private LicenseManagerClient lmClient;

        public LicenseManagerTokenCredentialsProvider build() {
            return new LicenseManagerTokenCredentialsProvider(this);
        }

        public LicenseManagerTokenCredentialsProvider.Builder licenseAccessTokenFile(Path licenseAccessTokenFile) {
            this.licenseAccessTokenFile = licenseAccessTokenFile;
            return this;
        }

        public LicenseManagerTokenCredentialsProvider.Builder roleArn(String roleArn) {
            this.roleArn = roleArn;
            return this;
        }

        public LicenseManagerTokenCredentialsProvider.Builder roleSessionName(String roleSessionName) {
            this.roleSessionName = roleSessionName;
            return this;
        }

        public LicenseManagerTokenCredentialsProvider.Builder stsClient(StsClient stsClient) {
            this.stsClient = stsClient;
            return this;
        }

        public LicenseManagerTokenCredentialsProvider.Builder lmClient(LicenseManagerClient lmClient) {
            this.lmClient = lmClient;
            return this;
        }
    }

    private static final class AssumeRoleRequestSupplier implements Supplier {
        private final LicenseManagerClient lmClient;
        private final AssumeRoleWithWebIdentityRequest request;
        private final Path webIdentityRefreshTokenFile;

        AssumeRoleRequestSupplier(final AssumeRoleWithWebIdentityRequest request,
                                                 final Path webIdentityRefreshTokenFile,
                                                 final LicenseManagerClient lmClient) {
            this.lmClient = lmClient;
            this.request = request;
            this.webIdentityRefreshTokenFile = webIdentityRefreshTokenFile;
        }

        public AssumeRoleWithWebIdentityRequest get() {
            return this.request.toBuilder()
                    .webIdentityToken(getIdentityToken())
                    .build();
        }

        private String getIdentityToken() {
            return refreshIdToken(readRefreshToken(this.webIdentityRefreshTokenFile));
        }

        private String readRefreshToken(Path file) {
            try (InputStream webIdentityRefreshTokenStream = Files.newInputStream(file)) {
                return IoUtils.toUtf8String(webIdentityRefreshTokenStream);
            } catch (IOException e) {
                throw new UncheckedIOException(e);
            }
        }

        private String refreshIdToken(String licenseRefreshToken) {
            final GetAccessTokenRequest request = GetAccessTokenRequest.builder()
                    .token(licenseRefreshToken)
                    .build();

            GetAccessTokenResponse response = this.lmClient.getAccessToken(request);
            return response.accessToken();
        }
    }

    private static final class LicenseManagerClientFactory {
        private static final Duration DEFAULT_API_TIMEOUT = Duration.ofSeconds(30);
        private static final Duration DEFAULT_API_ATTEMPT_TIMEOUT = Duration.ofSeconds(10);

        public static LicenseManagerClient create() {
            return getLicenseManagerClient();
        }

        private static LicenseManagerClient getLicenseManagerClient() {
            ClientOverrideConfiguration configuration = ClientOverrideConfiguration.builder()
                    .apiCallTimeout(DEFAULT_API_TIMEOUT)
                    .apiCallAttemptTimeout(DEFAULT_API_ATTEMPT_TIMEOUT)
                    .build();

            LicenseManagerClient client = LicenseManagerClient.builder()
                    .region(configureLicenseManagerRegion())
                    .credentialsProvider(AnonymousCredentialsProvider.create())
                    .overrideConfiguration(configuration).build();
            return client;
        }

        private static Region configureLicenseManagerRegion() {
            Region defaultRegion = Region.US_EAST_1;

            Region region;
            try {
                region = (new DefaultAwsRegionProviderChain()).getRegion();
            } catch (RuntimeException ex) {
                region = defaultRegion;
            }
            return region;
        }
    }

    private static final class StsClientFactory {
        private static final Duration DEFAULT_API_TIMEOUT = Duration.ofSeconds(30);
        private static final Duration DEFAULT_API_ATTEMPT_TIMEOUT = Duration.ofSeconds(10);

        public static StsClient create() {
            return getStsClient();
        }

        private static StsClient getStsClient() {
            OrRetryCondition retryCondition = OrRetryCondition.create(new StsRetryCondition(),
                    RetryCondition.defaultRetryCondition());

            ClientOverrideConfiguration configuration = ClientOverrideConfiguration.builder()
                    .apiCallTimeout(DEFAULT_API_TIMEOUT)
                    .apiCallAttemptTimeout(DEFAULT_API_ATTEMPT_TIMEOUT)
                    .retryPolicy(r -> r.retryCondition(retryCondition))
                    .build();

            return StsClient.builder()
                    .region(configureStsRegion())
                    .credentialsProvider(AnonymousCredentialsProvider.create())
                    .overrideConfiguration(configuration).build();
        }

        private static Region configureStsRegion() {
            Region defaultRegion = Region.US_EAST_1;
            Region stsRegion;
            try {
                stsRegion = (new DefaultAwsRegionProviderChain()).getRegion();
            } catch (RuntimeException ex) {
                stsRegion = defaultRegion;
            }
            return stsRegion;
        }

        private static final class StsRetryCondition implements RetryCondition {
            public boolean shouldRetry(RetryPolicyContext context) {
                return context.exception() instanceof IdpCommunicationErrorException;
            }
        }
    }

    private enum LicenseSystemSetting implements SystemSetting {
        AWS_WEB_IDENTITY_REFRESH_TOKEN_FILE("aws.webIdentityRefreshTokenFile");

        private String systemProperty;
        private String defaultValue = null;

        LicenseSystemSetting(String systemProperty) {
            this.systemProperty = systemProperty;
        }

        @Override
        public String property() {
            return this.systemProperty;
        }

        @Override
        public String environmentVariable() {
            return this.name();
        }

        @Override
        public String defaultValue() {
            return this.defaultValue;
        }
    }
}
```

## `LicenseManagerCredentialsProvider` \- `Golang` implementation<a name="container-license-manager-cred-provider-golang"></a>

**`LicenseCredentialsProvider`**

`LicenseCredentialsProvider` extends the AWS SDK’s default credential provider chain for on\-premises use by adding `LicenseManagerTokenCredentialsProvider`\. 

```
package lib

import (
	"context"
	"fmt"
	"sync"

	"github.com/aws/aws-sdk-go-v2/aws"
	"github.com/aws/aws-sdk-go-v2/config"
)

// LicenseCredentialsProvider is the custom credential provider that can retrieve valid temporary aws credentials
type LicenseCredentialsProvider struct {
	fallBackProvider   aws.CredentialsProvider
	mux                sync.RWMutex
	licenseCredentials aws.Credentials
	err                error
}

// NewLicenseCredentialsProvider method will create a LicenseCredentialProvider Object which contains valid temporary aws credentials
func NewLicenseCredentialsProvider() (*LicenseCredentialsProvider, error) {
	licenseCredentialProvider := &LicenseCredentialsProvider{}
	fallBackProvider, err := createCredentialProvider()
	if err != nil {
		return licenseCredentialProvider, fmt.Errorf("failed to create LicenseCredentialsProvider, %w", err)
	}
	licenseCredentialProvider.fallBackProvider = fallBackProvider
	return licenseCredentialProvider, nil
}

// Retrieve method will retrieve temporary aws credentials from the credential provider
func (l *LicenseCredentialsProvider) Retrieve(ctx context.Context) (aws.Credentials, error) {
	l.mux.RLock()
	defer l.mux.RUnlock()
	l.licenseCredentials, l.err = l.fallBackProvider.Retrieve(ctx)
	return l.licenseCredentials, l.err
}

func createCredentialProvider() (aws.CredentialsProvider, error) {
	// LoadDefaultConfig will examine all "default" credential providers
	ctx := context.TODO()
	cfg, err := config.LoadDefaultConfig(ctx)
	if err != nil {
		return nil, fmt.Errorf("failed to create FallBackProvider, %w", err)
	}

	var useFallbackProvider bool
	if cfg.Credentials != nil {
		if _, err := cfg.Credentials.Retrieve(ctx); err != nil {
			// If the "default" credentials provider cannot retrieve credentials, enable fallback to customCredentialsProvider.
			useFallbackProvider = true
		}
	} else {
		useFallbackProvider = true
	}

	if useFallbackProvider {
		customProvider, err := newLicenseManagerTokenCredentialsProvider()
		if err != nil {
			return cfg.Credentials, fmt.Errorf("failed to create fallBackProvider, %w", err)
		}
		// wrap up customProvider with CredentialsCache to enable caching
		cfg.Credentials = aws.NewCredentialsCache(customProvider)
	}
	return cfg.Credentials, nil
}
```

**`LicenseManagerTokenCredentialsProvider`**

`LicenseManagerTokenCredentialsProvider` provides credentials by using License Manager OIDC issued identity tokens in on\-premises environments\. You must include the source code for `LicenseCredentialsProvider` in your application classpath\.

```
package lib

import (
	"context"
	"fmt"
	"io/ioutil"
	"os"
	"sync"
	"time"

	"github.com/aws/aws-sdk-go-v2/aws"
	"github.com/aws/aws-sdk-go-v2/config"
	"github.com/aws/aws-sdk-go-v2/service/sts"
)

const awsRefreshTokenFilePathEnvVar = "AWS_LICENSE_ACCESS_FILE"

// licenseManagerTokenCredentialsProvider defines and contains StsAssumeRoleWithWebIdentityProvider
type licenseManagerTokenCredentialsProvider struct {
	stsCredentialProvider *stsAssumeRoleWithWebIdentityProvider
	mux                   sync.RWMutex
	licenseCredentials    aws.Credentials
	err                   error
}

// Retrieve method will retrieve credentials from credential provider.
// Make this method public to make this provider satisfies CredentialProvider interface
func (a *licenseManagerTokenCredentialsProvider) Retrieve(ctx context.Context) (aws.Credentials, error) {
	a.mux.RLock()
	defer a.mux.RUnlock()
	a.licenseCredentials, a.err = a.stsCredentialProvider.Retrieve(ctx)
	return a.licenseCredentials, a.err
}

// newLicenseManagerTokenCredentialsProvider will create and return a LicenseManagerTokenCredentialsProvider Object which wraps up stsAssumeRoleWithWebIdentityProvider
func newLicenseManagerTokenCredentialsProvider() (*licenseManagerTokenCredentialsProvider, error) {
	// 1. Retrieve variables From yaml environment
	envConfig, err := config.NewEnvConfig()
	if err != nil {
		return &licenseManagerTokenCredentialsProvider{}, fmt.Errorf("failed to create LicenseManagerTokenCredentialsProvider, %w", err)
	}
	roleArn := envConfig.RoleARN
	var roleSessionName string
	if envConfig.RoleSessionName == "" {
		roleSessionName = fmt.Sprintf("aws-sdk-go-v2-%v", time.Now().UnixNano())
	} else {
		roleSessionName = envConfig.RoleSessionName
	}
	tokenFilePath := os.Getenv(awsRefreshTokenFilePathEnvVar)
	b, err := ioutil.ReadFile(tokenFilePath)
	if err != nil {
		return &licenseManagerTokenCredentialsProvider{}, fmt.Errorf("failed to create LicenseManagerTokenCredentialsProvider, %w", err)
	}
	refreshToken := aws.String(string(b))

	// 2. Create stsClient
	cfg, err := config.LoadDefaultConfig(context.TODO())
	if err != nil {
		return &licenseManagerTokenCredentialsProvider{}, fmt.Errorf("failed to create LicenseManagerTokenCredentialsProvider, %w", err)
	}
	stsClient := sts.NewFromConfig(cfg, func(o *sts.Options) {
		o.Region = configureStsClientRegion(cfg.Region)
		o.Credentials = aws.AnonymousCredentials{}
	})

	// 3. Configure StsAssumeRoleWithWebIdentityProvider
	stsCredentialProvider := newStsAssumeRoleWithWebIdentityProvider(stsClient, roleArn, roleSessionName, refreshToken)

	// 4. Build and return
	return &licenseManagerTokenCredentialsProvider{
		stsCredentialProvider: stsCredentialProvider,
	}, nil
}

func configureStsClientRegion(configRegion string) string {
	defaultRegion := "us-east-1"
	if configRegion == "" {
		return defaultRegion
	} else {
		return configRegion
	}
}
```