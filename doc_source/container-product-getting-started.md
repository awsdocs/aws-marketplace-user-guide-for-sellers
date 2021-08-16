# Getting started with container products<a name="container-product-getting-started"></a>

This topic describes all the steps related to creating, testing, and publishing your first container product for AWS Marketplace\. For this exercise, we assume that you already have created at least one container in Amazon Elastic Container Service \(Amazon ECS\), Amazon Elastic Kubernetes Service \(Amazon EKS\), or AWS Fargate, and that you have links for the associated images\. We recommend that you plan your pricing, entitlement, and metering strategy well in advance of publicly publishing your product\.

**Note**  
For information about the requirements for container\-based products, see [Container\-based product requirements](container-product-policies.md)\.  
For information about setting the pricing for your product, see [Pricing container products](pricing-container-products.md)\.  
For information about custom metering for your Paid container\-based product, see [AWS Marketplace Metering Service integration](entitlement-and-metering-for-paid-products.md)\.

**Topics**
+ [Creating a container product](#create-container-product)
+ [Creating the product ID for your container product](#create-initial-container-product)
+ [Creating or updating pricing for container products](#container-product-load-form)
+ [Integrating metering for your container product](#getting-started-integrate-metering)
+ [Adding a new version of your product](#container-add-version)
+ [Updating version information](#container-product-updating-version)
+ [Creating or updating product information for your container product](#update-container-product-info)
+ [Publishing container products](#container-product-publishing)
+ [Container product scans for security issues](#container-security)

## Creating a container product<a name="create-container-product"></a>

Creating a container product involves the following steps:

1. Create the product ID\.

1. Create the pricing details\.

1. For paid products, integrate metering into your product\.

1. Add a new version of your product, including:

   1. Add repositories for your containers\.

   1. Upload the final containers into the repositories\.

   1. Create the first version of the product with your first container images\.

1. Update the product information\.

1. Publish the product for buyers\.

The first two steps must happen before you can edit any other details in AWS Marketplace\. However, you can perform the other steps in the order that makes the most sense to you or in parallel\.

The following topics describe each of these steps\.

## Creating the product ID for your container product<a name="create-initial-container-product"></a>

To get started with a container product, you must create a product ID record in AWS Marketplace\. The product ID is used to track your product throughout its lifecycle\.

Use the following procedure to create a new container product in the AWS Marketplace Management Portal, and generate the product ID\.

**To create the container product ID**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the menu bar, expand **Assets**, and choose **Container**\.

1. Provide a customer\-facing name for your product, and choose **Create**\. You can change this name later, if needed\.

1. Make a note of the **Product ID** for your later use when you create or update the product pricing details\.
**Tip**  
If you lose your product ID, you can find it in the AWS Marketplace Management Portal by choosing **Containers** from the **Assets** menu\. The **Containers** page shows a list of your products with their associated product IDs\.

You now have your initial container product and product ID\. Next, add pricing details for your product\.

## Creating or updating pricing for container products<a name="container-product-load-form"></a>

To update the pricing details for your container product, you must use a product load form \(PLF\)\. The PLF for your product is a spreadsheet that contains information about your product\. The following procedure outlines using the PLF to update information about your product, including pricing details\.

**Note**  
For more information about pricing models for container products, see [Pricing container products](pricing-container-products.md)\.  
Your pricing and metering must be aligned\. For more information on metering with container products, see [AWS Marketplace Metering Service integration](entitlement-and-metering-for-paid-products.md)\.

**To update pricing for your container product by using the product load form**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the menu bar, expand **Assets**, and choose **File Upload**\.

1. From **Product load forms for download** on the right side, choose **Containers Product Load Form**\.

1. Open the PLF spreadsheet on your computer, and fill out the fields to define your product\. This information includes your product ID which you made note of when you created your container product\.
**Tip**  
When viewing the product load form in Microsoft Excel, hover over each of the fields to show comments that provide guidance about how to fill in each field\. 

   Provide pricing and metering dimensions, based on your pricing model for your product\. For more information, see the following:
   + [Product load form for custom metering](container-metering-meterusage.md#custom-metering-product-load-form)
   + [Product load form for hourly metering](container-metering-registerusage.md#hourly-metering-product-load-form)
**Note**  
Required fields have a red header with the word **REQUIRED** in the spreadsheet\. Make sure that all of these fields are filled out to avoid delays in processing your request\.

1. Save your product load form\.

1. If it's not still open, open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the menu bar, expand **Assets**, and choose **File Upload**\.

1. In **Upload File**, browse your computer and choose the PLF file you saved for this container product\.

1. Provide a brief description for this PLF to help you identify it among the other PLFs you upload\.

1. Choose **Upload**\. Your uploaded PLF appears in a table at the bottom of the page\.

Your pricing details are reviewed and updated manually by the AWS Marketplace Seller Operations team\. It typically takes a few business days to complete the update\. You can check the status by choosing **Containers** from the **Assets** menu in the AWS Marketplace Management Portal\. An email message is sent to you when the review of your product pricing details is complete\.

**Note**  
Your container product is now created, in a limited state\. Your account can view the product for testing, and make modifications to it\. To make it visible to other test accounts, or, when it's ready, to make it publicly available, see [Publishing container products](#container-product-publishing)\.

You can edit your container product pricing by following this same procedure, until the product is published publicly\.

After you have created the pricing details for your product, you can add other product details, integrate metering into your product, and create a software version for your product\.

## Integrating metering for your container product<a name="getting-started-integrate-metering"></a>

You use the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) for both checking entitlement to use your product and metering usage for billing\. You must meter for the pricing model that you created when setting your pricing information\. For more information, see [AWS Marketplace Metering Service integration](entitlement-and-metering-for-paid-products.md)\.

## Adding a new version of your product<a name="container-add-version"></a>

Your product may have several versions over its lifetime\. Each version has a set of container images that are specific to that version\.

**Note**  
You cannot add a version to your product until you have created the product ID and the pricing for your product\. For more information about these steps, see [Creating the product ID for your container product](#create-initial-container-product), and [Creating or updating pricing for container products](#container-product-load-form)\.

Creating a version of your product involves the following steps:

1. Add any needed repositories in AWS Marketplace\.

1. Upload container images and other artifacts to the repositories\.

1. Add a new version to your product\.

Your container images and other artifacts for your product are stored in repositories in AWS Marketplace\. Typically, you create one repository for each artifact needed, but the repository can store multiple versions of the artifact \(with different tags\)\. 

**Note**  
All images in your product deployment must use images from the AWS Marketplace repositories\.

The following procedure describes how to add a repository to AWS Marketplace\. If you have already created any necessary repositories \(for example, you are creating a new version and will use existing repositories\), you may skip this step\.

**Note**  
If you previously created repositories that use group IDs \(no longer used by AWS Marketplace\), you will need to create new repositories for new versions\. Your existing repositories will continue to work for versions you previously added\.

**To add repositories**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. Select **Server products** from the **Products** menu\.

1. On the **Current server products** tab, select the product you want to modify, and then choose **Add repositories** from the **Request changes** dropdown\.

1. Enter the name for the repository that you want to create\. If you want to create more than one new repository, choose **Add new repository** for each additional repository, and give it a unique name\.
**Note**  
The repository will have this structure: *<repositoryID>\.dkr\.ecr\.us\-east\-1\.amazonaws\.com/<sellerName>/<repositoryName>*\. When you add items to the repository \(in the following procedure\), they will get a tag and have this structure: *<repositoryID>\.dkr\.ecr\.us\-east\-1\.amazonaws\.com/<sellerName>/<repositoryName>:<tag>*\. The *repositoryID* is an internal ID for AWS Marketplace, the *sellerName* is created based on the name you created for your seller account\. You define the *respositoryName* in this step\. The *tag* is set when you upload an artifact to the respository\.

1. Select **Submit**\.

**Note**  
You may have up to 50 repositories per product\.

A new request is created and shown on the **Requests** tab\. When it is completed, within minutes, you can start adding container images and other artifacts to the repositories you have created\.

**Note**  
Your container images are scanned automatically to see if they meet the [Container\-based product requirements](container-product-policies.md)\. For more information, see [Container product scans for security issues](#container-security)\.

**To upload container images and artifacts to repositories**

1. If it's not already, open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. Select **Server products** from the **Products** menu\.

1. On the **Current server products** tab, select the product you want to modify\.

1. Choose **Add repositories** from the **Request changes** dropdown\.

1. Choose **View exisitng repositories**\.

1. Select the repository to which you want to upload, then select **View push commands** to see a list of instructions, including commands you can use to push Docker container images and Helm charts to that repository\.

1. Use the commands listed to push any needed artifacts from your local repository to the AWS Marketplace repository for your product\.
**Note**  
The **tag** that you provide in the push commands is used to differentiate the version of the artifact that you are uploading to the repository\. Use a tag that makes sense for the version the artifacts are a part of\.

1. Repeat for each container image or artifact you need in your version\.
**Note**  
Your version can include up to 50 container images or artifacts in each delivery option \(see the following procedure for more information on delivery options\)\.

After you have uploaded your artifacts, you are ready to create the version of your product\.

**To add a new version to your container product**

1. If it's not already, open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. Select **Server products** from the **Products** menu\.

1. On the **Current server products** tab, select the product you want to add a version to, and then choose **Add new version** from the **Request changes** dropdown\.

1. On the **Add new version** page, enter the **Version title** and **Release notes** for your version\.

1. For each delivery option of your product, enter the **Title**, **Description**, and **Usage instructions**, as well as compatibility information and artifacts that customers will need\. Include enough information for your customers to understand how to choose the correct delivery option for their needs\.
**Note**  
If your product supports multiple platforms with different container images \(for example, Kubernetes and Ubuntu deployments\), you create one delivery option for each way that customers can set up your product, up to 4 delivery options for a product\.

1. For each delivery option, enter the paths in the AWS Marketplace repositories for each container image needed for your product\. If needed, select **Add container image path** to add additional images\.

1. If needed, select **New delivery option** to add additional delivery options\.

1. Select **Submit**\.

Your request for a new version is created and should complete within minutes\. You can track the request from the **Requests** tab of the **Server products** page\.

**Note**  
Your new version is available to all of your buyers\. If your product is currently set to limited availability, your version is available to the set of buyers that the product is available for\. If your product is currently set to public availability, then your new version is available to all AWS Marketplace buyers\.

If this was your first version set, your product is now ready to be published\. The next topic describes publishing your product\.

## Updating version information<a name="container-product-updating-version"></a>

After a version is created, it can be helpful to provide updated information to your buyers by modifying the information associated with the version\. For example, if you plan to restrict version 1\.0 after version 1\.1 is released, you can update the description of version 1\.0 to direct buyers to version 1\.1, with the date that the version will be restricted\. You update the version information from the AWS Marketplace Management Portal\.

**To update version information**

1. Open the AWS Marketplace Management Portal at [https://aws.amazon.com/marketplace/management/tour/](https://aws.amazon.com/marketplace/management/tour/), and then sign in to your seller account\.

1. Go to the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page, and on the **Current server products** tab, select the product you want to modify\.

1. From the **Request changes** dropdown, choose **Update version information**\.

1. On the **Update version** page, select the version that you want to update\.

1. You can update the **Release notes** for the version\.
**Note**  
For versions that are not yet publicly available, you can also edit the **Version title**\.

1. For delivery options that haven't been restricted, you can edit the following fields:
   + **Description**
   + **Usage Instructions**
   + **Compatible AWS Services**
**Note**  
For delivery options in versions that are not yet publicly available, you can also change the **Title of delivery option**, the **Container images**, and the **Deployment resources**\.

1. Select **Submit**\.

1. Verify that the request appears on the **Requests** tab with the **Under review** status\.

You can check the status of your request at any time from the **Requests** tab of the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page\.

## Creating or updating product information for your container product<a name="update-container-product-info"></a>

After you have created your product ID and set the pricing, you can edit your product information, including what customers will see about your container product in the AWS Marketplace\. The following procedure outlines creating the product details for your product\.

**To create product details for your container product**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. Go to the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page, and on the **Current server products** tab, select the container product you want to modify\.

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
Image URLs must be in an S3 bucket that is publicly accessible\. For more details about the logo format, see [Company and product logo requirements](product-submission.md#seller-and-product-logos)\.

1. Select **Submit**\.

1. Verify that the request appears on the **Requests** tab with the **Under review** status\. You may need to refresh the page to see the request on the list\.

You can check the status of your request at any time from the **Requests** tab of the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page\.

## Publishing container products<a name="container-product-publishing"></a>

When you initially create your product, its availability is limited to just your account\. Once your product is ready for testing \(including having product details filled in and the first version created\), you can make it available to other accounts for testing, or to all accounts as a public product\.

**Note**  
Before publishing publicly, you should review your product to ensure accuracy, including image links, deployment templates, descriptions, and pricing\. Your pricing model can't be changed for publicly published products\.

To publish your limited product to additional accounts or for public availability, contact the [ AWS Marketplace Seller Operations team](https://aws.amazon.com/marketplace/management/contact-us/)\. In your request, provide the product ID and describe the changes that you want to make\.

**Note**  
You can also choose to restrict a version that you no longer want available to buyers\. You can include this in a request to publish a product publicly, to avoid test versions appearing in public products\.  
You can't restrict a version if it will leave your public product with no public versions\.

When you publicly publish a container product, you make it visible to all AWS customers who can then subscribe and launch your product\. The AWS Marketplace Seller Operations team reviews the data in your product information, as well as your test calls to the AWS Marketplace Metering Service\.

## Container product scans for security issues<a name="container-security"></a>

When you submit a container image URL, we scan it and check for security vulnerabilities\. We examine the images you provide for known security vulnerabilities\. To do this, we perform a layer\-by\-layer static scan on the image\. If we find critical vulnerabilities with remotely exploitable risk vectors, we provide you with a list of found issues\. We strongly recommend that you perform your own security analysis using a container image scanner such as Clair, Twistlock, Aqua Security, or Trend Micro to avoid delays in the ingestion and publishing process\. 

Your choice of base image for building your container images can have a significant influence on the security profile of the final image\. If you choose a base image that already has known critical vulnerabilities, they will be flagged because of the base layer, even if your application software layers are clean\. We recommend that you verify that you are starting with a vulnerability\-free base container before you build your images and submit them to AWS Marketplace\. 