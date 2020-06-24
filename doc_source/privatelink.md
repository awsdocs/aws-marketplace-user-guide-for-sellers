# Using AWS PrivateLink with AWS Marketplace<a name="privatelink"></a>

AWS Marketplace supports AWS PrivateLink, a technology that allows you to use the Amazon network to provide buyers with access to products you sell through AWS Marketplace\. This document outlines the process for configuring and delivering your products through an Amazon Virtual Private Cloud \(VPC\) endpoint using AWS PrivateLink technology\. 

 In this document, we assume that you have working knowledge of several AWS services and the AWS Marketplace environment\. 

## Introduction<a name="introduction"></a>

 As an AWS Marketplace seller, you can provide buyers access to your service through an Amazon VPC endpoint\. This approach provides buyers with access to your service across the Amazon network using [AWS PrivateLink](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Introduction.html#what-is-privatelink) technology\. If you use AWS Marketplace to create and deliver this offering, buyers can discover your service in AWS Marketplace\. Your buyers can also find your product in the list of available services for creating a VPC endpoint\. 

 ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/private-endpoint-diagram.png) 

A [VPC endpoint](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-endpoints.html) is a virtual device that enables AWS customers to create a private connection between their VPC and another AWS service without requiring access over the internet, through a NAT device, a VPN connection, or AWS Direct Connect\. You can create an endpoint service through AWS Marketplace that makes it possible for buyers to use this technology to connect to your service\. This connection method is more secure for your buyers because they access your service through the Amazon private network rather than through the Internet\. 

For each region where you want to offer your service, you create or use existing resources to configure a VPC, set up your service instances, set up a network load balancer, and register your services with the network load balancer by creating a service endpoint\. After you complete those steps and test your offering, you provide your configuration information to the the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

AWS recommends that provide a private DNS name that your buyers can use when they create VPC endpoints\. 

 When buyers create their VPC endpoints, they have the option to enable a private DNS name\. By choosing this option, the buyer’s VPC service configures a [private hosted zone](http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-private.html)\. If you provide the private DNS name, buyers can use it when configuring VPC endpoints to connect to your service\. In the buyer’s private hosted zone, the private DNS name \(api\.example\.com\) will point to the randomly generated DNS name\(s\) \(vpce\-11111111111111111\-yyyyyyyy\.api\.vpce\.example\.com\) created for your endpoint service\(s\)\. The buyer's EC2 instances call the same unified DNS name \(api\.example\.com\) across different VPCs\. Also, if public and private DNS names are same, the buyer can use the same public name when accessing your service from within or outside of the VPC\. 

For assistance with making your service available through AWS Marketplace, you can contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. When an AWS Marketplace buyer subscribes to your service and creates a VPC endpoint, your service is shown under **Your AWS Marketplace Services**\. The MCO team uses the user\-friendly DNS name for ease of discovery of your service when creating the VPC endpoint\. 

Your product is created as a software as a service \(SaaS\) product\. Metering and billing is the same as with other AWS Marketplace SaaS products\. 

## Configuring your product<a name="configuring-your-product"></a>

To configure your product to be available through an Amazon VPC endpoint: 

1. Create or use an existing [Amazon VPC](https://aws.amazon.com/documentation/vpc/)\. 

1. Create \(or use existing\) [Amazon EC2](https://aws.amazon.com/documentation/ec2/) instance\(s\) for your product\. 

1. Create a [network load balancer](http://docs.aws.amazon.com/elasticloadbalancing/latest/network/network-load-balancer-getting-started.html) in each of the regions where you offer your product\. AWS recommends that you include all [Availability Zones](http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/enable-disable-az.html) \(AZs\) for a region\. 

1. Use the Amazon VPC console, the CLI, or supported SDKs to create a VPC endpoint service\. 

1. Verify that you can access the service through the network load balancer\. 

1. [Request a certificate from AWS Certificate Manager \(ACM\)](http://docs.aws.amazon.com/acm/latest/userguide/gs-acm-request.html) for your user\-friendly DNS name\. Before ACM issues a certificate, it validates that you own or control the domain names in your certificate request\. 

1. Delegate the subdomain of your user\-friendly DNS name, such as api\.vpce\.example\.com, to the name servers provided to you by the MCO team\. In your DNS system, you must create a name server \(NS\) resource record to point this subdomain to the Amazon Route 53 name servers provided by the MCO team so that DNS names \(such as vpce\-0ac6c347a78c90f8\.api\.vpce\.example\.com\) are publicly resolvable\. 

1. Allow access to your buyers' AWS accounts\. 

    **Note**: You can use a supported SDK or this CLI command to automate access to accounts: aws vpcev2 modify\-vpc\-endpoint\-service\-permissions \-\-service\-id vpce\-svc\-0123456789abcdef1 \-\-add\-allowed\-principals arn:aws:iam::111111111111:root arn:aws:iam::222222222222:root\. 

## Submitting your product to AWS Marketplace<a name="submitting-your-product-to-aws-marketplace"></a>

During the process of publishing your service to AWS Marketplace, you work with the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. To submit your PrivateLink\-enabled product: 

1. Email the following information to the [AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/) team: 

   1. The endpoint and the AWS account used to create the endpoint\. The endpoint is similar to this: com\.amazonaws\.vpce\.us\-east\-1\.vpce\-svc\-0daa010345a21646 

   1. The user\-friendly DNS name for your service\. This is the DNS name that AWS Marketplace buyers use to access your product\.

   1. The AWS account that you used to request certificates and the private DNS name buyers use to access the VPC endpoint\. 

      The AWS Marketplace MCO team verifies your company’s identity and the DNS name to use for the service you are registering \(such as api\.vpce\.example\.com\)\. After verification, the DNS name overrides the default base endpoint DNS name\. 

## Buyer access to VPC endpoints<a name="customer-access-to-vpc-endpoints"></a>

AWS Marketplace buyers who are creating a VPC endpoint can discover your service in these situations: 
+ You followed the seller processes described earlier on this page to create or use an existing product\. 
+ The buyer subscribes to your service\. 
+ You added the buyer's AWS account to your list of allowed accounts\. 

When the buyer creates the VPC endpoint, they have the option to associate a private hosted zone with their VPC\. The hosted zone contains a record set for the default private DNS name for the service that resolves to the private IP address of the endpoint network interfaces in their VPC\. 

Any buyer\-hosted endpoint, including AWS Marketplace services, can provide permissions to all accounts \(the "\*" permission\)\. However, when you use this approach, the services aren't included in the **Describe** calls or console unless you search by the service name\. To display the services in the **Describe** calls, the buyer's AWS account must be explicitly added to the allow list by the service\. 

To access your service, buyers do the following: 

1. Discover and subscribe to your service on AWS Marketplace\. 

1. Use the AWS Command Line Interface \(AWS CLI\), API, or the Amazon VPC console to discover your service and then establish a VPC endpoint to connect to your service in the subnets and AZs they use\. The endpoints are shown as elastic network interfaces in the subnets\. Local IP addresses and region and zonal DNS names are assigned to the endpoints\. 


|  **Client\-side DNS name**  |  **Name**  | 
| --- | --- | 
|  Regional   |  Vpce<0dc9a211a78c90f8>\.api\.vpce\.example\.com   | 
|  IAD2 \(1a \)   |   **us\-east\-1a**\-Vpce<0dc9a211a78c90f8>\.api\.vpce\.example\.com   | 
|  IAD2 \(1b \)   |   **us\-east\-1b**\-Vpce<0dc9a211a78c90f8>\.api\.vpce\.example\.com   | 

If you provided a default private DNS name and the buyer chooses **Enable Private DNS Name** \(associated a private hosted zone\) when creating a VPC endpoint, the buyer sees the regional default private DNS name to onnect to your service\. 


|  **Name**  |  **Alias**  |  **Alias hosted zone ID**  |  **\(Notes\)**  | 
| --- | --- | --- | --- | 
| api\.example\.com  | vpce<0dc9a211a78c90f8>\. api\.vpce\.example\.com  | Z00AABBCCDD  |  IAD1  IAD2   | 

## Appendix: Checklists<a name="appendix-checklists"></a>

Use the following checklists to ensure that you configure and test your product before you submit it to the MCO team\. 

### Product creation checklist<a name="product-creation-checklist"></a>
+ Create \(or use an existing\) VPC and then configure it\. 
+ Create and configure a network load balancer within the VPC\. 
+ Register your service with your network load balancer by creating a VPC endpoint service\. 
+ Provide the AWS account ID you used to configure the VPC endpoint to MCO\. 
+ Provide the default endpoint service name \(for example, com\.amazonaws\.vpce\.us\-east\-1\.vpce\-svc\-0bbb070044a2164\) to MCO\. 
+ Provide a user\-friendly service DNS name \(required\) to override the randomly generated service DNS name\. Request SSL certificates from ACM for the subdomain used for your user\-friendly service DNS name\. Provide these certificates and the AWS account ID you used to request them to the MCO team\. 
+ Recommended: Provide a private DNS name\. 
+ Create a process to inform and allow your AWS Marketplace buyers the option to connect to your service using AWS PrivateLink technology\. Add AWS account IDs for your buyers to your allowed list of accounts\. 

### Product testing<a name="product-testing"></a>
+ Verify that your service is configured and discoverable\. 
+ Verify that your service is discoverable over the network load balancer\. 
+ Verify that a buyer can create a VPC endpoint and access your service\. Use an AWS account you own that is not the account you used to set up your service\. 