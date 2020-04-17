# Pricing container products<a name="pricing-container-products"></a>

This section outlines the available pricing models for container products\. You can list free products, bring\-your\-own\-license \(BYOL\) products, and paid products for Amazon ECS, Amazon EKS, and Fargate\. You can set only one price per product\.

**Note**  
You use the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) to enforce entitlement and meter usage for your paid products\. For per task or per pod pricing, usage is metered automatically by AWS\.

The price you set for a container product applies to all AWS Regions\. Whenever you lower the price for a container product, the new price is implemented for your buyers immediately\. For price increases, existing buyers are notified about the change 90 days before it impacts their billing\. New buyers are billed the new amount\.

## Pricing models for container products<a name="pricing-models-for-server-products"></a>

Paid container products support the following pricing models:
+ Custom metered prices based off of dimensions you define \(for example users, nodes, repositories, GB, etc\.\), up to 24 dimensions per product\.
+ A long term contract, at a reduced price, paid up front or in regular installments\. A long term contract can be added to an existing product that has custom metered pricing, or per task / per pod pricing\. Buyers pay the metered prices when they consume more than what they purchased in the long term contract\.
+ A fixed monthly price that provides users with unlimited product usage during the following month\. 
+ Per Amazon ECS task or Amazon EKS pod pricing that we measure to the second with the price set per hour\.
+ BYOL pricing, which is managed outside of AWS Marketplace through an external billing relationship you maintain with the buyer\.

**Example Fixed monthly price**  
You set the price for your product at $99 per month\. Your product includes three different container images that are deployed using an Amazon ECS task definition\.  
After a buyer subscribes to your product, they're immediately charged $99, which repeats each month until they cancel the subscription\. The buyer also gets unlimited usage of the product\. The buyer also pays separately for any infrastructure that the tasks run on\. While subscribed, they can access your container images\. They can launch and run any number of containers from those images on Amazon ECS or Amazon EKS in any configuration\.  
If the buyer cancels their subscription in the middle of a month, they lose access to the Amazon ECR repository where AWS Marketplace stores the container images\. The buyer might have pulled and stored the original images, but they can no longer pull new container image versions that you make available through AWS Marketplace\. The buyer is refunded for the unused portion of the final month, and you're paid based on the buyer's usage minus the agreed\-to AWS Marketplace fee\.

**Example Custom metric pricing dimensions**  
Your product charges by users\. You have admin users and regular users and you define the pricing as $2 for admin users and $1 for regular users\. You can set them up as separate dimensions when listing your product\. You charge by users logged in per day and you meter that usage per day\.

**Example Per task or per pod hourly price**  
Your product includes three different container images: a controller node, a worker node, and an analytics node\. Because your product isn't functional or useful without the controller node, you decide that is the image that you want to charge usage for\. You set a price of $6 per hour\.  
You modify the software in the container image for the controller node to integrate with the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html)'s `RegisterUsage` operation\. This ensures that only buyers with an active subscription can launch and run that container image and that its usage is metered based on how long it runs\.  
The buyer is charged $6 per hour of usage for each Amazon EKS controller pod running\. If the buyer launches five Amazon EKS controller pods that include the controller node container, they're charged $30 per hour \($6 per pod\)\. The buyer also pays separately for any infrastructure that the pods run on\.  
For hourly pricing, billing is per\-second with a 1\-minute minimum\. If the customer runs this controller container for 20 minutes and 30 seconds, they're charged `20 x ($6/60) + 30 x ($6/60/60) = $2 + $0.05 = $2.05`\. You're paid based on the buyer's usage minus the agreed\-to AWS Marketplace fee\.

**Example Long term contracts**  
For metered pricing models, you can add a long term contract price for buyers to get a discount for committing upfront\. Say that the buyer commits to pay for regular users upfront for a one year contract, and the price drops from $1 per user to $0\.5 per user\.  
For the per task / per pod example, you can drop the price from $6 per pod to $3 per pod if they commit upfront to running those pods for a year\.  
In both cases, buyers that purchase long term contracts will be billed upfront, either as a one\-time payment or regularly scheduled future payments\. Buyers will also be billed for any additional usage above their contract at the metered rate\. 