# Publishing your product in AWS Marketplace<a name="ml-publishing-your-product-in-aws-marketplace"></a>

 Before you can publish your model package or algorithm, the following are required: 
+  An AWS account that is registered as an AWS Marketplace seller\. You can do this in the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\. 
+  A completed seller profile under the [Settings](http://aws.amazon.com/marketplace/management/seller-settings) page in the AWS Marketplace Management Portal\. 
+  For publishing paid products, you must complete the tax interview and bank forms\. This is not required for publishing free products\. For more information, see [Seller registration process](https://docs.aws.amazon.com/marketplace/latest/userguide/seller-registration-process.html)\. 
+ You must have permissions to access the AWS Marketplace Management Portal and Amazon SageMaker\. For more information, see [Permissions required](#ml-permissions-required)\.

## Overview of publishing process<a name="ml-overview-of-publishing-process"></a>

 There are four steps in the publishing process: 

1.  **Submit product** – Create a listing with the description, usage information, and other details of your model package or algorithm product\. After you submit your product for publishing, it takes about an hour until the status changes to the next step\. 

1.  **Test product** – Use your AWS account that is registered as an AWS Marketplace seller to preview the listing in the AWS Marketplace, subscribe to it, and test the product\. In addition, other allowed AWS accounts can preview and test the product\. If any changes are necessary, you can go back and edit the listing details\. 

1.  **Sign off for publishing** – When your product is ready to go live, return to the AWS Marketplace Management Portal, and choose **Sign off and publish**\. 

1.  **Product goes live** – Your product is now live in the AWS Marketplace\. You can maintain your product by publishing new versions with updates or product fixes\.

## Permissions required<a name="ml-permissions-required"></a>

 To publish an Amazon SageMaker product, the AWS Identity and Access Management \(IAM\) user or role you are logged in as requires one or both of the following IAM actions:
+  **sagemaker:DescribeModelPackage** – For listing a model package 
+  **sagemaker:DescribeAlgorithm** – For listing an algorithm 

 For the AWS Marketplace permissions needed, or for managing your seller account, see [Policies and permissions for AWS Marketplace sellers](https://docs.aws.amazon.com/marketplace/latest/userguide/detailed-management-portal-permissions.html)\. 

## Creating your product listing<a name="ml-creating-your-listing"></a>

 The following is a walkthrough for creating your product listing in the AWS Marketplace for both model package and algorithm products\. 

**Note**  
 Before creating your listing, ensure that you have the required resources specified in [Requirements and best practices for creating machine learning products](ml-listing-requirements-and-best-practices.md)\. 

The process has the following steps:

**Topics**
+ [Step 1: Create a new listing](#create-new-listing)
+ [Step 2: Provide general product information](#provide-general-info)
+ [Step 3: Add your launch option](#add-launch-option)
+ [Step 4: Set the pricing and terms](#set-pricing-and-terms)
+ [Step 5: Submit your product for publishing](#submit-product-for-publishing)

### Step 1: Create a new listing<a name="create-new-listing"></a>

**To create a new machine learning product listing**

1. Sign in to your seller AWS account and navigate to the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management)\. 

1.  In the top menu, navigate to **Products** and then **Machine learning**\. 

1.  Choose **Create new listing**\. 

**Note**  
 On the **New Product** page, in the **Product summary** section, you can view the current status, privacy setting, product type, creator, and product ID\.

### Step 2: Provide general product information<a name="provide-general-info"></a>

**To provide general product information**

1. In the **General product information** section, for **Product descriptions**, choose **Add**\. 

   1. For the **Product visibility** section, choose one of the following options:
      + **Public** – The product will initially be available to a limited set of AWS accounts for testing\. After you sign off and publish it, the product is publicly discoverable and available for subscription by all customers\. 
      + **Private** – The product will only be visible to the AWS accounts that you specify\. You will not be able to make this product public in the future\.

   1. Enter **Product title**, **Short product description**, **Product overview**,** Product category 1**, and other details\. You can change these values later\. For product descriptions, see [Requirements and best practices for creating machine learning products](ml-listing-requirements-and-best-practices.md)\. 

   1. Choose **Continue** when complete\. 

1. For **Promotional Resources**, provide a product logo, search keywords, and relevant resource links\. You can change these values later\.

   1. Choose **Continue** when complete\. 

1. For **Support Information**, choose whether you are offering support for the product\.

   1. If you choose **Yes**, provide support and contact details\. You can change these values later\.

   1. Choose **Continue** when complete\. 

1. For **Region Availability**, choose the specific AWS Regions you want to list your product in\. 

   The default value is **Make available in all current and future supported Regions**\. 

   1. Choose **Continue** when complete\. 
**Note**  
After you submit your draft for publishing, you can't change this selection\. 

The next step in publishing your product is to provide the launch option, which is the model package or algorithm that you're selling\.

### Step 3: Add your launch option<a name="add-launch-option"></a>

**To add your launch option**

1. In the **Launch option** section, for **Enter ARN**, enter the Amazon Resource Name \(ARN\) of your model package or algorithm\. 

   You can find the ARN in the Amazon SageMaker console [Model Packages](https://console.aws.amazon.com/sagemaker/home#/model-packages/my-resources) or [Algorithms](https://console.aws.amazon.com/sagemaker/home#/algorithms/my-resources) pages\.   
**Example ARN for a model package**  

   `arn:aws:sagemaker:<region>:<account-id>:model-package/<model-package-name>`  
**Example ARN for an algorithm**  

   `arn:aws:sagemaker:<region>:<account-id>:algorithm/<algorithm-name>`

1. Choose **Add**\. 

1. The following steps differ depending on if you publish a model package or algorithm product\. With the exception of the buyer\-facing version number, you can change the version details later\. 

   1. For **Step 1: Enter version details and Git repository links**, provide the version number, release notes, and URLs to the sample Jupyter notebook and GitHub repository\. 

   1. For *algorithm products* only, for **Step 2: Enter details describing the training data inputs**, describe the training data and include an example training data resource along with an overview of the training algorithm\. 

      The algorithm metrics, channel specification, and hyperparameters are automatically displayed on the product detail page based on the values you provided when you created the algorithm resource in SageMaker\.

      The following examples show how the training data inputs details appear to you as a seller, and how training data inputs details appear to the buyer\.  
**Example training data inputs – seller view**    
![\[Example of how training data inputs appear to a seller.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/algo-training-description-seller.jpg)  
**Example training data inputs – buyer view**    
![\[Example of how training data inputs appear to a buyer.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/algo-training-description-buyer.jpg)

      The following examples show how the custom attributes \(invocation parameters\) appear to you as a seller, and how custom attributes \(invocation parameters\) appear to the buyer\.  
**Example custom attributes \(invocation parameters\) – seller view**    
![\[Example of how custom attributes appear to a seller.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/model-custom-attributes-seller.jpg)  
**Example custom attributes \(invocation parameters\) – buyer view**    
![\[Example of how custom attributes appear to a buyer.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/model-custom-attributes-buyer.jpg)

   1. For **Step 3: Enter input details**, provide the model or algorithm input details and URLs for the sample input files\. 

      The following examples show how the model data inputs details appear to you as a seller, and how model data inputs details appear to the buyer\.  
**Example model data inputs – seller view**    
![\[Example of how model data inputs appear to a seller.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/model-input-details-seller.jpg)  
**Example model data inputs – buyer view**    
![\[Example of how model data inputs appear to a buyer.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/model-input-details-buyer.jpg)

   1. For **Step 4: Enter output details**, provide the model or algorithm output details and sample outputs as text or URLs\. 

      For usage information, see [Requirements and best practices for creating machine learning products](ml-listing-requirements-and-best-practices.md)\.

      The following examples show how the model data outputs details appear to you as a seller, and how model data outputs details appear to the buyer\.  
**Example model data outputs – seller view**    
![\[Example of how model data outputs appear to a seller.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/model-output-details-seller.jpg)  
**Example model data outputs – buyer view**    
![\[Example of how model data outputs appear to a buyer.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/model-output-details-buyer.jpg)

   1. For **Step 5: Review supported instances and create**, set the recommended instances\. 
      + If this is a *model package* product, choose the recommended instance type from your supported instances for both the batch transform and real\-time deployments\. 
      + If this is an *algorithm* product, also choose the recommended instance type training jobs\.

       You can't choose instance types that your model package or algorithm resource doesn't support\. The supported instance types were selected when you created those resources in Amazon SageMaker\.

1.  Choose **Continue** when complete\. 

**Note**  
 Clear usage information that describes the expected inputs and outputs of your product \(with examples\) is crucial for supporting a positive buyer experience\. For more information, see [Requirements and best practices for creating machine learning products](ml-listing-requirements-and-best-practices.md)\. 

The next step in publishing your product is to set the pricing and terms\.

### Step 4: Set the pricing and terms<a name="set-pricing-and-terms"></a>

**To set the pricing and terms**

1. In the **Pricing and terms** section, choose **Add offer**\. 

1.  Set your **Pricing**\. 

   You can provide your software for free, set your paid pricing, or enable a free trial period\. For more information, see [Machine learning product pricing](machine-learning-pricing.md)\. 

1.  Upload a plaintext file to use as your End User License Agreement \(EULA\)\. 

1. Choose **Save and close**\. 

 You have provided all the information for your product\. The next step is to publish it to limited availability so that you can test the product\.

### Step 5: Submit your product for publishing<a name="submit-product-for-publishing"></a>

**To submit your product for publishing**

1. On the **New Product** page, in the **Submit for publishing** section, under **Additional test accounts – optional**, enter one or more AWS account IDs for your additional testers\.

1. Choose **Submit for publishing**\. 

This starts the publishing process by creating a preview listing in AWS Marketplace that you \(and your optional testers\) can subscribe to and use for testing\. 

You are now ready to test your product\. For more information about testing your machine learning product, see [Testing your product](#ml-testing-your-product)\.

After testing your product, you can redo the steps above if there are any changes that need to be made\. When you're ready for your product to be available to buyers, you can [sign off for publishing](#ml-sign-off-for-publishing)\.

## Testing your product<a name="ml-testing-your-product"></a>

After the initial submission of your product, it takes about an hour for your preview listing to be ready\. After the status changes to **Test Product**, your seller account and other allow\-listed AWS accounts can preview the listing in AWS Marketplace, subscribe to the product, and test it\. 

**To see a preview of your listing**

1. In the AWS Marketplace Management Portal, navigate to the **Product Overview** page\.

1. Choose **Go to staged product**\. 

1. If you want to make changes, choose **Edit product** and follow the same steps as [creating your product listing](#ml-creating-your-listing)\. 

1. When you're ready for your product to be published publicly for all buyers to see, follow the steps in [Signing off for publishing](#ml-sign-off-for-publishing)\.

 To add other AWS accounts to test your product before publishing, contact [AWS Marketplace Seller Operations](http://aws.amazon.com/marketplace/management/contact-us) and provide the AWS account IDs\. Allow\-listed accounts display a **Limited** badge alongside the product version on the product detail page\. 

## Signing off for publishing<a name="ml-sign-off-for-publishing"></a>

This step is to be done after you write your descriptions, pricing, and usage information, and then test your product\.

**To sign off for publishing**

1. Sign in to your seller AWS account and navigate to the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management)\. 

1.  In the top menu, navigate to **Products** and then **Machine learning**\. 

1. Navigate to the **Product Overview** of your product\.

1. Choose **Sign off and publish**\. 

## Updating your product<a name="ml-updating-your-product"></a>

You can use the [Machine Learning Listings](http://aws.amazon.com/marketplace/management/ml-products) page in the AWS Marketplace Management Portal to update your model package or algorithm product in the following ways: 
+ [Add new versions](#ml-adding-new-versions) – You can add new model package or algorithm resources as new versions of your existing product\.
+ [Restrict versions](#ml-restricting-versions) – You can restrict previous versions of your existing product\.
+ [Remove product](#ml-remove-or-delist-a-product) – You can remove your entire product\.

### Adding new versions<a name="ml-adding-new-versions"></a>

**To add new versions of your model package or algorithm resources**

1. Navigate to the [Machine Learning Listings](http://aws.amazon.com/marketplace/management/ml-products) page in the AWS Marketplace Management Portal\.

1. Navigate to the **Product Overview** of your existing product\.

1.  Choose **Edit product**\. 

1. Under **Launch option**, choose **Edit**\. 

1. To add the ARN of your resource, navigate to the **Versions** page, and choose **Add new version**\. 

   For more information about adding a launch option, see [Creating your product listing](#ml-creating-your-listing)\. 

**Note**  
Usage information is specific to each product version\. Continue to follow the [Requirements and best practices for creating machine learning products](ml-listing-requirements-and-best-practices.md) when adding usage information to new versions\. 

When your buyers launch your product from its AWS Marketplace listing, they can choose different versions\. When your buyers launch your product from the Amazon SageMaker console, only the latest version is visible\. 

### Restricting versions<a name="ml-restricting-versions"></a>

**To restrict versions of your model package or algorithm resources**

1. Navigate to the **Product Overview** of your existing product\.

1. Choose **Edit product**\. 

1. Under **Launch option**, choose **Edit**\. 

1. On the **Version** page, choose **Restrict version**\. 

1. Return to the **Product Overview**, and choose **Submit for publishing**\. 

**Note**  
Buyers that have already subscribed to your product can continue to use restricted versions of your model package or algorithm\. However, new buyers will not be able to see those restricted versions as options\. 

### Removing a product<a name="ml-remove-or-delist-a-product"></a>

**To remove a product**

1. Navigate to your list of published products in the [Machine Learning Listings](http://aws.amazon.com/marketplace/management/ml-products) page in the AWS Marketplace Management Portal\. 

1. Choose the product you want to remove, and in the **Actions** dropdown list, choose **Unpublish listing**\. 

1. Provide an email address and a reason to remove your listing, in the event that an AWS Marketplace representative contacts you regarding your request\. 

**Note**  
When you remove a product from AWS Marketplace, new buyers can no longer subscribe to your product\. However, existing buyers can continue using your product, which must be supported for a minimum of 90 days\. If you plan to have another product replace the unpublished listing, indicate the new listing in the details of your removal request\. 