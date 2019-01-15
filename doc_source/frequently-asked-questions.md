# Frequently Asked Questions<a name="frequently-asked-questions"></a>

## What is the customer experience for using AWS Marketplace for Containers?<a name="what-is-the-customer-experience-for-using-aws-marketplace-for-containers"></a>

 Customers visiting the Amazon ECS pages in the AWS Management Console can browse and search available container products using an AWS Marketplace link in the navigation pane\. Customers also search products from the AWS Marketplace website using the **Container** filter under **Delivery Method**\. Selecting a product brings the customer to the product page on the AWS Marketplace website, where they can see full details, including pricing information\. The customer can choose public terms or a private offer and subscribe to the product\. If the seller has provided a deployment template such as a task definition or Helm chart, the customer can use it to deploy and launch the product using an orchestration service such as Amazon ECS or Amazon EKS\. After subscribing, customers can see a list of their container products by using a link in the Amazon ECS console that directs them to the **Your Software** page of the AWS Marketplace website\. 

## How do I extend an existing product to use AWS Marketplace for Containers?<a name="how-do-i-extend-an-existing-product-to-use-aws-marketplace-for-containers"></a>

If you have existing AMI\-based software products and you want to offer an equivalent container\-based offering, you need to create a separate product listing and submit the relevant metadata and the container images\. You do this using a Microsoft Excel–based PLF\. A later release will have a web\-based self\-service listing experience for creating and editing container products\. To modify your product to run as a set of containers, you need to ensure that it can run as a stateless instance in a virtualized operating system\. AWS Marketplace partner solutions architects might review your container applications to ensure that they meet best practices\.

## Why do I have to write code to verify entitlement for paid container products but not AMI products?<a name="why-do-i-have-to-write-code-to-verify-entitlement-for-paid-container-products-but-not-ami-products"></a>

 AWS Marketplace uses capabilities and metadata built into the AMIs to verify entitlement and enforce launch control\. However, Docker container images are an open, portable format that doesn't provide the same mechanisms\. The `RegisterUsage` operation allows sellers to verify that only subscribed and paying customers are running their container images, and that they are being run only on supported AWS runtimes\. Requiring this check for paid products also helps customers by protecting them from accidental unlicensed use of the software\. 

## Can I include multiple container images in my product listing?<a name="can-i-include-multiple-container-images-in-my-product-listing"></a>

 Yes\. A product can have different container images as separate fulfillment options if they're configured for different deployment scenarios\. You can also have up to 50 container images in a single fulfillment option, with one or more task definitions specifying how the containers are deployed\. However, customers might choose to reconfigure your task definitions or create their own\. You can have up to four fulfillment options in a single container product\. 

## If I want to list a container product, do I have to list an AMI\-based equivalent, too?<a name="if-i-want-to-list-a-container-product-do-i-have-to-list-an-ami-based-equivalent-too"></a>

 No, you don't have to list an AMI if you provide one or more container images and the required product metadata and optional pricing information\. 

## What are the AWS Marketplace listing fees for container products?<a name="what-will-be-the-aws-marketplace-listing-fees-for-container-products"></a>

 AWS Marketplace listing fees are the same as for other server products such as AMI\-based products\. 

## What kind of reports will I get on my container\-based software?<a name="what-kind-of-reports-will-i-get-on-my-container-based-software"></a>

 AWS Marketplace will send similar reports as for AMI\-based software that show usage and revenue for any paid container\-based fulfillment options that you have enabled for your products\. If you want to get reports for BYOL or free products running on Amazon ECS, you need to add code that calls the AWS Marketplace Metering Service to ensure that their usage is tracked\. 