# Pricing Container Products<a name="pricing-container-products"></a>

 You can offer free, BYOL, and paid products\. This section helps you understand the available pricing models\. AWS infrastructure costs for your product usage, such as for Amazon EC2, Amazon EKS, or Amazon Fargate, are independent of the software usage costs that you specify\. 

## Pricing Models for Server Products<a name="pricing-models-for-server-products"></a>

 As with AMI\-based products, you can choose from different licensing and pricing options for your container products on AWS Marketplace\. We support free products, BYOL products, and paid products\. Paid products support the following pricing models: 
+  A fixed monthly price that provides users with unlimited product usage during the following month\. 
+  Usage\-based pricing that is billed per second, and set per hour, per task for Amazon ECS, or per pod for Amazon EKS\. 

### Example 1: Fixed Monthly Price<a name="example-1-fixed-monthly-price"></a>

 You set the price for your product at $99 per month\. Your product includes three different container images that are deployed using an Amazon ECS task definition or Amazon EKS pod configuration\. After a customer subscribes to your product, they're immediately charged $99, which repeats each month until they cancel the subscription\. During that time, the customer can access your container images\. They can launch and run any number of containers from those images on Amazon ECS or Amazon EKS in any configuration\. If the customer cancels their subscription in the middle of a month, they lose access to the Amazon ECR repository where AWS Marketplace stores the container images\. Customers might have pulled and stored the original images, but they can no longer pull new container image versions that you make available through AWS Marketplace\. The customer is refunded for the unused portion of the final month, and you're paid based on the customer's usage minus the agreed\-to AWS Marketplace fee\. 

### Example 2: Usage\-Based Hourly Price<a name="example-2-usage-based-hourly-price"></a>

 Your product includes three different container images: a controller node, a worker node, and an analytics node\. Because your product isn't functional or useful without the controller node, you decide that is the image that you want to charge usage for\. You set a price of $6 per hour\. You modify the software in the container image for the controller node to integrate with the [AWS Marketplace Metering Service API](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html)\. This ensures that only customers with an active subscription can launch and run that container image and that its usage is metered based on how long it runs\. The customer is charged $6 per hour of usage for each Amazon ECS task or Amazon EKS pod running\. For example, if the customer launches five Amazon ECS tasks or Amazon EKS pods that include the controller node container, they're charged $30 per hour \($6 per task or per pod\)\. The customer also pays separately for any infrastructure that the tasks run on\. 

 For hourly pricing, billing is per\-second with a 1\-minute minimum\. For example, if the customer runs this controller container for 20 minutes and 30 seconds, they're charged 20 x \($6/60\) \+ 30 x \($6/60/60\) = $2 \+ $0\.05 = $2\.05\. 

## Pricing for SaaS Products<a name="pricing-for-saas-products"></a>

 SaaS pricing is the same as offered on AWS Marketplace\. You should offer container\-based agents that you list for use with your SaaS products as free container products\. 