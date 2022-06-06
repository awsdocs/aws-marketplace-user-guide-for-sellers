# AMI\-based products<a name="ami-products"></a>

One way of delivering your products to buyers is with [Amazon Machine Images \(AMIs\)](https://docs.aws.amazon.com/general/latest/gr/glos-chap.html#AmazonMachineImage)\. An AMI provides the information required to launch an Amazon Elastic Compute Cloud \(Amazon EC2\) instance\. You create a custom AMI for your product, and buyers can use it to create EC2 instances with your product already installed and ready to use\.

When buyers use the AMI that you provide, they're billed for instances that they create, following the pricing and metering options that you create for your product\. Buyers can use your product AMI in the same way that they use other AMIs in AWS, including making new custom versions of the AMI\. EC2 instances created from the AMI are still billed as your product, based on the AMI product code\.

See the following resources:
+ For more information about pricing AWS Marketplace products, see [Product pricing](pricing.md)\.
+ For more information about creating custom metering for your product, see [Custom metering for AMI products with AWS Marketplace Metering Service](custom-metering-with-mp-metering-service.md)\.

## AMI\-based product delivery methods<a name="ami-product-delivery-methods"></a>

You can deliver your AMI\-based product in one of three ways:
+ **Single AMI** – Buyers select and use the AMI as a template for an EC2 instance\. Buyers can find these products using the **Amazon Machine Image** delivery method filter\. 

  For more information, see [Single\-AMI products](ami-single-ami-products.md)\.
+ **AWS CloudFormation templates** – You create templates that allow buyers to install a system of multiple instances with different roles as a single unit\. Buyers can find these products using the **CloudFormation** delivery method filter\. 

  For more information, see [AMI\-based delivery using AWS CloudFormation](cloudformation.md)\.
+ **Private image build** – This approach allows buyers to install your product on a base gold image that meets their internal needs for operating system configuration\. They create a new AMI, with your product code for tracking and billing\. Buyers can find these products using the **Private Amazon Machine Image** delivery method filter\.

  For more information, see [Private images](private-images.md)\.

See the following resources:
+ For more information about how your AMIs are tracked as buyers use them, see [AMI product codes](ami-getting-started.md#ami-product-codes)\.
+ For more information about the details of AMI\-based products, and their lifecycle, see [Understanding AMI\-based products](ami-getting-started.md)\.