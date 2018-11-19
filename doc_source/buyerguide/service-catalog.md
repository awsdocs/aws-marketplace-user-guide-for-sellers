# Adding AWS Marketplace Subscriptions to AWS Service Catalog<a name="service-catalog"></a>

 AWS Service Catalog allows organizations to create and manage catalogs of IT services that are approved for use on AWS\. These IT services can include everything from virtual machine images, servers, software, and databases to complete multi\-tier application architectures\. AWS Service Catalog allows you to centrally manage commonly deployed IT services, and helps you achieve consistent governance and meet your compliance requirements, while enabling users to quickly deploy only the approved IT services they need\. 

## Frequently Asked Questions<a name="buyer-service-catalog-frequently-asked-questions"></a>

### What does it mean to copy AWS Marketplace products to AWS Service Catalog?<a name="what-does-it-mean-to-copy-aws-marketplace-products-to-service-catalog"></a>

You can copy AWS Marketplace software products into AWS Service Catalog from the AWS Marketplace website\. Currently, only select products that are delivered as Amazon Machine Images \(AMIs\) or as AWS CloudFormation stacks can be copied\. If a product is available to copy, a **Service Catalog** view appears on the product’s launch page\. You must first accept the software terms and subscribe to the product before you can copy it to AWS Service Catalog\. When you choose **Service Catalog**, you can select the version or versions of the product to copy and the AWS Service Catalog Region into which it should be copied\. You can create as many copies of each product version in your catalog as you want, even if they are identical to existing entries\. This gives you flexibility when managing AWS Marketplace products in your catalog\. You can then access, manage, and launch your products from AWS Service Catalog, or further customize them by editing their AWS CloudFormation template\. You will be charged for any instances you launch from within AWS Service Catalog just as if you launched them from the AWS Marketplace website or Amazon EC2 console\. You can also add the products to a new or existing AWS Service Catalog portfolio\. For more information, see [AWS Service Catalog](https://aws.amazon.com/servicecatalog/)\.

### What are the steps to copy a product to AWS Service Catalog?<a name="what-are-the-steps-to-copy-a-product-to-service-catalog"></a>

1.  Visit the product launch page for the AWS Marketplace product you want to copy\. For a product to which you have already subscribed, you can find this page by choosing **Launch More Software** for that product on the [Your Software](https://aws.amazon.com/marketplace/library) page\. For a product to which you have not yet subscribed, browse to the product detail page and then choose **Continue**\. You might need to sign in to AWS Marketplace if you have not already done so\. 

1.  From the launch page of the product you want to add to AWS Service Catalog, choose **Service Catalog**\. If there is no **Service Catalog** view, then the product cannot be copied to AWS Service Catalog\. 

1.  Under **Copy to Service Catalog**, for **Service Catalog Region**, choose the Region into which you want to copy the product\. 

1.  Select the version or versions of the product you want to copy, and then choose **Copy to Service Catalog**\. A message appears, indicating that the product is being copied to the Region you selected\. 

1.  This message appears after the product has been copied and for any product version that has been previously copied: 

### Is there a charge for copying items from AWS Marketplace into my catalog?<a name="is-there-a-charge-for-copying-items-from-aws-marketplace-into-my-catalog"></a>

 There is no additional charge for copying products from AWS Marketplace to AWS Service Catalog\. Each AWS Marketplace product has its own pricing model for the usage of the product software\. For more information on AWS Service Catalog pricing, see [AWS Service Catalog pricing](https://aws.amazon.com/servicecatalog/pricing/)\.

### Why is the Copy to Service Catalog button dimmed?<a name="why-is-my-copy-to-service-catalog-button-grayed-out"></a>

 The button is dimmed until you accept the software license terms for the product\. The button might also be dimmed if you do not have permissions to use AWS Service Catalog\. 

### Do I need specific permissions to use this service?<a name="do-i-need-specific-permissions-to-use-this-service"></a>

 Yes\. You must have an account that can read and write to AWS Service Catalog\. 

### Can I customize the AWS CloudFormation template before copying a product to AWS Service Catalog?<a name="can-i-customize-the-cloudformation-template-before-copying-a-product-to-service-catalog"></a>

 No\. However, you can create a new AWS CloudFormation template that references the AWS Marketplace AMI or use the template copied to AWS Service Catalog as a starting point to create a new version\. For more information, see [Adding an AWS Marketplace Product to Your Portfolio](http://docs.aws.amazon.com/servicecatalog/latest/adminguide/catalogs_marketplace-products.html)\.

### Why doesn’t the pricing information reflect the costs of the Region to which I am copying the product?<a name="why-doesnt-the-pricing-information-reflect-the-costs-of-the-region-to-which-i-am-copying-the-product"></a>

 The **Version** and **Region** dropdowns in the **Copy to Service Catalog** section are used only to select the product version and the AWS Service Catalog Region where you want the product copied\. To see how launching a product in a specific Region might change the costs of Amazon EC2 or other infrastructure, use the **Region** dropdown in the **Pricing Information** section\. 

### Can I make multiple entries of the same product in the same Region?<a name="can-i-make-multiple-entries-of-the-same-product-in-the-same-region"></a>

 Yes\. Each time you choose **Copy to Service Catalog**, a new entry will be made\. 

### Can I copy more than one version of a product at a time?<a name="can-i-copy-more-than-one-version-of-a-product-at-a-time"></a>

 Yes\. You can choose to copy one or more versions of the product at a time\. Every time you choose **Copy to Service Catalog**, a new copy of the product is created in AWS Service Catalog\. Existing AWS Service Catalog products and previously made product copies will not be altered\. 

### Can I copy the product to more than one Region at a time?<a name="can-i-copy-the-product-to-more-than-one-region-at-a-time"></a>

 No\. When you use this feature to add products to AWS Service Catalog, you can copy to only one Region at a time\. 

### Can I remove copies from AWS Service Catalog?<a name="can-i-remove-copies-from-service-catalog"></a>

 Yes\. You can use the AWS Service Catalog console, CLI, or APIs to remove products copied to AWS Service Catalog\. 

### Is Copy Products to AWS Service Catalog available for the AWS GovCloud \(US\) Region?<a name="is-copy-products-to-aws-service-catalog-available-for-the-aws-govcloud-region"></a>

 No, not at this time\. 