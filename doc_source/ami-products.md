# AMI\-Based Products<a name="ami-products"></a>

Each product in AWS Marketplace is assigned a unique product ID\. This ID is used to track and identify the product in our catalog and is included in seller reports\. A unique product code is assigned to all AMIs submitted to AWS Marketplace\. The unique product ID is used to distinguish your product in AWS Marketplace and provide access to users who purchase your product as well as for the customer billing process\. 

Sellers can obtain the product code while developing their software so it can be used for extra security, such as validating the product code at product start\. API calls to an AMI's product code isn't possible until the product has been published into a limited state for testing\. 

Product codes automatically propagate as customers work with the software\. For example, a customer subscribes and launches an AMI, configures it, and produces a new AMI\. The new AMI still contains the original product code, so correct billing and permissions remains in place\. For more information, see [Instance Metadata and User Data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide//ec2-instance-metadata.html) in the *Amazon EC2 User Guide for Linux Instances*\. 

## Multiple Versions<a name="multiple-versions"></a>

AWS Marketplace product listings allow for multiple versions of the product to be available to subscribers as part of their subscription as separate AMIs\. The seller can request any number of versions to be available on a product listing\. Once a subscriber has access to an AMI, they always have launch permissions on the AMI, regardless of the visibility or status of that version on the listing\. 

 For example, the product Data Cleaner might have versions 1\.0\.0, 1\.2\.5, and 2\.0\.1, all of which can be available to subscribers\. If you request the removal of version 1\.0\.0, no new customers can subscribe to that version, but exisiting customers can access it\. 

## Removing Products from AWS Marketplace<a name="removing-products-from-aws-marketplace"></a>

Once your product is published, you can sunset \(remove\) the product from AWS Marketplace\. To remove a product, identify the product and submit a request to remove it, along with a reason for removing and a contact email for you\. You can also provide a replacement product ID if you're replacing the current product with a new one\. Once you request to remove your product, new customers will no longer be able to subscribe\. You're required to support any existing customers for a minimum of 90 days\. Requests for a product to be removed from AWS Marketplace are processed with the following conditions: 
+  The product is removed from AWS Marketplace search, browse and other discovery tools\. Any Subscribe button or functionality is disabled, and messaging on the page clearly indicates the product is no longer available\. Note that the product detail page is still accessible using the URL and may be indexed in public search engines\. 
+  A reason for take down must be specified \(e\.g\., end of support, end of product updates, or replacement product\)\. For the requirements for continuing support for removed products, see [Terms and Conditions for AWS Marketplace Sellers](https://aws.amazon.com/marketplace/management/terms?)\. 
+  Current subscribers are messaged by AWS Marketplace informing of the product take down, reasons, and provide seller contact information\. 
+  Current subscribed customers *do* retain access to the software until they cancel their subscription\. They aren't impacted in any way\. 

**To remove a product created using the Self\-Service Listings tool**

1. Open the AWS Marketplace Management Portal at [https://aws.amazon.com/marketplace/management/tour/](https://aws.amazon.com/marketplace/management/tour/) and sign in to your seller account\.

1. Choose the **Listings** tab\.

1. On your products listing page under **Current Listings**, locate the product that you want to remove\. In the **Actions** column for the listing, on the **Select action** menu, choose **Remove listing**\.

1. On the **Remove Product Listing** page, for **Request Reason**, type the reason that you're requesting the product's removal\.

1. For **Contact Email**, type the email that AWS can use to contact you with any questions\.
**Note**  
You can also provide a replacement product ID, but that field isn't required\.

1. Review the information for accuracy and then choose **Submit Sunset Request**\. 

Once you have submitted the request, you will be taken to a **What’s next** informational page\. The AWS Marketplace Seller Operations team reviews and processes your request\. Check the status of your submission by viewing **Open Requests** on your **Self\-Service Listing** page\.

After your product is removed, the product appears in your **Request History** list and in the **Current Listings** list\. In **Current Listings**, the only action that you can perform is downloading the spreadsheet for the listing\. You can't edit or submit another sunset request\. 

For listings not created with the Self\-Service Listings tool, edit and upload the Product Load Form for the product\. Links to upload updated Product Load Forms are on the **File Uploads** tab on the AMMP landing page\.

 If you have questions about product removals, contact the AWS Marketplace Seller Operations team at aws\-marketplace\-seller\-ops@amazon\.com\.