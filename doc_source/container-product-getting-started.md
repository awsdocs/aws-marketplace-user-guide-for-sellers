# Getting started with container products<a name="container-product-getting-started"></a>

This topic describes all the steps related to creating, testing, and publishing your first container product for AWS Marketplace\. 

**Topics**
+ [Prerequisites](#container-prereq)
+ [Creating a container product](#create-container-product)
+ [Creating the product ID for your container product](#create-initial-container-product)
+ [Creating or updating pricing details for container products](#container-product-load-form)
+ [Integrating AWS Marketplace Metering Service for your container product](#getting-started-integrate-metering)
+ [Integrating AWS License Manager for your container product](#container-integrate-LM)
+ [Adding a new version of your product](#container-add-version)
+ [Updating version information](#container-product-updating-version)
+ [Creating or updating product information for your container product](#update-container-product-info)
+ [Publishing container products](#container-product-publishing)
+ [Container product scans for security issues](#container-security)

## Prerequisites<a name="container-prereq"></a>

Before you get started, you must complete the following prerequisites:

1. Access and use the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\. This is the tool that you use to register as a seller and manage the products that you sell on AWS Marketplace\. For more information, see [AWS Marketplace Management Portal](https://docs.aws.amazon.com/marketplace/latest/userguide/user-guide-for-sellers.html#management-portal)\.

1. Register as a seller, and submit your tax and banking information\. For more information, see [Seller registration process](seller-registration-process.md)\.

1. Create at least one container in Amazon Elastic Container Service \(Amazon ECS\), Amazon Elastic Kubernetes Service \(Amazon EKS\), or AWS Fargate\. Make sure that you have links for the associated images\.

1. Plan how you'll create and integrate your container product in AWS Marketplace\.

   We recommend that you plan your pricing, entitlement, and metering strategy well in advance of publicly publishing your product\.
   + For information about the requirements for container\-based products, see [Container\-based product requirements](container-product-policies.md)\.
   + For information about setting the pricing for your product, see [Container product pricing](pricing-container-products.md)\.
   + For information about custom metering for your paid container\-based product, see [Hourly and custom metering with AWS Marketplace Metering Service](container-products-billing-integration.md#entitlement-and-metering-for-paid-products)\.

## Creating a container product<a name="create-container-product"></a>

Creating a container product involves the following steps:

1. [Create the product ID](#create-initial-container-product)\.

1. [Create the pricing details](#container-product-load-form)\.

1. For paid products, [integrate metering into your product](#getting-started-integrate-metering)\.

1. [Add a new version of your product](#container-add-version), including:

   1. Add repositories for your containers\.

   1. Upload the final containers into the repositories\.

   1. Create the first version of the product with your first container images\.

1. [Update the product version information](#container-product-updating-version)\.

1. [Publish the product for buyers](#container-product-publishing)\.

The first two steps must happen before you can edit any other details in AWS Marketplace\. However, you can perform the other steps in the order that makes the most sense to you or in parallel\.

The following topics describe each of these steps\.

## Creating the product ID for your container product<a name="create-initial-container-product"></a>

To get started with a container product, you must create a product ID record in AWS Marketplace\. The product ID is used to track your product throughout its lifecycle\.

Use the following procedure to create a new container product in the AWS Marketplace Management Portal, and generate the product ID\.

**To create the container product ID**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the menu bar, expand **Assets**, and choose **Container**\.

1. Enter a customer\-facing name for your product, and choose **Create**\. If necessary, you can change this name later\.

1. Make a note of the **Product ID** for your later use when you create or update the product pricing details\.
**Tip**  
If you lose your product ID, you can find it in the AWS Marketplace Management Portal by choosing **Container** from the **Assets** menu\. The **Containers** page shows a list of your products with their associated product IDs\.

You now have your initial container product and product ID\. Next, add pricing details for your product\.

## Creating or updating pricing details for container products<a name="container-product-load-form"></a>

To update the pricing details for your container product, you must use a product load form \(PLF\)\. The PLF for your product is a spreadsheet that contains information about your product\. The following procedure outlines using the PLF to update information about your product, including pricing details\.

**Note**  
For more information about pricing models for container products, see [Container product pricing](pricing-container-products.md)\.  
Your pricing and metering must be aligned\. For more information about metering with container products, see [Hourly and custom metering with AWS Marketplace Metering Service](container-products-billing-integration.md#entitlement-and-metering-for-paid-products)\.

**To update pricing for your container product by using the product load form**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the menu bar, expand **Assets**, and choose **File upload**\.

1. From **Product load forms for download** on the right side, choose **Containers Product Load Form**\.

1. Open the PLF spreadsheet on your computer, and fill out the fields to define your product\. This information includes your product ID that you made note of when you created your container product\.
**Tip**  
When viewing the PLF in Microsoft Excel, hover over each of the fields to show comments that provide guidance about how to fill in each field\. 

   Provide pricing and metering dimensions, based on your pricing model for your product\. For more information, see the following:
   + [Product load form for custom metering](container-metering-meterusage.md#custom-metering-product-load-form)
   + [Product load form for hourly metering](container-metering-registerusage.md#hourly-metering-product-load-form)
**Note**  
Required fields have a red header with the word **REQUIRED** in the spreadsheet\. Make sure that all of these fields are filled out to avoid delays in processing your request\.

1. Save your PLF\.

1. If it's not still open, open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the menu bar, expand **Assets**, and choose **File Upload**\.

1. In **Upload File**, browse your computer and choose the PLF you saved for this container product\.

1. Provide a brief description for this PLF to help you identify it among the other PLFs you upload\.

1. Choose **Upload**\. Your uploaded PLF appears in a table at the bottom of the page\.

Your pricing details are reviewed and updated manually by the AWS Marketplace Seller Operations team\. It typically takes a few business days to complete the update\. You can check the status by choosing **Container** from the **Assets** menu in the AWS Marketplace Management Portal\. An email message is sent to you when the review of your product pricing details is complete\.

**Note**  
Your container product is now created, in a limited state\. Your account can view the product for testing and modify it\. To make it visible to other test accounts, or when it's ready to be made publicly available, see [Publishing container products](#container-product-publishing)\.

You can edit your container product pricing by following this same procedure, until you publicly publish the product\.

After you create the pricing details for your product, you can add other product details, integrate metering into your product, and create a software version for your product\.

## Integrating AWS Marketplace Metering Service for your container product<a name="getting-started-integrate-metering"></a>

For container\-based products with usage pricing, you use the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) for both checking entitlement to use your product and metering usage for billing\. You must meter for the pricing model that you created when setting your pricing information\. For more information, see [Hourly and custom metering with AWS Marketplace Metering Service](container-products-billing-integration.md#entitlement-and-metering-for-paid-products)\.

## Integrating AWS License Manager for your container product<a name="container-integrate-LM"></a>

For container\-based products with contract pricing, you use the AWS License Manager to associate licenses with your product\. 

For more information about integrating with AWS License Manager, see [Contract pricing with AWS License Manager](container-license-manager-integration.md)\.

## Adding a new version of your product<a name="container-add-version"></a>

Your product might have several versions over its lifetime\. Each version has a set of container images that are specific to that version\.

**Note**  
You can't add a version to your product until you have created the product ID and the pricing for your product\. For more information about these steps, see [Creating the product ID for your container product](#create-initial-container-product), and [Creating or updating pricing details for container products](#container-product-load-form)\.

Creating a version of your product involves the following steps:

**Topics**
+ [Step 1: Adding repositories](#add-repositories)
+ [Step 2: Uploading container images and artifacts to repositories](#upload-resources)
+ [Step 3: Adding a new version to your container product](#add-new-version)

Your container images and other artifacts for your product are stored in repositories in AWS Marketplace\. Typically, you create one repository for each artifact needed, but the repository can store multiple versions of the artifact \(with different tags\)\. 

**Note**  
All images in your product deployment must use images from the AWS Marketplace repositories\.

### Step 1: Adding repositories<a name="add-repositories"></a>

 The following procedure describes how to add any needed repositories in AWS Marketplace\.

**To add repositories**

1. Sign in to the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. Select **Server** from the **Products** menu\.

1. On the **Server products** tab, select the product you want to modify, and then choose **Add repositories** from the **Request changes** dropdown\.

1. Enter the name for the repository that you want to create\. If you want to create more than one new repository, choose **Add new repository** for each additional repository, and give it a unique name\.
**Note**  
The repository will have this structure: `<repositoryID>.dkr.ecr.us-east-1.amazonaws.com/<sellerName>/<repositoryName>`\. When you add items to the repository \(in the following procedure\), they will get a tag and have this structure: `<repositoryID>.dkr.ecr.us-east-1.amazonaws.com/<sellerName>/<repositoryName>:<tag>`\. The `repositoryID` is an internal ID for AWS Marketplace\. The `sellerName` is based on the name you created for your seller account\. You define the `respositoryName` in this step\. The `tag` is set when you upload an artifact to the repository\.

1. Select **Submit**\.

**Note**  
You can have up to 50 repositories per product\.

A new request is created and shown on the **Requests** tab\. When it's completed, within minutes, you can start adding container images and other artifacts to the repositories you have created\.

### Step 2: Uploading container images and artifacts to repositories<a name="upload-resources"></a>

**To upload container images and artifacts to repositories**

1. Sign in to the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the **Products** menu, choose **Server**\.

1. On the **Server products** tab, select the product you want to modify\.

1. Choose **Add repositories** from the **Request changes** dropdown\.

1. Choose **View existing repositories**\.

1. Select the repository to which you want to upload\.

1. Select **View push commands** to open a list of instructions, including commands you can use to push Docker container images and Helm charts to that repository\. 

   For general information about how to push container images and other artifacts to repositories, refer to [Pushing an image](https://docs.aws.amazon.com/AmazonECR/latest/userguide/image-push.html) in the *Amazon Elastic Container Registry User Guide*\.
**Note**  
You can use the following Amazon Elastic Container Registry \(Amazon ECR\) API operations when calling `docker pull` or `docker push`:  
`DescribeImages` – Use this to review the metadata about the images in a repository\.
`GetAuthorizationToken` – Use to authenticate before uploading artifacts to the repository, then use `docker pull` or `docker push` commands\.
`ListImages` – Use to view a list of images you pushed\.

1. Use the commands listed to push any needed artifacts from your local repository to the AWS Marketplace repository for your product\.
**Note**  
The **tag** that you provide in the `push` commands is used to differentiate the version of the artifact that you are uploading to the repository\. Use a tag that makes sense for the version the artifacts are a part of\.

1. Repeat for each container image or artifact you need in your version\.
**Note**  
Your version can include up to 50 container images or artifacts in each delivery option\. Refer to the following procedure for more information about delivery options\.

After you upload your artifacts, you're ready to create the version of your product\. 

**Note**  
Your container images are scanned automatically to see if they meet the [Container\-based product requirements](container-product-policies.md)\. For more information, refer to [Container product scans for security issues](#container-security)\.

#### Adding a new delivery option without a template<a name="add-delivery-option"></a>

1. To add a new delivery option without a template, choose **Add delivery option**\. After adding an option, follow the instructions in the following steps to configure it\.

1. Choose a delivery method for the delivery option\. The delivery method determines how buyers will launch your software\.
   + For a **Container image** delivery option, provide paths to container images in an Amazon Elastic Container Registry \(Amazon ECR\) repository that was created in the AWS Marketplace console\. Buyers use the container image paths to launch the software by pulling the images directly into their environments\.
   + For a **Helm chart** delivery option, provide paths to Helm charts in an Amazon ECR repository that was created in the AWS Marketplace console\. Buyers install the Helm charts in their deployment environment to launch the software\.

1. To add a **Container image** delivery option, perform the following steps:

   1. In **Container images**, add the Amazon ECR URL to the container images that contain the product version software\.

   1. In **Delivery option title** and **Deployment option description**, enter a title and description for this delivery option\.

   1. In **Usage instructions**, enter detailed information to help your buyers use your software after launching it\.

   1. In **Supported services**, select the environments that buyers can launch the software in\.

   1. In **Deployment templates**, add resources that buyers can use to launch the software\. Enter a title and a URL to the resource for each template\.

1. To add a **Helm chart** delivery option, perform the following steps:

   1. In **Helm chart**, add the Amazon ECR URL to the Helm chart that buyers will install in their deployment environment to launch your software\.

   1. In **Container images**, add the Amazon ECR URL to the container images that contain the product version software\.

   1. In **Delivery option title** and **Deployment option description**, enter a title and description for this delivery option\.

   1. In **Usage instructions**, enter detailed information to help your buyers use your software after launching it\.

   1. In **Supported services**, select the environments that buyers can launch the software in\.

   1. *Optional \- * In **Helm release name**, enter the name of the Kubernetes namespace where the Helm chart will be installed\.

   1. *Optional \- * In **Helm installation namespace**, enter the name for the Helm release that will be used by the `helm install` command\.

   1. *Optional \- * In **Kubernetes service account name**, enter the name of the Kubernetes service account that will be used to connect to AWS Identity and Access Management \(IAM\)\. The Kubernetes service account calls AWS services such as licensing or metering\.

   1. Choose to enable **QuickLaunch** on this product version\. QuickLaunch is a feature in AWS Marketplace\. Buyers can use QuickLaunch to create an Amazon EKS cluster quickly and launch your software on it by using AWS CloudFormation\. For more information, see [QuickLaunch in AWS Marketplace](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-configuring-a-product.html#buyer-launch-container-quicklaunch)\.

   1. In **Override parameters**, enter parameters that will be used in the Helm CLI commands that launch the software\. Buyers can override the provided default values\. If you have enabled QuickLaunch, also enter a parameter name and description for the CloudFormation form\.

   1. Choose **Hide passwords and secrets** to mask sensitive information in consoles, command line tools, and APIs\. For more information, see the `NoEcho` parameter documentation in [Parameters](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html) in the *AWS CloudFormation User Guide*\.

1. If needed, choose **Add delivery option** to add additional delivery options and perform the instructions in the previous steps to configure them\.

1. Select **Submit**\.

### Step 3: Adding a new version to your container product<a name="add-new-version"></a>

**To add a new version to your container product**

1. Sign in to the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. Choose **Server** from the **Products** menu\.

1. On the **Server products** tab, select the product you want to add a version to\. Then choose **Add new version** from the **Request changes** dropdown\.

1. On the **Add new version** page, enter the **Version title** and **Release notes** for your version\.

1. After entering the version details, the next step is to add delivery options\. Delivery options are sets of instructions and information that buyers can use to launch the software from your product version\. Delivery options are known as *fulfillment options* to buyers\.
**Note**  
Your product can support multiple platforms with different container images \(for example, Kubernetes and Ubuntu deployments\)\. You can create one delivery option for each way that customers can set up your product, up to four delivery options for a product\.

   1. If the product already has delivery options in other versions, you can use the existing option as a template to add a delivery option to the new version\. In **Delivery options**, choose the delivery option that you want to add from the list\. You can edit the option using the instructions in the following steps\.

   1. To add a new delivery option without a template, choose **Add delivery option**\. After adding an option, follow the instructions in the following steps to configure it\.

1. Choose a delivery method for the delivery option\. The delivery method determines how buyers will launch your software\.
   + For a **Container image** delivery option, provide paths to container images in an Amazon Elastic Container Registry \(Amazon ECR\) repository that was created in the AWS Marketplace console\. Buyers use the container image paths to launch the software by pulling the images directly into their environments\.
   + For a **Helm chart** delivery option, provide paths to Helm charts in an Amazon ECR repository that was created in the AWS Marketplace console\. Buyers install the Helm charts in their deployment environment to launch the software\.

1. To add a **Container image** delivery option, perform the following steps:

   1. In **Container images**, add the Amazon ECR URL to the container images that contain the product version software\.

   1. In **Delivery option title** and **Deployment option description**, enter a title and description for this delivery option\.

   1. In **Usage instructions**, enter detailed information to help your buyers use your software after launching it\.

   1. In **Supported services**, select the environments that buyers can launch the software in\.

   1. In **Deployment templates**, add resources that buyers can use to launch the software\. Enter a title and a URL to the resource for each template\.

1. To add a **Helm chart** delivery option, perform the following steps:

   1. In **Helm chart**, add the Amazon ECR URL to the Helm chart that buyers will install in their deployment environment to launch your software\.

   1. In **Container images**, add the Amazon ECR URL to the container images that contain the product version software\.

   1. In **Delivery option title** and **Deployment option description**, enter a title and description for this delivery option\.

   1. In **Usage instructions**, enter detailed information to help your buyers use your software after launching it\.

   1. In **Supported services**, select the environments that buyers can launch the software in\.

   1. *Optional \- * In **Helm release name**, enter the name of the Kubernetes namespace where the Helm chart will be installed\.

   1. *Optional \- * In **Helm installation namespace**, enter the name for the Helm release that will be used by the `helm install` command\.

   1. *Optional \- * In **Kubernetes service account name**, enter the name of the Kubernetes service account that will be used to connect to AWS Identity and Access Management \(IAM\)\. The Kubernetes service account calls AWS services such as licensing or metering\.

   1. Choose to enable **QuickLaunch** on this product version\. QuickLaunch is a feature in AWS Marketplace\. Buyers can use QuickLaunch to create an Amazon EKS cluster quickly and launch your software on it by using AWS CloudFormation\. For more information, see [QuickLaunch in AWS Marketplace](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-configuring-a-product.html#buyer-launch-container-quicklaunch)\.

   1. In **Override parameters**, enter parameters that will be used in the Helm CLI commands that launch the software\. Buyers can override the provided default values\. If you have enabled QuickLaunch, also enter a parameter name and description for the CloudFormation form\.

   1. Choose **Hide passwords and secrets** to mask sensitive information in consoles, command line tools, and APIs\. For more information, see the `NoEcho` parameter documentation in [Parameters](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html) in the *AWS CloudFormation User Guide*\.

1. If needed, choose **Add delivery option** to add additional delivery options and perform the instructions in the previous steps to configure them\.

1. Select **Submit**\.

Your request for a new version is created and should complete within minutes\. You can track the request from the **Requests** tab of the **Server products** page\.

**Note**  
Your new version is available to all of your buyers\. If your product is currently set to limited availability, your version is available to the set of buyers that the product is available for\. If your product is currently set to public availability, then your new version is available to all AWS Marketplace buyers\.

If this was your first version set, your product is now ready to be published\. For information about how to publish a product, see [Publishing container products](#container-product-publishing)\.

Your request for a new version is created and should complete within minutes\. You can track the request from the **Requests** tab of the **Server products** page\.

**Note**  
Your new version is available to all of your buyers\. If your product is currently set to limited availability, your version is available to the set of buyers that the product is available for\. If your product is currently set to public availability, then your new version is available to all AWS Marketplace buyers\.

If this was your first version set, your product is now ready to be published\. The next topic describes publishing your product\.

If this was your first version set, your product is now ready to be published, see [Publishing container products](#container-product-publishing)\.

## Updating version information<a name="container-product-updating-version"></a>

After a version is created, it can be helpful to provide updated information to your buyers by modifying the information associated with the version\. For example, if you plan to restrict version 1\.0 after version 1\.1 is released, you can update the description of version 1\.0 to direct buyers to version 1\.1\. Provide the date that version 1\.0 will be restricted\. You update the version information from the AWS Marketplace Management Portal\.

**To update version information**

1. Sign in to the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. Select **Server** from the **Products** menu\. 

1. On the **Server products** tab, select the product that you want to modify\.

1. From the **Request changes** dropdown, choose **Update version information**\.

1. On the **Update version** page, select the version that you want to update and choose **Submit**\.

1. Make updates to the selected version\. The fields that are available for updating depend on the status of the product version or delivery option\.

   1. For all versions, you can update the **Release notes**\.

   1. For versions that are not yet publicly available, you can update the **Version title**\.

   1. For delivery options that haven't been restricted, you can update the following fields:
      + **Description**
      + **Usage instructions**
      + **Supported services**

   1. For delivery options in versions that are not yet publicly available, you can update the following fields:
      + **Delivery option titles**
      + **Helm chart** \(for **Helm chart** delivery options only\)
      + **Container images**
      + **Deployment resources**

1. Choose **Submit**\.

1. Verify that the request appears on the **Requests** tab with the **Under review** status\.

You can check the status of your request at any time from the **Requests** tab of the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page\.

## Creating or updating product information for your container product<a name="update-container-product-info"></a>

After you have created your product ID and set the pricing, you can edit your product information, including what customers will see about your container product in the AWS Marketplace\. The following procedure outlines creating the product details for your product\.

**To create or update product details for your container product**

1. Sign in to the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. Select **Server** from the **Products** menu\. 

1. On the **Server products** tab, select the product that you want to modify\.

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
Image URLs must be in an Amazon S3 bucket that is publicly accessible\. For more details about the logo format, see [Company and product logo requirements](product-submission.md#seller-and-product-logos)\.

1. Select **Submit**\.

1. Verify that the request appears on the **Requests** tab with the **Under review** status\. You might need to refresh the page to see the request on the list\.

You can check the status of your request at any time from the **Requests** tab of the [ Server Products](https://aws.amazon.com/marketplace/management/products/server) page\.

## Publishing container products<a name="container-product-publishing"></a>

When you initially create your product, its availability is limited to just your account\. Once your product is ready for testing \(including having product details filled in and the first version created\), you can make it available to other accounts for testing, or to all accounts as a public product\.

**Note**  
Before publishing publicly, you should review your product to ensure accuracy, including image links, deployment templates, descriptions, and pricing\. Your pricing model can't be changed for publicly published products\.

To publish your limited product to additional accounts or for public availability, contact the [AWS Marketplace Seller Operations team](https://aws.amazon.com/marketplace/management/contact-us/)\. In your request, provide the product ID and describe the changes that you want to make\.

**Note**  
You can also choose to restrict a version that you no longer want available to buyers\. You can include this in a request to publish a product publicly, to avoid test versions appearing in public products\.  
You can't restrict a version if it will leave your public product with no public versions\.

When you publicly publish a container product, you make it visible to all AWS customers who can then subscribe and launch your product\. The AWS Marketplace Seller Operations team reviews the data in your product information, as well as your test calls to the AWS Marketplace Metering Service\.

## Container product scans for security issues<a name="container-security"></a>

When you submit a container image URL, we scan it and check for security vulnerabilities\. We examine the images you provide for known security vulnerabilities\. To do this, we perform a layer\-by\-layer static scan on the image\. If we find critical vulnerabilities with remotely exploitable risk vectors, we provide you with a list of found issues\. We strongly recommend that you perform your own security analysis using a container image scanner such as Clair, Twistlock, Aqua Security, or Trend Micro to avoid delays in the ingestion and publishing process\. 

Your choice of base image for building your container images can have a significant influence on the security profile of the final image\. If you choose a base image that already has known critical vulnerabilities, they will be flagged because of the base layer, even if your application software layers are clean\. We recommend that you verify that you're starting with a vulnerability\-free base container before you build your images and submit them to AWS Marketplace\. 