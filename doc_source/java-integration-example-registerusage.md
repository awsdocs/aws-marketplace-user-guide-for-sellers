# Integrating your container product with the AWS Marketplace Metering Service using the AWS SDK for Java<a name="java-integration-example-registerusage"></a>

The following steps outline an example implementation using the AWS SDK for Java to integrate with the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html)'s `RegisterUsage` action\. For the full source code, see [RegisterUsage Java example](#registerusage-java-example)\. Many of these steps apply regardless of the language\. 

**Example steps for AWS Marketplace Metering Service integration**

1. Sign into the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour)\.

1. From **Assets** choose **Containers** to start creating a new container product\. Creating the product generates the product code for the product to integrate with your container image\. For more information about publishing, see [Publishing container products](container-product-getting-started.md#container-product-publishing)\. For information about setting IAM permissions, see [AWS Marketplace metering and entitlement API permissions](iam-user-policy-for-aws-marketplace-actions.md)\.

1.  Download the public [AWS Java SDK](https://aws.amazon.com/sdk-for-java/)\. 
**Important**  
 To call the metering APIs from Amazon EKS, you must [use a supported AWS SDK](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts-minimum-sdk.html) and run on an Amazon EKS cluster running Kubernetes 1\.13 or later\. 

1.  \(Optional\) If you're integrating with the `RegisterUsage` action and you want to perform digital signature verification, you need to configure the [BouncyCastle](https://mvnrepository.com/artifact/org.bouncycastle/bcprov-jdk15on) signature verification library in your application classpath\.

   If you want to use JSON Web Token \(JWT\), you must also include [JWT Java](https://jwt.io/) libraries in your application classpath\. Using JWT provides a simpler approach to signature verification but is not required, and you can use standalone BouncyCastle instead\. Whether you use JWT or BouncyCastle, you need to use a build system such as Maven to include transitive dependencies of BouncyCastle or JWT in your application classpath\.

   ```
   // Required for signature verification using code sample
   <dependency>
       <groupId>org.bouncycastle</groupId>
       <artifactId>bcpkix-jdk15on</artifactId>
       <version>1.60</version>
   </dependency>
   
   // This one is only required for JWT
   <dependency>
       <groupId>com.nimbusds</groupId>
       <artifactId>nimbus-jose-jwt</artifactId>
       <version>6.0</version>
   </dependency>
   ```

1.  Call `RegisterUsage` from each paid container image in your product offering\. `ProductCode` and `PublicKeyVersion` are required parameters, and all other inputs are optional\. The following is an example payload for `RegisterUsage`\. 

   ```
   {
       "ProductCode" : "string", // (required)
       "PublicKeyVersion": 1,    // (required)
       "Nonce": "string",        // (optional) to scope down the registration
                                 //            to a specific running software
                                 //            instance and guard against
                                 //            replay attacks
   }
   ```

1.  `RegisterUsage` generates an RSA\-PSS digital signature using SHA\-256 that you can use to verify request authenticity\. The signature includes the following fields: `ProductCode`, `PublicKeyVersion`, and `Nonce`\. To verify the digital signature, you must retain these fields from the request\. The following code is an example response to a `RegisterUsage` call\. 

   ```
   {
   "Signature": "<<JWT Token>>"
   }
   
   // Where the JWT Token is composed of 3 dot-separated, 
   // base-64 URL Encoded sections.
   // e.g. eyJhbGcVCJ9.eyJzdWIMzkwMjJ9.rrO9Qw0SXRWTe
   
   // Section 1: Header/Algorithm
   {
   "alg": "PS256",
   "typ": "JWT"
   }
   
   // Section 2: Payload
   {
   "ProductCode" : "string",
   "PublicKeyVersion": 1,
   "Nonce": "string",
   "iat": date // JWT issued at claim 
   }
   
   // Section 3: RSA-PSS SHA256 signature
   "rrO9Q4FEi3gweH3X4lrt2okf5zwIatUUwERlw016wTy_21Nv8S..."
   ```

1. Rebuild a new version of your Docker container image that includes the `RegisterUsage` call, tag the container, and push it to any Docker registry that is compatible with Amazon ECS or Amazon EKS, such as Amazon ECR or Docker Hub\. If you are using Amazon ECR, ensure that the account launching the Amazon ECS task or Amazon EKS pod has permissions on the Amazon ECR repository\. Otherwise, execution fails\.
**Note**  
 If you use a private Docker Hub repository, follow the steps in [Private Registry Authentication for Tasks](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/private-auth.html) in the *Amazon Elastic Container Service Developer Guide*\. 

1.  Create an [IAM](https://aws.amazon.com/iam/) role that grants permission for your container to call `RegisterUsage`, as defined in the following code\. You must supply this IAM role in the [Task Role](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html#task_role_arn) parameter of the Amazon ECS task or Amazon EKS pod definition\.

   ```
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Action": [
                   "aws-marketplace:RegisterUsage"
                   ],
                   "Effect": "Allow",
                   "Resource": "*"
           }
       ]
   }
   ```

1. Create an Amazon ECS task or Amazon EKS pod definition that references the container that has integrated with AWS Marketplace and references the IAM role that you created in step 7\. You should enable AWS CloudTrail logging in the task definition if you want to see logging\. 

1. Create an Amazon ECS or Amazon EKS cluster to execute your task or pod\. For more information about creating an Amazon ECS cluster, see [Creating a Cluster](https://docs.aws.amazon.com/AmazonECS/latest/userguide/create_cluster.html) in the *Amazon Elastic Container Service Developer Guide*\. For more information about creating an Amazon EKS cluster \(using Kubernetes version 1\.1\.3\.x or later\), see [Creating an Amazon EKS Cluster](https://docs.aws.amazon.com/eks/latest/userguide/create_cluster.html)\.

1. Configure the Amazon ECS or Amazon EKS cluster and launch the Amazon ECS task definition or Amazon EKS pod that you created, in the us\-east\-1 AWS Region\. It's only during this testing process, before the product is live, that you have to use this region\.

1. When you get a valid response back from `RegisterUsage`, you can begin creating your container product\. For questions, contact the [AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

## RegisterUsage Java example<a name="registerusage-java-example"></a>

The following example uses the AWS SDK for Java and AWS Marketplace Metering Service to call the `RegisterUsage` operation\. Signature verification is optional, but if you want to perform signature verification, you must include the required digital signature verification libraries\. This example is for illustrative purposes only\. 

```
import com.amazonaws.auth.PEM;
import com.amazonaws.services.marketplacemetering.AWSMarketplaceMetering;
import com.amazonaws.services.marketplacemetering.AWSMarketplaceMeteringClientBuilder;
import com.amazonaws.services.marketplacemetering.model.RegisterUsageRequest;
import com.amazonaws.services.marketplacemetering.model.RegisterUsageResult;
import com.amazonaws.util.json.Jackson;
import com.fasterxml.jackson.databind.JsonNode;
import com.nimbusds.jose.JWSObject;
import com.nimbusds.jose.JWSVerifier;
import com.nimbusds.jose.crypto.RSASSAVerifier;
import java.io.ByteArrayInputStream;
import java.nio.charset.StandardCharsets;
import java.security.PublicKey;
import java.security.Security;
import java.security.Signature;
import java.security.interfaces.RSAPublicKey;
import java.util.Base64;
import java.util.Optional;
import java.util.UUID;
import org.bouncycastle.jce.provider.BouncyCastleProvider;

/**
 * Class for making calls out to AWS Marketplace Metering Service.
 */
class RegisterUsage {

    private static final String PRODUCT_CODE = ".......";

    private final AWSMarketplaceMetering registerUsageClient;
    private final SignatureVerifier signatureVerifier;
    private final int publicKeyVersion;

    public RegisterUsage(final SignatureVerifier signatureVerifier) {
        this.signatureVerifier = signatureVerifier;
        this.publicKeyVersion = PublicKeyProvider.PUBLIC_KEY_VERSION;
        this.registerUsageClient = AWSMarketplaceMeteringClientBuilder.standard().build();
    }

    /**
     * Shows how to call RegisterUsage client and verify digital signature.
     */
    public void callRegisterUsage() {
        RegisterUsageRequest request = new RegisterUsageRequest()
                .withProductCode(PRODUCT_CODE)
                .withPublicKeyVersion(publicKeyVersion)
                .withNonce(UUID.randomUUID().toString());

        // Execute call to RegisterUsage (only need to call once at container startup)
        RegisterUsageResult result = this.registerUsageClient.registerUsage(request);

        // Verify Digital Signature w/o JWT
        boolean isSignatureValid = this.signatureVerifier.verify(request, result);
        if (!isSignatureValid) {
            throw new RuntimeException("Revoke entitlement, digital signature invalid.");
        }
    }
}

/**
 * Signature verification class with both a JWT-library based verification
 * and a non-library based implementation.
 */
class SignatureVerifier {
    private static BouncyCastleProvider BC = new BouncyCastleProvider();

    private static final String SIGNATURE_ALGORITHM = "SHA256withRSA/PSS";

    private final PublicKey publicKey;

    public SignatureVerifier(PublicKeyProvider publicKeyProvider) {
        this.publicKey = publicKeyProvider.getPublicKey().orElse(null);
        Security.addProvider(BC);
    }

    /**
     * Example signature verification using the NimbusJOSEJWT library to verify the JWT Token.
     *
     * @param request RegisterUsage Request.
     * @param result  RegisterUsage Result.
     * @return true if the token matches.
     */
    public boolean verifyUsingNimbusJOSEJWT(final RegisterUsageRequest request, final RegisterUsageResult result) {
        if (!getPublicKey().isPresent()) {
            return false;
        }

        try {
            JWSVerifier verifier = new RSASSAVerifier((RSAPublicKey) getPublicKey().get());
            JWSObject jwsObject = JWSObject.parse(result.getSignature());
            return jwsObject.verify(verifier) && validatePayload(jwsObject.getPayload().toString(), request, result);
        } catch (Exception e) {
            // log error
            return false;
        }
    }

    /**
     * Example signature verification without any JWT library support.
     *
     * @param request RegisterUsage Request.
     * @param result  RegisterUsage Result.
     * @return true if the token matches.
     */
    public boolean verify(final RegisterUsageRequest request, final RegisterUsageResult result) {
        if (!getPublicKey().isPresent()) {
            return false;
        }
        try {
            String[] jwtParts = result.getSignature().split("\\.");
            String header = jwtParts[0];
            String payload = jwtParts[1];
            String payloadSignature = jwtParts[2];

            Signature signature = Signature.getInstance(SIGNATURE_ALGORITHM, BC);
            signature.initVerify(getPublicKey().get());
            signature.update(String.format("%s.%s", header, payload).getBytes(StandardCharsets.UTF_8));
            boolean verified = signature.verify(Base64.getUrlDecoder()
                    .decode(payloadSignature.getBytes(StandardCharsets.UTF_8)));

            String decodedPayload = new String(Base64.getUrlDecoder().decode(payload));
            return verified && validatePayload(decodedPayload, request, result);
        } catch (Exception e) {
            // log error
            return false;
        }
    }

    /**
     * Validate each value in the returned payload matches values originally
     * supplied in the request to RegisterUsage. TimeToLiveInMillis and
     * PublicKeyExpirationTimestamp will have the values in the payload compared
     * to values in the signature
     */
    private boolean validatePayload(final String payload, final RegisterUsageRequest request,
                                    final RegisterUsageResult result) {
        try {
            JsonNode payloadJson = Jackson.getObjectMapper().readTree(payload);
            boolean matches = payloadJson.get("productCode")
                    .asText()
                    .equals(request.getProductCode());
            matches = matches && payloadJson.get("nonce")
                    .asText()
                    .equals(request.getNonce());
            return matches = matches && payloadJson.get("publicKeyVersion")
                    .asText()
                    .equals(String.valueOf(request.getPublicKeyVersion()));

        } catch (Exception ex) {
            // log error
            return false;
        }
    }

    private Optional<PublicKey> getPublicKey() {
        return Optional.ofNullable(this.publicKey);
    }
}

/**
 * Public key provider taking advantage of the AWS PEM Utility.
 */
class PublicKeyProvider {
    // Replace with your public key. Ensure there are new-lines ("\n") in the
    // string after "-----BEGIN PUBLIC KEY-----\n" and before "\n-----END PUBLIC KEY-----".
    private static final String PUBLIC_KEY =
            "-----BEGIN PUBLIC KEY-----\n"
                    + "MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDdlatRjRjogo3WojgGHFHYLugd\n"
                    + "UWAY9iR3fy4arWNA1KoS8kVw33cJibXr8bvwUAUparCwlvdbH6dvEOfou0/gCFQs\n"
                    + "HUfQrSDv+MuSUMAe8jzKE4qW+jK+xQU9a03GUnKHkkle+Q0pX/g6jXZ7r1/xAK5D\n"
                    + "o2kQ+X5xK9cipRgEKwIDAQAB\n"
                    + "-----END PUBLIC KEY-----";

    public static final int PUBLIC_KEY_VERSION = 1;

    public Optional<PublicKey> getPublicKey() {
        try {
            return Optional.of(PEM.readPublicKey(new ByteArrayInputStream(
                    PUBLIC_KEY.getBytes(StandardCharsets.UTF_8))));
        } catch (Exception e) {
            // log error
            return Optional.empty();
        }
    }
}
```