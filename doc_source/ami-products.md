# AMI\-based products<a name="ami-products"></a>

[Amazon Machine Images \(AMIs\)](https://docs.aws.amazon.com/general/latest/gr/glos-chap.html#AmazonMachineImage) provide the information required to launch an Amazon EC2 instance\.

Each product in AWS Marketplace is assigned a unique product ID\. This product ID is used to identify your product in the AWS Marketplace catalog, in customer billing, and in seller reports\. A unique product code is assigned to all AMIs submitted to AWS Marketplace\. Product codes are not product IDs\. Sellers can obtain the product code while they develop their software so it can be used for extra security, such as validating the product code at product start\. you cannot make API calls to an AMI's product code until the product has been published into a limited state for testing\. 

Product codes are propagated automatically as customers work with the software\. For example, a customer subscribes and launches an AMI, configures it, and produces a new AMI\. The new AMI still contains the original product code, so correct billing and permissions remains in place\. For more information, see [Instance Metadata and User Data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html) in the *Amazon EC2 User Guide for Linux Instances*\. 

## Multiple versions<a name="multiple-versions"></a>

You can provide multiple versions of a product as separate AMIs to buyers as part of their purchase\. The seller can make available any number of versions for a product\. After a buyer has access to an AMI, they always have launch permissions on the AMI, regardless of the visibility or status of that version\.

 For example, the product Data Cleaner might have versions 1\.0\.0, 1\.2\.5, and 2\.0\.1, all of which can be available to buyers\. If you request the removal of version 1\.0\.0, no new customers can buy that version, but existing customers can access it\. 

## AMI file upload<a name="amis-file-upload"></a>

Self\-service AMI scanning is available in the AWS Marketplace Management Portal\. With this feature, you can initiate scans of your AMIs and receive scanning results quickly—typically in less than an hour—with clear feedback in a single location\. For more information, see [AMI Self\-Service Scanning](https://aws.amazon.com/marketplace/management/manage-products/#/build.build-new)\. 

To upload a new product load form, go to [File Upload](https://aws.amazon.com/marketplace/management/product-load) in the AWS Marketplace Management Portal\. From there, you can download the most recent product load template\. We strongly recommend checking that the form is the most recent because it's consistently updated with more instance types and regions as they become available\. Using AMI Self\-Service Scanning significantly increases the ease of loading the page\. 

## Removing products from AWS Marketplace<a name="removing-products-from-aws-marketplace"></a>

After your product is published, you can remove \(also referred to as *sunset*\) the product from AWS Marketplace\. To remove a product, identify the product and submit a request to remove it, along with a reason for removal and a contact email address for you\. You can also provide a replacement product ID if you're replacing the current product with a new one\. After you request product removal, new customers will no longer be able to subscribe\. You're required to support any existing customers for a minimum of 90 days\. We process requests for product removal from AWS Marketplace with the following conditions: 
+ The product is removed from AWS Marketplace search, browse, and other discovery tools\. Any Subscribe button or functionality is disabled, and messaging on the page clearly indicates the product is no longer available\. Note that the product detail page is still accessible using the URL and may be indexed in public search engines\. 
+ A reason for removal must be specified \(for example, end of support, end of product updates, or replacement product\)\. For the requirements for continuing support for removed products, see [Terms and Conditions for AWS Marketplace Sellers](https://aws.amazon.com/marketplace/management/terms?)\. 
+ Current buyers are messaged by AWS Marketplace informing of the product removal, reasons for the removal, and provide seller contact information\. 
+  Current buyers *do* retain access to the software until they cancel their subscription\. They aren't impacted in any way by the product removal\. 

**To remove a product created using the AWS Marketplace Management Portal**

1. Open the AWS Marketplace Management Portal at [https://aws.amazon.com/marketplace/management/tour/](https://aws.amazon.com/marketplace/management/tour/), and then sign in to your seller account\.

1. Choose the **Products** tab, and then choose **Server**\.

1. On your product page under **Current server products**, locate the product that you want to remove\. From the **Actions** column on the **Select action** menu, choose **Remove product**\.

1. On the **Remove Product** page, for **Request Reason**, type the reason that you're requesting the product's removal\.

1. For **Contact Email**, type the email that AWS can use to contact you with any questions\.
**Note**  
You can also provide a replacement product ID, but that field isn't required\.

1. Review the information for accuracy, and then choose **Submit Sunset Request**\. 

A **What’s next** informational page displays after you submit the product removal request\. The AWS Marketplace Seller Operations team reviews and processes your request\. Check the status of your submission by viewing **Requests**\.

After your product is removed, the product appears in your **Request History** list and in the **Current Products** list\. In **Current Products**, the only action that you can perform is downloading the spreadsheet for the product\. You can't edit or submit another sunset request\. 

For products not created using the **Products** tab, edit and upload the product load form for the product\. Links to upload updated product load forms are on the **Assets** tab on the AWS Marketplace Management Portal landing page\.

 If you have questions about product removals, contact the [AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/) team\.