# Listing Algorithms and Model Packages in AWS Marketplace for Machine Learning<a name="listing-algorithms-and-model-packages-in-aws-marketplace-for-machine-learning"></a>

 To distribute your products to AWS customers using AWS Marketplace, you perform three steps\. 

1.  Package your code\. 

1.  Create and algorithm or model package in Amazon SageMaker\. 

1.  List and monetize your product\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/ml-product-find-subscribe-deploy-process.png)

 Amazon SageMaker builds and maintains the containers for the first and second use cases\. For the third use case, Amazon SageMaker lets customers package their own code, which can be written in any language with any dependencies, into a Docker image\. These Docker images allow customers to run their code anywhere without relying on the underlying hosting system\. 

## Listing Your Algorithm or Model Package in AWS Marketplace<a name="listing-your-algorithm-or-model-package-in-aws-marketplace"></a>

 After creating and validating your algorithm or model package in Amazon SageMaker, you list your product\. The listing process makes your products available in the AWS Marketplace and the Amazon SageMaker console\. 

**Note**  
To list products on AWS Marketplace, you must be a registered seller\. If you have not registered, review [Getting Started as a Seller](https://docs.aws.amazon.com/marketplace/latest/userguide/user-guide-for-sellers.html) and complete the registration process\. 

 To start the listing process, do one of the following: 
+  From the Amazon SageMaker console, choose the product, choose **Actions**, and choose **Publish new AWS Marketplace listing**\. This carries over your product reference, the Amazon Resource Name \(ARN\), and directs you to the AMMP to create the listing\. 
+  Navigate to [ML listing process](https://aws.amazon.com/marketplace/management/ml-products/), manually enter the \(ARN, and start listing your product\. This process carries over the product metadata that you entered when you created the product in Amazon SageMaker\. This information includes the training specification, supported instance types, hyperparameters, inference and channel information, input data type, and sample data\. 

 When listing a product on AWS Marketplace, you provide the following: 
+  General product information 
+  Launch option 
+  Pricing and terms 

 **General Product Information** 

 Enter the product description, promotional resources, support information, and region availability\. This information will appear on the AWS Marketplace product detail page\. It is searchable in AWS Marketplace\. 

 **Launch Option** 

 Define general usage information, a customer\-facing version number, and release notes\. Review the Amazon SageMaker metadata, such as Amazon SageMaker content types, MIME types, supported input methods, and hyperparameters\. 

 **Pricing and Terms** 

 Define a EULA, pricing, the product tax code, and the refund policy\. When you list a paid \(not free trial\) algorithm, you can enter a training price for the algorithm and real\-time and batch inference prices for the inference image packaged with the algorithm\. When you list a model package, you can define real\-time and batch inference prices for the package\. 

 For both algorithms and model packages, you can define prices for each supported instance type per hour\. You can also list a free\-trial algorithm by specifying the number of free days\. 

 **Product Publishing** 

 After entering the product information, you can publish you product\. This involves publishing the metadata to multiple systems and copying your algorithm or model package to different AWS Regions\. 

 Publishing can take 30–60 minutes\. If you try to access the AWS Marketplace product detail page during the publishing process, you might get a 404 error\. This is expected while the information propagates through multiple systems\. 

 After the publishing process has finished, review the product detail page to ensure that all of the product information is rendered correctly\. At this stage, only you can see your product listing\. After you verify that the product information is correct, sign off on your product to make it available to buyers on AWS Marketplace\. 

## Monetizing Your Algorithm or Model Package<a name="monetizing-your-algorithm-or-model-package"></a>

 For algorithms and model packages, AWS Marketplace has an hourly pricing model per instance type\. Algorithms have two prices: training price and inference price\. Model packages have only an inference price\. Amazon SageMaker supports real\-time and batch inference modes, and you can set different prices for each mode\. Buyer usage is metered and billed in one\-second increments\. Currently, you can list only paid products and free\-trial products only\. 

**Important**  
 You will not receive disbursements during the preview period\. All algorithm and model package charges will be refunded to buyers\. At general availability, you will start receiving monthly disbursements\. 