# Understanding AMI\-based products<a name="ami-getting-started"></a>

This section outlines key concepts in working with AMI\-based products\.

**Topics**
+ [Product lifecycle](#ami-product-lifecycle)
+ [AMI product codes](#ami-product-codes)
+ [Change requests](#ami-change-requests)
+ [Product Load Forms](#ami-product-load-forms)

## Product lifecycle<a name="ami-product-lifecycle"></a>

AMI\-based products include a set of one or more versions of the software, and metadata about the product as a whole\. When you create the product, you configure its properties in AWS Marketplace including your product’s name, description, and pricing\. You also determine the appropriate categories for your product and add keywords so your product appears in relevant searches\.

You also create the first version of the software\. Depending on how you are delivering your software, this might be a single AMI, a set of one or more AMIs with AWS CloudFormation templates, or software packages for your buyer to use in creating their own AMIs\. For more information, see [AMI\-based product delivery methods](ami-products.md#ami-product-delivery-methods)\.

For paid products, buyers are billed for the number of installed instances\. To meter on a different dimension that your software tracks \(for example, number of users of the product\), integrate your product with the AWS Marketplace Metering Service\. For more information, see [Custom metering for AMI products with AWS Marketplace Metering Service](custom-metering-with-mp-metering-service.md)\.

When you create your product and the first version of your software, it's initially published in a limited scope so that only your account can access it\. When you're ready, you can publish it to the AWS Marketplace catalog to allow buyers to subscribe and purchase your product\.

The lifecycle of an AMI\-based product for AWS Marketplace does not end after you publish the first version\. You should keep your product up to date with new versions of your software and with security patches for the base operating system\.

As an example of a complete AMI\-based product lifecycle, imagine a seller wants to sell their AMI\-based product on AWS Marketplace\. Following is how the seller creates and maintains the product over time:

1. **Create a product** – The seller creates the product, and publishes version 1\.0\.0 to AWS Marketplace\. Buyers can create instances of version 1\.0\.0 and use it\.

1. **Add a new version** – Later, the seller adds a new feature to the product, and adds a new version, 1\.1\.0, that includes the feature\. Buyers can still use the original version, 1\.0\.0, or they can choose the new version, 1\.1\.0\.
**Note**  
Unlike new products, new versions are published to full public availability\. You can only test them in AWS Marketplace without customers seeing them if the product as a whole is in limited release\.

1. **Update product information** – With version 1\.1\.0 available, the seller lets buyers know about the new feature by updating the product information with new highlight text describing the feature\.

1. **Add a minor version** – When the seller fixes a bug in version 1\.1\.0, they release it by adding a new version 1\.1\.1\. Buyers now have the choice of using version 1\.0\.0, 1\.1\.0, or 1\.1\.1\.

1. **Restrict a version** – The seller decides that the bug is serious enough that they don’t want buyers to be able to use version 1\.1\.0, so they restrict that version\. No new customers can then buy 1\.1\.0 \(they can only choose 1\.0\.0 or 1\.1\.1\), although existing buyers still have access to it\.

1. **Update version information** – To help those existing buyers, the seller updates the version information for 1\.1\.0 with a suggestion to upgrade to version 1\.1\.1\.

1. **Monitor usage** – As buyers purchase and use the product, the seller monitors sales, usage, and other metrics using the AWS Marketplace [Seller reports and data feeds](reports-and-data-feed.md)\.

1. **Remove the product** – When the product is no longer needed, the seller removes it from AWS Marketplace\.

In this example, the seller created three different versions of the AMI in the product, but only two were available to new buyers \(prior to removing the product\)\.

To make modifications to versions or the product information, you create [Change requests](#ami-change-requests) in the AWS Marketplace Management Portal\.

For detailed instructions on the steps to create and manage your AMI\-based product, see [Single\-AMI products](ami-single-ami-products.md)\.



## AMI product codes<a name="ami-product-codes"></a>

A unique product code is assigned to your product when you create it in AWS Marketplace\. That product code is associated with the AMIs for your product and is used to track usage of your product\. Product codes are propagated automatically as buyers work with the software\. For example, a customer subscribes and launches an AMI, configures it, and produces a new AMI\. The new AMI still contains the original product code, so correct usage tracking and permissions remains in place\.

**Note**  
The product *code* is different than the product *ID* for your product\. Each product in AWS Marketplace is assigned a unique product ID\. The product ID is used to identify your product in the AWS Marketplace catalog, in customer billing, and in seller reports\. The product code is attached to instances created from your AMI as instance metadata\. When an AMI with that product code is used to create an instance, the customer will get a bill that shows the associated product ID\. After you create your product, find the product code and the product ID in the AWS Marketplace Management Portal page for your product\.

As a seller, your software can get the product code for the running Amazon Elastic Compute Cloud \(Amazon EC2\) instance at runtime from the instance metadata\. You can use the product code for extra security, such as validating the product code at product start\. You can't make API calls to an AMI's product code until the product has been published into a limited state for testing\. For more information about verifying the product code, see [Verifying your software is running on your AWS Marketplace AMI](best-practices-for-building-your-amis.md#verifying-ami-runtime) \.

## Change requests<a name="ami-change-requests"></a>

To make changes to a product or version in AWS Marketplace, you submit a **change request** through the AWS Marketplace Management Portal\. Change requests are added to a queue and can take from minutes to days to resolve, depending on the type of request\. You can see the status of requests in the AWS Marketplace Management Portal\.

The types of changes you can request for AMI\-based products include:
+ Update product information displayed to buyers\.
+ Update version information displayed to buyers\.
+ Add a new version of your product\.
+ Restrict a version so that new buyers can no longer access that version\.
+ Update the AWS Regions that a product is available in\.
+ Update the pricing and instance types for a product\.
+ Remove a product from AWS Marketplace\.

For more information, see [Creating a change request](ami-single-ami-products.md#single-ami-creating-change-request)\.

**Note**  
Some change requests require you to use product load forms to create the request\. See the following section\.

## Product Load Forms<a name="ami-product-load-forms"></a>

Typically, when you create or edit your product, you work within the AWS Marketplace Management Portal user interface to make the changes that you want\. However, a few operations direct you to use a *Product Load Form* \(PLF\)\. 

A PLF is a spreadsheet that contains all the information about a product\. There are several ways that you can get the PLF:
+ You can download the PLF for an existing product from the product's details page in the AWS Marketplace Management Portal\. 
+ You are prompted to download the PLF when you select a menu item for an action that requires it\. For example, if you choose to create a new monthly billed server product, you will be prompted to download the appropriate PLF\. 

  If the action is an edit to an existing product, the PLF is pre\-populated with the information for that product, so you only need to change the details that you are updating\.
+ If you need a new, blank PLF, there are links to PLFs, based on the type of product you want to create, on the AWS Marketplace Management Portal [ File upload](https://aws.amazon.com/marketplace/management/product-load) page\. 

 After you have completed your PLF, upload it to the AWS Marketplace Management Portal [ File upload](https://aws.amazon.com/marketplace/management/product-load) page\. The PLF itself has more detailed instructions in the **Instructions** tab\. 