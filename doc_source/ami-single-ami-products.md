# Single\-AMI products<a name="ami-single-ami-products"></a>

This section discusses how you can work with products in AWS Marketplace that are made up of a single Amazon Machine Instance \(AMI\)\. Customers can use AMIs to create Amazon EC2 instances with your product already installed and configured\.

**Topics**
+ [Prerequisites](#single-ami-prerequisites)
+ [Creating your product](#single-ami-creating-product)
+ [Creating a change request](#single-ami-creating-change-request)
+ [Getting status of a request](#single-ami-getting-change-request-status)
+ [Updating product information](#single-ami-updating-product)
+ [Updating version information](#single-ami-updating-version)
+ [Adding a new version](#single-ami-adding-version)
+ [Giving AWS Marketplace access to your AMI](#single-ami-marketplace-ami-access)
+ [Restricting a version](#single-ami-restricting-version)
+ [Removing a product from AWS Marketplace](#removing-products-from-aws-marketplace)
+ [Common errors when submitting change requests](#request-errors-and-issues)

## Prerequisites<a name="single-ami-prerequisites"></a>

Before you get started, you must complete the following prerequisites:

1. Have access to the AWS Marketplace Management Portal\. This is the tool that you use to register as a seller and manage the product that you sell on AWS Marketplace\. To learn more about getting access to the AWS Marketplace Management Portal, see [Policies and permissions for AWS Marketplace sellers](detailed-management-portal-permissions.md)\.

1. Register as a seller and, if you want to charge for your products, submit your tax and banking information\. To learn more about becoming a seller, see [Getting started as a seller](user-guide-for-sellers.md)\.

1. Have a product that you want to sell\. For AMI\-based products, this typically means you have created or modified server software, and you have created an AMI for your customers to use\. To learn more about preparing an AMI for use in AWS Marketplace, see [Best practices for building AMIs](best-practices-for-building-your-amis.md)\. 

## Creating your product<a name="single-ami-creating-product"></a>

Create AMI\-based products by using the AWS Marketplace Management Portal\.

**To create a single\-AMI product**

1. Open the AWS Marketplace Management Portal at [https://aws.amazon.com/marketplace/management/tour/](https://aws.amazon.com/marketplace/management/tour/), and then sign in to your seller account\.

1. From the **Products** menu, choose **Server**\. Or, you can go directly to the [Server Products](https://aws.amazon.com/marketplace/management/products/server) page\.

1. From the **Current Server Products** tab, select **Create server product** and then select one of the licensing types for single AMI products:
   + **Bring your own license \(BYOL\)** – A product that the user gets a license from you outside of AWS Marketplace\. It can be either a paid or free license\.
   + **Free** – A product that is free for your subscribers to use\. \(They will still pay charges for any associated Amazon Elastic Compute Cloud \(Amazon EC2\) instance or other AWS resources\.\)
   + **Paid hourly or hourly\-annual** – A product that the buyer pays for either on an hourly basis or hourly with an annual contract\. AWS does the metering based on the product code on the AMI\.
   + **Paid monthly** – A product that the buyer is billed for monthly by AWS\.
**Note**  
There is one other type of licensing for AMI\-based products: Usage\-based\. This licensing type applies when your product integrates with the AWS Marketplace Metering Service to provide custom metering based on your customers' usage\. To create a product that has usage\-based pricing, you must to download, complete, and upload a Product Load Form \(PLF\)\.  
For more information about PLFs, see [Product Load Forms](ami-getting-started.md#ami-product-load-forms)\.  
For more information about the different types of licensing, see [AMI pricing models](pricing-ami-products.md#pricing-models-for-ami-products)\.

1. Based on your selection, fill out the information for the new product, and choose **Submit**\.
**Note**  
If you select **Paid monthly**, you will be asked to download a Product Load Form \(PLF\)\.

1. Verify that the request appears on the **Requests** tab with the **Under Review** status\. You can return to this page to see the status of your request as it is processed\.
**Note**  
Product verification and publication is a manual process, handled by the AWS Marketplace Seller Operations team\. It can take 3–5 days to publish your initial product version, if there are no errors\. For more details about timing, see [Timing and expectations](product-submission.md#timing-and-expectations)\.

When your product is initially published, it's only accessible to your AWS account \(the one you used to create the product\)\. If you view the product from the **Server products** page, you can select **View on AWS Marketplace** to view the product details as it will appear in AWS Marketplace for buyers\. This detail listing isn't visible to other AWS Marketplace users\. 

This capability allows you to test your product \(and even publish multiple versions for testing\) before releasing it publicly\. If you need to make the product available to additional test accounts, or to publish your product publicly, contact the [AWS Marketplace Seller Operations team](https://aws.amazon.com/marketplace/management/contact-us/)\.

For more information about preparing your product information and submitting it for publication, see the following resources:
+ [Preparing your product](product-preparation.md)
+ [Submitting your product for publication](product-submission.md)

For more information about preparing your AMI for submission to AWS Marketplace, see the following resources:
+ [Best practices for building AMIs](best-practices-for-building-your-amis.md)
+ [AMI product checklist](aws-marketplace-listing-checklist.md)
+ [AMI\-based product requirements](product-and-ami-policies.md)

## Creating a change request<a name="single-ami-creating-change-request"></a>

To make modifications to versions or the product information, you create a *change request* in the AWS Marketplace Management Portal\.

**Note**  
You can also create change requests using the [AWS Marketplace Catalog API](https://docs.aws.amazon.com/marketplace-catalog/latest/api-reference/seller-products.html)\.

**To create a change request**

1. Open the AWS Marketplace Management Portal at [https://aws.amazon.com/marketplace/management/tour/](https://aws.amazon.com/marketplace/management/tour/), and sign in to your seller account, then go to the [ Server products](https://aws.amazon.com/marketplace/management/products/server) page\.

1. On the **Current server products** tab, select the product you want to modify\.

1. Choose an option from the **Request changes** dropdown\.

For most change requests, you simply fill out the UI form and submit\. However, for certain changes, you must download, complete, and then upload a Product Load Form \(PLF\)\. This is a spreadsheet that contains a form for you to fill out with the required information\. When you choose one of these change requests, you will be prompted to download the correct PLF for the request you are attempting to create\. The PLF is pre\-populated with information from your existing product details\. You can upload your completed PLF to the AWS Marketplace Management Portal [ File upload](https://aws.amazon.com/marketplace/management/product-load) page\.

**Note**  
We strongly recommend that you download and use the most recent PLF\. The form is regularly updated with new information, including instance types and Regions as they become available\. You can find the latest PLF for a product from the **Server products** page, by selecting the product and then choosing **Download Product Load Form**\.

For more information about the status of a change request, see [Getting status of a request](#single-ami-getting-change-request-status)\. For insight into potential issues with change requests, see [Common errors when submitting change requests](#request-errors-and-issues)\.

For more details about specific change requests, see the following resources:
+ [Updating product information](#single-ami-updating-product)
+ [Updating version information](#single-ami-updating-version)
+ [Adding a new version](#single-ami-adding-version)
+ [Restricting a version](#single-ami-restricting-version)

## Getting status of a request<a name="single-ami-getting-change-request-status"></a>

After you submit a change request, you can see the status of your request from the **Requests** tab of the [Server products](https://aws.amazon.com/marketplace/management/products/server) page of the AWS Marketplace Management Portal\. The status could be any of the following:
+ **Under review** means that your request is being reviewed\. Some requests require manual review by the AWS Marketplace team but most are reviewed automatically in the system\.
+ **Succeeded** means that your request is complete\. Your product or version has been updated as you requested\.
+ **Action required** means that you need to update your request to fix an issue or answer a question about the request\. Select the request to see the details, including any issues\.
+ **Failed** means that something went wrong with the request, and you should create a new request for the change, with the same data\.

## Updating product information<a name="single-ami-updating-product"></a>

After you have created your product, you may want to change some of the information associated with it in AWS Marketplace\. For example, if a new version modifies the description or highlights of the product, you can edit the product information with the new data\.

**To update product information**

1. Open the AWS Marketplace Management Portal at [https://aws.amazon.com/marketplace/management/tour/](https://aws.amazon.com/marketplace/management/tour/), and then sign in to your seller account\.

1. Go to the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page, and on the **Current server products** tab, select the product you want to modify\.

1. From the **Request changes** dropdown, choose **Update product information**\.

1. Update any of the following fields that you need to change:
   + **Product title**
   + **SKU**
   + **Short description**
   + **Long description**
   + **Product logo image URL**
   + **Highlights**
   + **Product categories**
   + **Keywords**
   + **Product video URL**
   + **Resources**
   + **Support information**
**Note**  
For details about the logo format, see [Company and product logo requirements](product-submission.md#seller-and-product-logos)\.

1. Select **Submit**\.

1. Verify that the request appears on the **Requests** tab with the **Under review** status\. You may need to refresh the page to see the request on the list\.

You can check the status of your request at any time from the **Requests** tab of the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page\. For more information, see [Getting status of a request](#single-ami-getting-change-request-status)\.

## Updating version information<a name="single-ami-updating-version"></a>

After a version is created, it can be helpful to provide updated information to your buyers by modifying the information associated with the version\. For example, if you plan to restrict version 1\.0 after version 1\.1 is released, you can update the description of version 1\.0 to direct buyers to version 1\.1, with the date that the version will be restricted\. You update the version information from the AWS Marketplace Management Portal\.

**To update version information**

1. Open the AWS Marketplace Management Portal at [https://aws.amazon.com/marketplace/management/tour/](https://aws.amazon.com/marketplace/management/tour/), and then sign in to your seller account\.

1. Go to the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page, and on the **Current server products** tab, select the product you want to modify\.

1. From the **Request changes** dropdown, choose **Update version information**\.

1. On the **Update version** page, select the version that you want to update\.

1. Update any of the following information that you need to modify:
   + **Release notes**
   + **Usage instructions**
   + **64\-bit \(x86\) Amazon Machine Image \(AMI\)** – Details on usage and security group

1. Select **Submit**\.

1. Verify that the request appears on the **Requests** tab with the **Under review** status\.

**Note**  
You can't use this procedure to update the version title, or the AMI associated with the version\. In this case, [create a new version](#single-ami-adding-version) and [restrict the previous one](#single-ami-restricting-version)\.

You can check the status of your request at any time from the **Requests** tab of the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page\. For more information, see [Getting status of a request](#single-ami-getting-change-request-status)\.

## Adding a new version<a name="single-ami-adding-version"></a>

You can add a new version of your product when you make changes to the product, the base image, or any other time you need to modify the AMI for the product\. Add a new version of your product from the AWS Marketplace Management Portal\. 

**Note**  
For information about creating an AMI for AWS Marketplace, see [Best practices for building AMIs](best-practices-for-building-your-amis.md)\.

**To add a new version**

1. Open the AWS Marketplace Management Portal at [https://aws.amazon.com/marketplace/management/tour/](https://aws.amazon.com/marketplace/management/tour/), and then sign in to your seller account\.

1. Go to the [ Server products](https://aws.amazon.com/marketplace/management/products/server) page, and on the **Current server products** tab, select the product you want to modify\. 

1. From the **Request changes** dropdown, choose **Add new version**\. The **Add a new version** form appears, pre\-populated with the information from your most recent version\.

1. In the **Version information** section, provide the following information:
   + **Version title** – Enter a valid string \(for example *1\.1* or *Version 2\.0*\)\. It must be unique across the product\.
   + **Release notes** – Enter text to describe details about this version\.

1. In the **New Amazon Machine Image \(AMI\)** section, provide the following information:
   + **Amazon Machine Image ID** – Enter the AMI ID for the AMI that you want to use for this version\. You can find the AMI ID from the [ list of AMIs in the console](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#Images:sort=name)\. The AMI must exist in the US East \(N\. Virginia\) Region, and in your AWS Marketplace Seller account\.
   + **IAM access role ARN** – Enter the Amazon Resource Name \(ARN\) for an AWS Identity and Access Management \(IAM\) role that allows AWS Marketplace to gain access to your AMI\. For instructions on how to create the IAM role, see [Giving AWS Marketplace access to your AMI](#single-ami-marketplace-ami-access)\. Use the standard format for an IAM ARN, for example: *arn:aws:iam::123456789012:role/RoleName*\. The ARN must exist in your AWS Marketplace Seller account\.
   + **OS user name** – For Linux\-based AMIs, enter the name of a user that can be used to sign into the instance\. We recommend using *ec2\-user*\.
   + **Scanning port** – Enter the port number that can be used to log into the operating system: the SSH port for a Linux AMI or the RDP port for a Windows AMI\.

1. If it is not already, expand the **Configuration settings to publish the AMI to the AWS Marketplace customer website** section, then provide the following information:
   + **Usage instructions** – Enter instructions for using the AMI or a link to more information about using the AMI\. For example: *To get started with the product, navigate to https://example\.com/usage\.htm\.*
   + **Endpoint URL** – Provide information about how the buyer can access the software after they create an instance\. Enter the **Protocol** \(*https* or *http*\), the **Relative URL** \(for example, */index\.html*\), and the **Port** \(for example, *443*\) that buyers can use to access your product\. \(The host name depends on the EC2 instance, so you only need to provide the relative path\)\.
   + **Operating system \(OS\)** – Enter the name of the OS used by the AMI \(for example, *Amazon Linux*\)\.
   + **OS version** – Enter the specific version of the OS in the AMI\.
   + **Recommended instance type**– Choose the instance type that buyers get by default\.
   + **Security group recommendations** – Enter the information for one or more recommendations, including the protocol \(*TCP* or *UDP*\), range of ports to allow, and list of IPv4 CIDR IPs \(in the form *xxx\.xxx\.xxx\.xxx/nn*, for example, *192\.0\.2\.0/24*\)\.

1. Select **Submit** to submit the request to add your new version\.

1. Verify that the request appears on the **Requests** tab with the **Under review** status\. If there are errors to fix, the page displays the errors in a table at the top of the page, and the specific fields that need to be updated display in red\.

You can check the status of your request at any time from the **Requests** tab of the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page\. The new version will be reviewed and, if successful, published as a new public version of your product\. If there is an issue, the status may show **Action required**\. Select the request to see details, including any issues\.

If your request is successful, your existing users will receive the following email message\. The message notifies them that the new version is available, links to the version's release notes, and suggests they upgrade to the latest version\. As the AWS account root user, you'll also receive a copy of the email message in the email account that's associated with your AWS account\.

```
Greetings from AWS Marketplace,

Thank you for subscribing to <product-title>

We are writing to inform you that <seller-name> has added a new version to <product-title> on AWS Marketplace. As an existing customer, your subscription to the product, any running instances and access to previous versions are unaffected. However, <seller-name> does recommend you to update to the latest version, <product-title>/<version-title> by visiting <product-detail-page-of-new-listing>.

For additional questions or upgrade information, please contact <seller-name> directly. Click here <link of seller page on MP> to visit the seller’s profile page on AWS Marketplace.

Release notes for <product-title>/<version-title>:

<release-notes>

Thank you,
The AWS Marketplace Team
https://aws.amazon.com/marketplace

Amazon Web Services, Inc. is a subsidiary of Amazon.com, Inc. Amazon.com is a registered trademark of Amazon.com, Inc. This message was produced and distributed by Amazon Web Services Inc., 410 Terry Ave. North, Seattle, WA 98109-5210
```

## Giving AWS Marketplace access to your AMI<a name="single-ami-marketplace-ami-access"></a>

When you create a request that includes adding a new AMI to AWS Marketplace, the AMI must be copied into the AWS Marketplace system and then scanned for security issues\. You must give AWS Marketplace access to the AMI by creating an AWS Identity and Access Management \(IAM\) role with permissions to perform actions on your AMI and a trust policy that allows AWS Marketplace to assume the role\. You only need to create the IAM role once\.

**To create a role for AWS Marketplace AMI assets ingestion**

1. Sign in to the AWS Management Console, open the IAM console and go to the [ Roles page](https://console.aws.amazon.com/iam/home?region=us-east-1#/roles)\.

1. Select **Create role**\.

1. On the **Create role** page, make the following selections:
   + **Select type of trusted entity** – Choose **AWS Service**\.
   + **Choose a use case** – Choose **AWS Marketplace**\.
   + **Select your use case** – Choose **Marketplace – AMI Assets Ingestion**\. 
   + To move to the next page, select **Next: Permissions**\.

1. Select the **AWSMarketplaceAmiIngestion** policy\. Add a permissions boundary if required, and then select **Next: Tags** to continue\.
**Note**  
You can use permissions boundaries to limit the access that you give AWS Marketplace with this role\. For more information, see [Permissions boundaries for IAM entities](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html) in the *AWS Identity and Access Management User Guide*\.

1. To continue, select **Next: Review**\.

1. Provide a name for the role, and select **Create role**\.

1. You should see "The role *rolename* has been created" at the top of the page, and the role should appear in the list of roles\.

On this page, when you select the role that you just created, you can see its ARN in the form *arn:aws:iam::123456789012:role/exampleRole*\. Use the ARN for the **IAM access role ARN** when you create change requests, for example, when [adding a new version](#single-ami-adding-version) to your product\.

## Restricting a version<a name="single-ami-restricting-version"></a>

If you want to prevent buyers from accessing a specific version of your public product, you can restrict that version\.

**Note**  
All subscribers can use the current version regardless of the restriction status\. AWS Marketplace guidelines require that you continue to offer support to existing buyers for 90 days after restricting the version\. Your AMI will be marked as deprecated after the version is restricted\. For more information, see [Deprecate an AMI](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ami-deprecate.html) in the *Amazon Elastic Compute Cloud User Guide for Windows Instances*\.

**To restrict a version**

1. Open the AWS Marketplace Management Portal at [https://aws.amazon.com/marketplace/management/tour/](https://aws.amazon.com/marketplace/management/tour/), and then sign in to your seller account\.

1. Go to the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page, and on the **Current server products** tab, select the product you want to modify\.

1. From the **Request changes** dropdown, choose **Restrict version**\.

1. On the **Restrict version** page, select the version \(or versions\) that you want to restrict\.

1. Select **Submit** to submit your request for review\.

1. Verify that the **Requests** tab show the **Request status** as **Under review**\. When the request completes, the status is **Succeeded**\.

**Note**  
You can't restrict all versions of a product\. If you try to restrict the last remaining public version of a product, you will receive an error\. To completely remove a product, see [Removing a product from AWS Marketplace](#removing-products-from-aws-marketplace)\.

You can check the status of your request at any time from the **Requests** tab of the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page\. For more information, see [Getting status of a request](#single-ami-getting-change-request-status)\.

**Note**  
Restricting a version can take up to 3 days to complete\.

If your request is successful, your existing users will receive the following email message that notifies them of the version restriction and suggests they use the most recent version available\. As the AWS account root user, you'll also receive a copy of the email message in the email account that's associated with your AWS account\.

```
Greetings from AWS Marketplace,

Thank you for subscribing to <product-title>.

We are writing to inform you that, as of <Version-Restriction-Date>, <Seller Name> will no longer offer version(s) "<version-title>" to new subscribers. Your use and subscription is unaffected for this version(s), however it is recommended that users upgrade to the latest version on AWS Marketplace.

For additional questions or upgrade information, please contact <seller-name> directly. Click here<link of seller page on MP> to visit the seller’s profile page on AWS Marketplace.

Thank you,
The AWS Marketplace Team
https://aws.amazon.com/marketplace

Amazon Web Services, Inc. is a subsidiary of Amazon.com, Inc. Amazon.com is a registered trademark of Amazon.com, Inc. This message was produced and distributed by Amazon Web Services Inc., 410 Terry Ave. North, Seattle, WA 98109-5210
```

## Removing a product from AWS Marketplace<a name="removing-products-from-aws-marketplace"></a>

After your product is published, you can remove \(also referred to as *sunset*\) it from AWS Marketplace\. To remove a product, identify the product and submit a request to remove it, along with a reason for removal and a contact email address for you\. You can also provide a replacement product ID if you're replacing the current product with a new one\. After you request product removal, new customers will no longer be able to subscribe to the product\. You're required to support any existing customers for a minimum of 90 days\. We process requests for product removal from AWS Marketplace with the following conditions: 
+ The product is removed from AWS Marketplace search, browse, and other discovery tools\. Any Subscribe button or functionality is disabled, and messaging on the page clearly indicates the product is no longer available\. Note that the product detail page is still accessible using the URL and may be indexed in public search engines\. 
+ A reason for removal must be specified \(for example, end of support, end of product updates, or replacement product\)\. For the requirements for continuing support for removed products, see [ Terms and Conditions for AWS Marketplace Sellers](https://aws.amazon.com/marketplace/management/terms)\. 
+ AWS Marketplace contacts current buyers via email message informing them of the product removal, reasons for the removal, and to provide seller contact information\. 
+ Current buyers *do* retain access to the software until they cancel their subscription\. They aren't affected in any way by the product's removal\. 

**To remove a product created using the AWS Marketplace Management Portal**

1. Open the AWS Marketplace Management Portal at [https://aws.amazon.com/marketplace/management/tour/](https://aws.amazon.com/marketplace/management/tour/), and then sign in to your seller account\.

1. Choose the **Products** tab, and then choose **Server**\. 

1. On your product page, under **Current server products**, locate the product that you want to remove\. From the **Actions** column on the **Select action** menu, choose **Unpublish product**\.

1. On the **Unpublish Product** page, for **Request Reason**, enter the reason that you're requesting the product's removal\. 

1. \(Optional\) Provide a **Replacement Product ID**, if there is another product that will take the place of the product you are removing\.

1. For **Contact Information**, enter the email address that AWS can use to contact you with any questions\. 

1. Review the information for accuracy, and then choose **Submit Sunset Request**\. 

A **What’s next** informational page displays after you submit the product removal request\. The AWS Marketplace Seller Operations team reviews and processes your request\. Check the status of your submission by viewing **Requests**\. 

After your product is removed, the product appears in the **Current Products** list in the AWS Marketplace Management Portal\. In **Current Products**, the only action that you can perform is downloading the spreadsheet for the product\. You can't edit or submit another sunset request\. 

If you have questions about product removals, contact the [AWS Marketplace Seller Operations team](https://aws.amazon.com/marketplace/management/contact-us/)\.

## Common errors when submitting change requests<a name="request-errors-and-issues"></a>

When you make changes to your product's information, you sometimes run into errors\. Following are some common issues and suggestions for how to fix them:
+ **Scanning your AMI** – Several issues could happen when scanning your AMI:
  + You have not granted AWS Marketplace permissions to scan your AMI\. Grant AWS Marketplace permissions to access it\. Or you have granted permissions, but the permissions boundary is too restrictive\. For more information, see [Giving AWS Marketplace access to your AMI](#single-ami-marketplace-ami-access)\.
  + If scanning finds security issues or Common Vulnerabilities and Exposures \(CVEs\) in your AMI, make sure you're using the latest patches for the operating system in your image\. For more information, see [AMI\-based product requirements](product-and-ami-policies.md)\.

  For general guidelines about building an AMI, see [Best practices for building AMIs](best-practices-for-building-your-amis.md)\.
+ **AWS Marketplace Management Portal fields** – Some fields in the AWS Marketplace Management Portal require very specific information:
  + If you are unsure about what the field is requesting, try checking the details in the console\. Most fields have text descriptions above the field, and formatting requirements below the field\.
  + If you try to submit a form with one or more invalid fields, a list of issues is shown\. A recommended action is provided to help you fix the issue\.
  +  If you're asked to provide an ARN, you will typically find it elsewhere in the console\. For example, the ARN for the IAM role that you created to give AWS Marketplace access to your AMI is found on the [ Roles page](https://console.aws.amazon.com/iam/home?region=us-east-1#/roles) in the IAM console\. ARNs all have a similar format\. For example, an IAM role ARN is in the form *arn:aws:iam::123456789012:role/exampleRole*\. 
  + Your logos and videos must be provided as a URL directly to the content\. For more information about logo formats, see [Company and product logo requirements](product-submission.md#seller-and-product-logos)\.

  For more information about submitting products and version change requests, see [Submitting your product for publication](product-submission.md)\.
+ **Product Load Form \(PLF\) issues** – PLFs contain instructions that are included in the spreadsheet\. Overall instructions are provided in the Instructions table\. Each field has instructions for how to fill it out—select the field to reveal the instructions\.
+ **Request in Progress** – Some requests cannot happen in parallel\. You can only have one request to update specific information in progress for a product at a time\. You can see all of your requests still under review on the **Requests** tab of the **Server products** page in AWS Marketplace Management Portal\. If you have a pending request that you did not intend, you can cancel it and then submit a new request with the change that you want to make\.
  + You can't update version information when an update \(to add or restrict\) a version is ongoing\.
  + If there is a request pending from the AWS Marketplace Seller Operations team, you can't submit any new changes\.
+ **Unexplained error** – If your submission fails with no explanation, try again\. Occasionally, server load causes a submission to fail\.

If you're still having problems with a change request, contact the [AWS Marketplace Seller Operations team](https://aws.amazon.com/marketplace/management/contact-us/)\.