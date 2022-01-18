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

**To create a machine learning product**

1.  While logged into your seller AWS account, navigate to the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management)\. 

1.  In the top menu, navigate to **Products** and then **Machine learning**\. 

1.  Choose **Create new listing**\. 

After you have created your listing, you must provide general product information, set up the launch option for the first version of your product, set up the pricing for your product, and finally submit the product\. The following procedures take you through each of these steps\.

**Step 1: To provide general product information**

1. Choose **Add** for **Product descriptions**\. 

   1. For the **Product visibility** section, choose one of the following options:
      + **Public** – The product will initially be available to a limited set of AWS accounts for testing\. After you sign off and publish it, the product will be publicly discoverable and available for subscription by all customers\. 
      + **Private** – The product will only be visible to the AWS accounts that you specify\. You will not be able to make this product public in the future\.

   1. Enter **Product title**, **Short product description**, **Product overview**,** Product category 1**, and other details\. For product descriptions, see [Requirements and best practices for creating machine learning products](ml-listing-requirements-and-best-practices.md)\. 

   1. Choose **Continue** when complete\. You can change these values later\. 

1. Continue to **Promotional Resources**, and provide a product logo and relevant links\. Choose **Continue** when complete\. You can change these values later\. 

1. Continue to **Support Information**, provide support and contact details\. Choose **Continue** when complete\. You can change these values later\.

1. Continue to **Region Availability**, and choose the specific AWS Regions you want to list your product in\. The default value is **Make available in all current and future supported Regions**\. Choose **Continue** when complete\. After you submit your draft for publishing, you can't change this selection\. 

Next, you're ready to provide the launch option, which is the model or algorithm that you're selling\.

**Step 2: To add your launch option**

1. For **Enter ARN**, paste the Amazon Resource Name \(ARN\) of your model package or algorithm\. You can find these in the Amazon SageMaker console [Model Packages](https://us-east-2.console.aws.amazon.com/sagemaker/home?region=us-east-2#/model-packages/my-resources) or [Algorithms](https://us-east-2.console.aws.amazon.com/sagemaker/home?region=us-east-2#/algorithms/my-resources) pages\. 

   1. An ARN for a model package appears as the following: `arn:aws:sagemaker:<region>:<account-id>:model-package/<model-package-name>` 

   1. An ARN for an algorithm appears as the following: `arn:aws:sagemaker:<region>:<account-id>:algorithm/<algorithm-name>` 

1. Choose **Add**\. 

1. This step differs depending on if you publish a model package or algorithm product\. With the exception of the buyer\-facing version number, you can change the version details later\. 

   1.  Provide the version number, release notes, and URLs to the sample Jupyter notebook and GitHub repository\. 

   1. For *algorithm products* only, on the next page, describe the training data and include an example training data resource along with an overview of the training algorithm\. The algorithm metrics, channel specification, and hyperparameters will be automatically displayed on the product detail page based on the values you provided when you created the algorithm resource in SageMaker\.

   1.  On the next page, provide model input details and URLs for the sample input files\. 

   1.  On the next page, provide the model output details and sample outputs as text or URLs\. For usage information, see [Requirements and best practices for creating machine learning products](ml-listing-requirements-and-best-practices.md)\.

   1. On the next page, set the recommended instances\. If this is a model package product, choose the recommended instance type from your supported instances for both the batch transform and real\-time deployments\. If this is an algorithm product, choose the recommended instance type training jobs, as well\. You can't choose instance types that your model package or algorithm resource doesn't support\. The supported instance types were selected when you created those resources in Amazon SageMaker\.

1.  Choose **Continue** when complete\. 

**Note**  
 Clear usage information that describes the expected inputs and outputs of your product \(with examples\) is crucial for supporting a positive buyer experience\. For more information, see [Requirements and best practices for creating machine learning products](ml-listing-requirements-and-best-practices.md)\. 

The next step in publishing your product is to set the pricing and terms\.

**Step 3: To set the pricing and terms**

1.  Choose **Add offer**\. 

1.  Set your **Pricing**\. You can provide your software for free, set your paid pricing, or enable a free trial period\. For more information, see [Machine learning product pricing](machine-learning-pricing.md)\. 

1.  Upload a plaintext file to use as your End User License Agreement \(EULA\)\. 

1. Choose **Save and close**\. 

 You have provided all the information for your product\. The next step is to publish it to limited availability so that you can test the product\.

**Step 5: To submit your product for publishing**
+  For **Product overview**, choose **Submit for publishing**\. This starts the publishing process by creating a preview listing in AWS Marketplace that you can subscribe to and use for testing\. 

**Note**  
For more information about testing your machine learning product, see [Testing your product](#ml-testing-your-product)\.

After testing your product, you can redo the steps above if there are any changes that need to be made\. When you're ready for your product to be available to buyers in AWS Data Exchange, you can sign off for publishing\.

**Step 4: To sign off for publishing**
+  After testing your product and writing your descriptions, pricing, and usage information, return to the product overview, and choose **Sign off and publish**\. 

## Testing your product<a name="ml-testing-your-product"></a>

After the initial submission of your product, it takes about an hour for your preview listing to be ready\. After the status changes to **Test Product**, your seller account and other allow\-listed AWS accounts can preview the listing in AWS Marketplace, subscribe to the product, and test it\. To see a preview of your listing, in the AWS Marketplace Management Portal, navigate to the product overview page, and choose **Go to staged product**\. 

 To add other AWS accounts to test your product before publishing, contact [AWS Marketplace Seller Operations](http://aws.amazon.com/marketplace/management/contact-us) and provide the AWS account IDs\. Allow\-listed accounts display a **Limited** badge alongside the product version on the product detail page\. 

If you want to make changes, choose **Edit product** and follow the same steps as creating your product\. When you're ready for your product to be published publicly for all buyers to see, return to the management portal, and choose **Sign off and publish**\. 

## Updating your product<a name="ml-updating-your-product"></a>

To update your model package or algorithm product, navigate to the [Machine Learning Listings](http://aws.amazon.com/marketplace/management/ml-products) page in the AWS Marketplace Management Portal\. You can add new model package or algorithm resources as new versions of your existing product\. You can also restrict previous versions or remove your entire product\. 

### Adding new versions<a name="ml-adding-new-versions"></a>

To add new versions of your model package or algorithm resources, navigate to the **Product Overview** of your existing product, and then use the follow procedure\. 

**To add a new version**

1.  Choose **Edit product**\. 

1. Under **Launch option**, choose **Edit**\. 

1. To add the ARN of your resource, navigate to the **Version** page, and choose **Add new version**\. For more information about adding a launch option, see [Creating your product listing](#ml-creating-your-listing)\. 

**Note**  
Usage information is specific to each product version\. Continue to follow the [Requirements and best practices for creating machine learning products](ml-listing-requirements-and-best-practices.md) when adding usage information to new versions\. 

When your buyers launch your product from its AWS Marketplace listing, they can choose different versions\. When your buyers launch your product from the Amazon SageMaker console, only the latest version is visible\. 

### Restricting versions<a name="ml-restricting-versions"></a>

To restrict versions of your model package or algorithm resources, navigate to the **Product Overview** page of your existing product, and then use the following procedure\.

**To restrict a version**

1. Choose **Edit product**\. 

1. Under **Launch option**, choose **Edit**\. 

1. On the **Version** page, choose **Restrict version**\. 

1. Return to the **Product Overview**, and choose **Submit for publishing**\. 

**Note**  
Buyers that have already subscribed to your product can continue to use restricted versions of your model package or algorithm\. However, new buyers will not be able to see those restricted versions as options\. 

### Remove a product<a name="ml-remove-or-delist-a-product"></a>

To remove a product, navigate to your list of published products in the [Machine Learning Listings](http://aws.amazon.com/marketplace/management/ml-products) page in the AWS Marketplace Management Portal\. Choose the product you want to remove, and in the **Actions** dropdown list, choose **Unpublish listing**\. 

Provide an email address and a reason to remove your listing, in the event that an AWS Marketplace representative contacts you regarding your request\. 

**Note**  
When you remove a product from AWS Marketplace, new buyers can no longer subscribe to your product\. However, existing buyers can continue using your product, which must be supported for a minimum of 90 days\. If you plan to have another product replace the unpublished listing, indicate the new listing in the details of your removal request\. 