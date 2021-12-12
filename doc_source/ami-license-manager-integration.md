# AWS License Manager integration<a name="ami-license-manager-integration"></a>

For Amazon Machine Image \(AMI\)\-based products with contract pricing, you use AWS License Manager to associate licenses with your product\. 

AWS License Manager is a license management tool that enables your application to track and update licenses \(also known as entitlements\) that have been purchased by a customer\. This section provides information about how to integrate your product with AWS License Manager\. After the integration is complete, you can publish your product listing on AWS Marketplace\.

For more information about AWS License Manager, see the [AWS License Manager User Guide](https://docs.aws.amazon.com/license-manager/latest/userguide/license-manager.html) and the [AWS License Manager](https://docs.aws.amazon.com/cli/latest/reference/license-manager/index.html) section of the *AWS CLI Command Reference*\.

**Note**  
Customers can't launch new instances of the AMI after the contract expiry period\. However, during the contract duration, they can launch any number of instances\. These licenses are not node\-locked or tied to particular instances\.
**Private Offer Creation**– Sellers can generate private offers for the products using the Private offer creation tool in the AWS Marketplace Management Portal\.
**Reporting** – You can set up data feeds by setting up an Amazon S3 bucket in the **Report** section in the AWS Marketplace Management Portal\. For more information, see [Seller reports and data feeds](reports-and-data-feed.md)\.

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
A user is entitled to process 500GB of data\. As they continue to process data, the quantity is drawn from the pool of 500GB until all 500GB licenses are consumed\.

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
  "ProductSku": "2205b290-19e6-4c76-9eea-377d6bf7la47",
  "Fingerprint": "aws:294406891311:AWS/Marketplace:issuer-fingerprint", "CheckoutType": "PERPETUAL",
  "EntitlementsAllowed": [
    {      
      "Name": "DataConsumption", "Count": 10,
      "Units": "Count"
    }
},
  "Expiration":    "2021-04-22Tl9:02: 36",
  "IssuedAt": "2021-04-22Tl8:02:36",
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
  "ProductSku": "2205b290-19e6-4c76-9eea-377d6bf7la47",
  "Fingerprint": "aws:294406891311:AWS/Marketplace:issuer-fingerprint", "CheckoutType": "PROVISIONAL",
  "EntitlementsAllowed": [
    {
      "Name": "ReadOnlyUsers", "Count": 10,
      "Units": "Count"
    }
},
  "Expiration": "2021-04-22Tl9:02: 36",
  "IssuedAt": "2021-04-22Tl8:02:36",
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
  "ProductSku": "2205b290-19e6-4c76-9eea-377d6bf7la47",
  "Fingerprint": "aws:294406891311:AWS/Marketplace:issuer-fingerprint", "CheckoutType": "PROVISIONAL",
  "EntitlementsAllowed": [
    {
      "Name": "IntermediateTier", "Units": "None"
    }
},
  "Expiration": "2021-04-22Tl9:02:36",
  "IssuedAt": "2021-04-22Tl8:02:36",  
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

## Integrating an AMI product with License Manager<a name="integrate-with-LM"></a>

**To integrate your AMI\-based product with License Manager**

1. Set IAM permissions to call License Manager\. For more information, see [License Manager integration prerequisites](#LM-prereqs)\.

1. Download the AWS SDK\.

   Don't configure AWS credentials within your software\. AWS credentials for the buyer are automatically obtained at runtime when your AMI is running within an Amazon EC2 instance, Amazon ECS task, or Amazon EKS pod\.

1. Add license checks to your product\.

   Your product can call the `CheckoutLicense` API operation wherever the license check should be performed\. For checking the license, your product has to know:

   1. The trusted issuer of the license \(AWS Marketplace\)

   1. The application's Product SKU \(Product ID\)

   1. The entitlement to check for this application

   The API calls vary based on what kind of pricing licenses you set up\.

1. Publish your product listing on AWS Marketplace\.

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