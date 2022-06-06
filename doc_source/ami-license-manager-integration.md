# Contract pricing for AMI products with AWS License Manager<a name="ami-license-manager-integration"></a>

For Amazon Machine Image \(AMI\)\-based products with contract pricing, you use AWS License Manager to associate licenses with your product\. 

AWS License Manager is a license management tool that enables your application to track and update licenses \(also known as entitlements\) that have been purchased by a customer\. This section provides information about how to integrate your product with AWS License Manager\. After the integration is complete, you can publish your product listing on AWS Marketplace\.

For more information about AWS License Manager, refer to the [AWS License Manager User Guide](https://docs.aws.amazon.com/license-manager/latest/userguide/license-manager.html) and the [AWS License Manager](https://docs.aws.amazon.com/cli/latest/reference/license-manager/index.html) section of the *AWS CLI Command Reference*\.

**Note**  
Customers can't launch new instances of the AMI after the contract expiry period\. However, during the contract duration, they can launch any number of instances\. These licenses are not node\-locked or tied to particular instances\.
**Private Offer Creation**– Sellers can generate private offers for the products using the Private offer creation tool in the AWS Marketplace Management Portal\.
**Reporting** – You can set up data feeds by setting up an Amazon S3 bucket in the **Report** section in the AWS Marketplace Management Portal\. For more information, refer to [Seller reports and data feeds](reports-and-data-feed.md)\.

## License models<a name="license-models"></a>

AWS Marketplace integration with AWS License Manager supports two license models:
+ [Configurable license model](#config-lic-model)
+ [Tiered license model](#tiered-lic-model)

### Configurable license model<a name="config-lic-model"></a>

The configurable license model \(also known as the quantifiable license model\) entitles a buyer to a specific quantity of resources after a buyer has procured a license\. 

You set a pricing dimension and a per unit price\. Then, buyer can choose the quantity of the resources that they want to purchase\.

**Example of pricing dimension and per unit price**  
You can set a pricing dimension \(such as data backup\) and per unit price \(such as $30/unit\)  
The buyer can choose to purchase 5, 10, or 20 units\.   
Your product tracks and meters usage to measure the quantity of resources consumed\.

With the configuration model, the entitlements are counted in one of two ways:
+ [Drawdown licenses](#drawndown-lic)
+ [Floating licenses](#floating-lic) 

#### Drawdown licenses<a name="drawndown-lic"></a>

 The license is drawn from the pool of allowed amount of licenses upon use\. That entitlement is checked out permanently and can't be returned to the license pool\.

**Example of processing a limited amount of data**  
A user is entitled to process 500 GB of data\. As they continue to process data, the quantity is drawn from the pool of 500 GB until all 500 GB licenses are consumed\.

For drawdown licenses, you can use the `CheckoutLicense` API operation to check out license units that are consumed\. 

**Example of backup to S3 for a number of units/year**  
You have a storage product that allows backup to Amazon Simple Storage Service \(Amazon S3\) for up to 1024 units for data for one year\. Your application can be launched by using multiple Amazon EC2 instances\. Your application has a mechanism to track and aggregate data\. Your software calls the `CheckoutLicense` API operation with the Product ID upon every backup or at fixed intervals to update the consumed quantities\.   
In this example, your software calls `CheckoutLicense` to check out 10 units of data\. When the total capacity reaches the backup limit that the customer has purchased, the API call fails\.

**Request**

```
linux-machine ~]$ aws license-manager checkout-license\
--product-sku "2205b290-19e6-4c76-9eea-377d6bf7la47" \
--checkout-type "PERPETUAL" \
--key-fingerprint "aws:294406891311:AWS/Marketplace:issuer-fingerprint" \
--entitlements "Name=DataConsumption, Value=l0, Unit=Count" \
--client-token "AKIAIOSFODNN7EXAMPLE"
```

**Response**

```
{
  "CheckoutType": "PERPETUAL",
  "EntitlementsAllowed": [
    {      
      "Name": "DataConsumption", 
      "Count": 10,
      "Units": "Count",
      "Value": "Enabled"
    }
},
  "Expiration":    "2021-04-22Tl9:02: 36",
  "IssuedAt": "2021-04-22Tl8:02:36",
  "LicenseArn": "arn:aws:license-manager::294406891311:license:l-16bf01b...",
  "LicenseConsumptionToken":  "AKIAIOSFODNN7EXAMPLE"
}
```

#### Floating licenses<a name="floating-lic"></a>

 The license is returned to the pool of the allowed amount of licenses after use\.

**Example of number of users from a fixed upper limit**  
A user is entitled to 500 simultaneous users on the application\. As users log in and log out, the users are drawn and returned to the pool of 500 users\. However, the application can't draw more than 500 users from the pool because 500 simultaneous users is the fixed upper limit\.

For floating licenses, you can use the `CheckInLicense` API operation to return the license units to the entitlement pool\. 

**Example of number of concurrent users for one year**  
Your product is priced based on number of concurrent users\. The customer purchases a license for 10 users for one year\. The customer launches the software by providing AWS Identity and Access Management \(IAM\) permissions\. When a user logs in, your application calls the `CheckoutLicense` API operation to reduce the quantity by 1\. When the user logs out, the application returns that license to the pool by calling the `CheckInLicense` API operation\. If you don't call `CheckInLicense`, the license unit will be automatically checked in after 1 hour\.

**Note**  
In the following Request, the `key-fingerprint` isn't a placeholder value but the actual value of the fingerprint with which all licenses will be published\.

**Request**

```
linux-machine ~]$ aws license-manager checkout-license\
--product-sku "2205b290-19e6-4c76-9eea-377d6bf7la47" \
--checkout-type "PROVISIONAL" \
--key-fingerprint "aws:294406891311:AWS/Marketplace:issuer-fingerprint" \
--entitlements "Name=ReadOnlyUSers, Value=l0, Unit=Count" \
--client-token "AKIAIOSFODNN7EXAMPLE"
```

**Response**

```
{
  "CheckoutType": "PROVISIONAL",
  "EntitlementsAllowed": [
    {
      "Name": "ReadOnlyUsers", 
      "Count": 10,
      "Units": "Count",
      "Value": "Enabled"
    }
},
  "Expiration": "2021-04-22Tl9:02: 36",
  "IssuedAt": "2021-04-22Tl8:02:36",
  "LicenseArn": "arn:aws:license-manager::294406891311:license:l-16bf01b...",
  "LicenseConsumptionToken": "AKIAIOSFODNN7EXAMPLE"
}
```

### Tiered license model<a name="tiered-lic-model"></a>

The tiered license model entitles a buyer to a specific level, or tier, of application features after a buyer has procured a license\. 

You create tiers for your product, such as Basic, Intermediate, and Premium\. The buyer then selects one of the predefined tiers\.

The application doesn't need to track or meter usage of the application\.

With the tiered license model, the entitlements aren't counted but instead signify a tier of service that was procured by the customer\. 

If you want to offer bundled features together, we recommend using the tiered license model\. 

**Example of Basic, Intermediate, and Premium tiers**  
A customer can sign a contract for one of three possible tiers of the software: Basic, Intermediate, or Premium\. Each of these tiers has its own pricing\. Your software can identify the tier that the customer has signed up for by invoking the `CheckoutLicense` API operation and specifying all possible tiers in the request\.   
The response of the request contains the entitlement corresponding to the tier the customer has procured\. Based on this information, the software can provision the appropriate customer experience\.

#### Request<a name="tiered-request"></a>

```
linux-machine  ~]$ aws  license-manager   checkout-license\
--product-sku  "2205b290-19e6-4c76-9eea-377d6bf7la47"  \
--checkout-type  "PROVISIONAL"  \
--key-fingerprint  "aws:294406891311:AWS/Marketplace:issuer-fingerprint" \
--entitlements  "Name=BasicTier,  Unit=None"   "Name=IntermediateTier,  Unit=None"	\ "Name=PremiumTier, Unit=None"
```

#### Response<a name="tiered-response"></a>

```
{ 
  "CheckoutType": "PROVISIONAL",
  "EntitlementsAllowed": [
    {
      "Name": "IntermediateTier", 
      "Units": "None"
    }
},
  "Expiration": "2021-04-22Tl9:02:36",
  "IssuedAt": "2021-04-22Tl8:02:36",
  "LicenseArn": "arn:aws:license-manager::294406891311:license:l-16bf01b...",
  "LicenseConsumptionToken": "AKIAIOSFODNN7EXAMPLE"
}
```

## Integration workflow<a name="LM-workflow"></a>

The following steps show the workflow for integrating your AMI product with AWS License Manager:

1. Seller creates a product with AWS License Manager integration\.

1. Seller lists the product on AWS Marketplace\.

1. Buyer finds the product on AWS Marketplace and purchases it\.

1. A license is sent to the buyer in their AWS account\.

1. Buyer uses the software by launching the Amazon Elastic Compute Cloud \(Amazon EC2\) instance, Amazon Elastic Container Service \(Amazon ECS\) task, or Amazon Elastic Kubernetes Service \(Amazon EKS\) pod software, The customer deploys by using an IAM role\.

1. Software reads the license in the buyer's AWS License Manager account, discovers the entitlements purchased, and provisions the features accordingly\. 
**Note**  
License Manager doesn't do any tracking or updates; this is done by the seller’s application\.

## License Manager integration prerequisites<a name="LM-prereqs"></a>

Before publishing the product, you must do the following:

1. Create a new AMI product in the AWS Marketplace Management Portal, and make a note of its product code\.

1. Fill out the Product Load Form \(PLF\) with the necessary price information, and return it to us for processing\.

1. Use an IAM role for the task or pod running your application with the IAM permissions necessary to call `CheckoutLicense`, `ExtendLicenseConsumption`, and `CheckInLicense`\.

   The required IAM permissions are detailed in the following IAM policy\.

   ```
   {
      "Version":"2012-10-17",
      "Statement":[
         {
            "Sid":"VisualEditorO",
            "Effect":"Allow",
            "Action":[
               "license-manager:CheckoutLicense",
               "license-manager:GetLicense",
               "license-manager:CheckInLicense",
               "license-manager:ExtendLicenseConsumption",
               "license-manager:ListReceivedLicenses"
            ],
            "Resource":"*"
         }
      ]
   }
   ```

1. Make a test call to the `RegisterUsage` API operation with a record for all of the pricing dimensions you deﬁne\.

## Integrating an AMI\-based product with AWS License Manager<a name="integrate-with-LM"></a>

You can integrate your AMI\-based product with License Manager by using the [AWS License Manager](https://docs.aws.amazon.com/license-manager/latest/APIReference/Welcome.html) API\. Launch the Amazon EC2 instances by using AWS Marketplace AMI\-based products\. 

**Note**  
Make sure that you have completed the [License Manager integration prerequisites](#LM-prereqs) before you perform the following procedure\. 

**To integrate your AMI\-based product with License Manager**

1. Complete the procedure in [Creating a test license in License Manager](#creating-test-license)\. You must create a test license in License Manager for testing your integration\.

1. Run the [GetLicense](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_GetLicense.html) API operation using the license Amazon Resource Name \(ARN\) that you obtained in step 1\. Note the value of the `KeyFingerprint` attribute of the `GetLicense` response for later use\. 

1. Download and include the latest public AWS SDK in your application\. 

1. To verify that the buyer is entitled to use a license for your application, run the [CheckoutLicense](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_CheckoutLicense.html) API operation\. Use the entitlements details and the key fingerprint of the test license that you obtained in step 1\. 

   If there are no entitlements found for the license, or the entitlement maximum count is exceeded, the `CheckoutLicense` API operation returns `NoEntitlementsAllowedException`\. If the entitlements are valid, or available to use, the `CheckoutLicense` operation returns a successful response with the requested entitlements and their values\.

1. \(Required for floating entitlements only\) Run the [CheckinLicense](https://docs.aws.amazon.com/license-manager/latest/APIReference/API_CheckInLicense.html) API operation using the `LicenseConsumptionToken` that was received in the `CheckoutLicense` response\. This action releases previously checked\-out entitlements back into the pool of available entitlements\.

1. After you successfully verify the License Manager integration with the test license that you created in step 1, update the key fingerprint in your code to `aws:294406891311:AWS/Marketplace:issuer-fingerprint`\. Now, you're ready to work with licenses issued by AWS Marketplace\.

Follow the release process of building the application to an AMI product and then submit the product to AWS Marketplace following the product publishing process\.

### Creating a test license in License Manager<a name="creating-test-license"></a>

You use version 2 of the AWS Command Line Interface \(AWS CLI\) to create a test license in AWS License Manager\. This test license is only used for verifying and testing the AWS License Manager integration\. After the testing is completed, you can delete the test license\. The actual license is generated by AWS Marketplace with a different key fingerprint\.

AWS Marketplace supports two types of entitlements in AWS License Manager\. However, only one type can be enabled for a product\. When you create a license, including a test license, you must specify one of the following types of entitlements: 

**Tiered entitlements ** – The tiered license model entitles the customer to certain application features\. Customers can't define the quantity of units they want to purchase\. However, they can select a single predefined package or tier\. Customers can modify the contract later to subscribe to another tier\.

**Configurable entitlements ** – The configurable license model grants entitlements to a certain quantity of resources when the customer procures a license\. The customer chooses the quantity of units they want to purchase during the subscription process and will be billed based on the unit price\. Customers can also subscribe to multiple dimensions\.

The required parameters for use in the `CheckoutLicense` API operation are as follows:
+ `CheckoutType` – The valid values are `Perpetual` or `Provisional`:
  + `Perpetual` – Used when the quantity of entitlements checked out will be exhausted from the pool\. Example: Buyer is entitled to process 500 GB of data\. As they continue to process data, the quantity is drawn down and exhausted from the pool of 500 GB\. Gets the status of a purchased license on whether the license is expired or about to be expired to send a notification to the customer\.
  + `Provisional` – Used for floating license entitlements where entitlements are checked out of the pool and returned back after use\. Example: User is entitled to 500 simultaneous users in the application\. As users log in and log out, the users are drawn and returned to the pool of 500 users\. For more information about floating license entitlements, see [Seller issued licenses in AWS License Manager\.](https://docs.aws.amazon.com/license-manager/latest/userguide/seller-issued-licenses.html)
+ `ClientToken` – Unique, case\-sensitive identifier to ensure the exact result occurs and is the same no matter how many times attempted\. We recommend that you use a random universally unique identifier \(UUID\) for each request\.
+ `Entitlements` – List of entitlements to be checked out\.
  + For tiered entitlements, provide `Name` and `Unit` properties as follows:

    `{`

    `"Name": "<Entitlement_Name>",`

    `"Unit": "None"`

    `}`
  + For configurable entitlements, provide `Name`, `Unit`, and `Value`properties as follows:

    `{`

    `"Name": "<Entitlement_Name>",`

    `"Unit": "<Entitlement_Unit>",`

    `"Value": <Desired_Count>{`

    \}
+ `KeyFingerprint` – Use this key fingerprint to verify that the license is issued by AWS Marketplace\. The key fingerprint for licenses issued by AWS Marketplace is as follows:

  `aws:294406891311:AWS/Marketplace:issuer-fingerprint`
+ `Product SKU` – Product ID with a Globally Unique Identifier \(GUID\) format that is associated with an AWS Marketplace product\.

**Example of a configurable entitlement**  
The following is an example of a request that uses the `CheckoutLicense` API operation to check out a configurable entitlement named `PowerUsers`\.  

```
aws license-manager checkout-license \
   product-sku "2205b290-19e6-4c76-9eea-377d6bf71a47" \
   checkout-type "PROVISIONAL" \
   client-token "79464194dca9429698cc774587a603a1" \"Statement":[
   entitlements "Name=PowerUsers,Value=1,Unit=Count" \ 
   key-fingerprint "aws:294406891311:AWS/Marketplace:issuer-fingerprint"
```

**Example of a tiered entitlement**  
The following is an example of a request that uses the `CheckoutLicense` API operation to check out a feature entitlement named `EnterpriseEdition`\.  

```
aws license-manager checkout-license \
   --product-sku "2205b290-19e6-4c76-9eea-377d6bf71a47" \
   --checkout-type "PROVISIONAL" \
   --client-token "79464194dca9429698cc774587a603a1" \
   --entitlements "Name=EnterpriseEdition,Unit=None" \
   --key-fingerprint "aws:294406891311:AWS/Marketplace:issuer-fingerprint"
```

**To create a test license for your AMI\-based product**

1. From your local environment with AWS CLI v2 installed, run the following script\. The script creates the test license and configures the appropriate product details\.

   ```
   #!/bin/bash
   
      # Replace with intended product ID on AWS Marketplace
      PRODUCT_ID=<REPLACE-WITH-PRODUCT-ID>
   
      # Replace with license recipient's AWS Account ID
      BENEFICIARY_ACCOUNT_ID=<REPLACE-WITH-BENEFICIARY-ACCOUNT-ID>\ 
      
      # Replace with your product's name
      PRODUCT_NAME="Test Product"
      
      # Replace with your seller name on AWS Marketplace
      SELLER_OF_RECORD="Test Seller" 
      
      # Replace with intended license name
      LICENSE_NAME="AWSMP Test License"
      
      # Replace with desired contract dimensions
      # More info here: https://docs.aws.amazon.com/license-manager/latest/APIReference/API_Entitlement.html
      CONFIGURABLE_ENTITLEMENTS='[
       {
         "Name": "ReadOnly",
         "MaxCount": 5,
         "Overage": false,
         "Unit": "Count",
         "AllowCheckIn": true
       }
    ]'
   
      TIERED_ENTITLEMENTS='[
       {
         "Name": "EnterpriseUsage", 
         "Value": "Enabled",
         "Unit": "None"
        
    ]'
   
      # Format "yyyy-mm-ddTHH:mm:ss.SSSZ"
      # This creates a validity period of 10 days starting the current day
      # Can be updated to desired dates
      VALIDITY_START=$(date +%Y-%m-%dT%H:%M:%S.%SZ)
      VALIDITY_END=$(date -v +10d +%Y-%m-%dT%H:%M:%S.%SZ)
   
      # Configuration for consumption of the license as set on Marketplace products
      CONSUMPTION_CONFIG='{
        "RenewType": "None",
        "ProvisionalConfiguration": {
          "MaxTimeToLiveInMinutes": 60
        }
      }'
   
      # License's home Region
      HOME_REGION=us-east-1
   
      # License issuer's name
      ISSUER=Self  
   
      # Run AWS CLI command to create a license
   aws license-manager create-license \
     --license-name "${LICENSE_NAME}" \
     --product-name "${PRODUCT_NAME}" \
     --product-sku "${PRODUCT_ID}" \
     --issuer Name="${ISSUER}" \
     --beneficiary "${BENEFICIARY_ACCOUNT_ID}" \
     --validity Begin="${VALIDITY_START}",End="${VALIDITY_END}" \
     --entitlements "${CONFIGURABLE_ENTITLEMENTS}" \ # Replace with `TIERED_ENTITLEMENTS` if desired
     --home-region "${HOME_REGION}" \
     --region "${HOME_REGION}" \
     --consumption-configuration "${CONSUMPTION_CONFIG}" \
     --client-token $(uuidgen)
   ```

1. Grant the license using the AWS License Manager console\. For more information, see [distribute an entitlement](https://docs.aws.amazon.com/license-manager/latest/userguide/granted-licenses.html#distribute-entitlement.) in the *License Manager User Guide*\.

1. Sign in to the AWS account that acts as a buyer account\. Go to the AWS License Manager console to accept and activate the granted licenses\. For more information, see [manage your granted licenses](https://docs.aws.amazon.com/license-manager/latest/userguide/granted-licenses.html#manage-granted-licenses) in the *License Manager User Guide*\.

1. Run the following command in your environment\.

   ```
   aws license-manager checkout-license \
      product-sku "${PRODUCT_ID}" \
      checkout-type "PROVISIONAL" \ 
      key-fingerprint "aws:294406891311:AWS/Marketplace:issuer-fingerprint" \
      entitlements "${CONFIGURABLE_ENTITLEMENTS}" \
      client-token $(uuidgen)
   ```

   The previous command uses `PROVISIONAL` as the value for the `CheckoutType` parameter\. If the entitlement uses a drawdown license, use `PERPETUAL` for the value\.

### License Manager API calls<a name="LM-API-calls"></a>

To manage the licenses stored in the customer's License Manager account, your software can use the following API calls:
+ `GetLicense` – Gets the status of a purchased license on whether the license is expired or about to be expired to send a notification to the customer\.
+ `CheckoutLicense` – Discovers licenses that the user has purchased\. You can also use it to update the license quantity when the user has consumed some quantity of licenses\. With `CheckoutLicense`, you can keep checking out the quantities of the licenses used by the customer\. When the customer exhausts all the licenses, this call returns an error\. For information about the suggested cadence to run `CheckoutLicense`, see [License renewals and upgrades](#lic-renew-upgrade)\.
+ `ExtendLicenseConsumption` – In case of floating dimensions, when the software check outs a license, it will return the license to the pool automatically after 60 minutes\. If you want to extend the time the license remains checked out, your software can call `ExtendLicenseConsumption` to extend the license for another 60 minutes\.
+ `CheckInLicense` – In case of floating dimensions, when you want to return the license to the entitlement pool, use `CheckInLicense`\.
+ `ListReceivedLicenses` – Lists licenses purchased by the buyer\.

## License renewals and upgrades<a name="lic-renew-upgrade"></a>

Customers can renew or upgrade their licenses on the AWS Marketplace Management Portal\. After they make an additional purchase, AWS Marketplace generates a new version of the license that reflects the new entitlements\. Your software reads the new entitlements using the same API calls\. You don't have to do anything different in terms of License Manager Integration to handle renewals and upgrades\.

Due to license renewals, upgrades, cancellations, and so on, we recommend that your product performs the `CheckoutLicense` API call at a regular cadence while the product is in use\. By using the `CheckoutLicense` API operation at a regular cadence, the product can detect changes in entitlements such as upgrades and expiry\.

We recommend that you perform the `CheckoutLicense` API call every 15 minutes\. 