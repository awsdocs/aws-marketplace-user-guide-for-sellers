# Using AWS PrivateLink with AWS Marketplace<a name="privatelink"></a>

 AWS Marketplace supports AWS PrivateLink, a technology that allows you to use the Amazon network to provide your customers with access to products you sell through AWS Marketplace\. This document outlines the process for configuring and delivering your products through an Amazon Virtual Private Cloud \(VPC\) endpoint using AWS PrivateLink technology\. 

 In this document, we assume that you have working knowledge of several AWS services and the AWS Marketplace environment\. 

## Introduction<a name="introduction"></a>

 As an AWS Marketplace vendor, you can provide AWS customers access to your service through an Amazon VPC endpoint\. This approach provides customers with access to your service across the Amazon network using [AWS PrivateLink](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Introduction.html#what-is-privatelink) technology\. If you use AWS Marketplace to create and deliver this offering, your customer will be able to discover your service in AWS Marketplace\. Your customer will also find your product in the list of available services for creating a VPC endpoint\. 

 ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/private-endpoint-diagram.png) 

A [VPC endpoint](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-endpoints.html) is a virtual device that enables AWS customers to create a private connection between their VPC and another AWS service without requiring access over the internet, through a NAT device, a VPN connection, or AWS Direct Connect\. You can create an endpoint service through AWS Marketplace that makes it possible for AWS Marketplace customers to connect to your service using this technology\. This is designed to be more secure for your customers because customers access your service through the Amazon private network rather than through the Internet\. 

 For each region in which you want to offer your service, you create or use existing resources to configure a VPC, set up your service instances, set up a network load balancer, and register your services with the network load balancer by creating a service endpoint\. After those steps are complete and you have tested your offering, you provide your configuration information to the Athe [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

 Although it is optional, we strongly encourage you to provide a private DNS name that your customer can use when they create a VPC endpoint\. 

 When the customer creates their VPC endpoint, they have the option to enable a private DNS name\. By choosing this option, the customer’s VPC service configures a [private hosted zone](http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/hosted-zones-private.html)\. If you provide the private DNS name, it will be used by the customer when they configure their VPC endpoint to connect to your service\. In the customer’s private hosted zone, the private DNS name \(api\.example\.com\) will point to the randomly generated DNS name\(s\) \(vpce\-11111111111111111\-yyyyyyyy\.api\.vpce\.example\.com\) created for your endpoint service\(s\)\. The benefit for your customer is that the customer’s EC2 instances call the same unified DNS name \(api\.example\.com\) across different VPCs\. Also, if public and private DNS names are same, the AWS Marketplace customer can use the same public name when accessing your service from within or outside of the VPC\. 

 The the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team will assist you with making your service available through AWS Marketplace\. When an AWS Marketplace customer subscribes to your service and is creating a VPC endpoint, your service will be listed in **Your AWS Marketplace Services**\. The MCO team uses the user\-friendly DNS name for easy discovery of your service when creating the VPC endpoint\. 

 Your product is created and listed as a software as a service \(SaaS\) product on AWS Marketplace\. Your customer can discover your product through the AWS Marketplace website\. Metering and billing will be the same as with other AWS Marketplace SaaS products\. To provide your customer access to your service offering, you whitelist their account ID\. They establish a VPC endpoint \(configured as an interface\) within their VPC to connect to you\. Only customers who are subscribed and whitelisted will see your product listed when they create a VPC endpoint\. 

## Configuring Your Product<a name="configuring-your-product"></a>

 To configure your product to be available through an Amazon VPC endpoint: 

1.  Create or use an existing [Amazon VPC](https://aws.amazon.com/documentation/vpc/)\. 

1.  Create \(or use existing\) [Amazon EC2](https://aws.amazon.com/documentation/ec2/) instance\(s\) for your product\. 

1.  Create a [network load balancer](http://docs.aws.amazon.com/elasticloadbalancing/latest/network/network-load-balancer-getting-started.html) in each of the regions in which you will offer your product\. We recommend that you include all [Availability Zones](http://docs.aws.amazon.com/elasticloadbalancing/latest/classic/enable-disable-az.html) \(AZs\) for a region\. 

1.  Use the Amazon VPC console, the CLI, or supported SDKs to create a VPC endpoint service\. 

1.  Verify that you can access the service through the network load balancer\. 

1. [Request a certificate from AWS Certificate Manager](http://docs.aws.amazon.com/acm/latest/userguide/gs-acm-request.html) for your user\-friendly DNS name\. Before AWS Certificate Manager \(ACM\) issues a certificate, it validates that you own or control the domain names in your certificate request\. 

1.  Delegate the subdomain of your user\-friendly DNS name, such as api\.vpce\.example\.com, to the name servers provided to you by the MCO team\. In your DNS system, you must create a name server \(NS\) resource record to point this subdomain to the Route 53 name servers provided by the MCO team so that DNS names \(such as vpce\-0ac6c347a78c90f8\.api\.vpce\.example\.com\) are publicly resolvable\. 

1.  Whitelist the AWS accounts the customer will use to access your service\. 

    **Note**: You can use a supported SDK or this CLI command to automate the whitelisting of accounts: aws vpcev2 modify\-vpc\-endpoint\-service\-permissions \-\-service\-id vpce\-svc\-0123456789abcdef1 \-\-add\-allowed\-principals arn:aws:iam::111111111111:root arn:aws:iam::222222222222:root\. 

## Submitting Your Product to AWS Marketplace<a name="submitting-your-product-to-aws-marketplace"></a>

 During the process of publishing your service to AWS Marketplace, you will work with the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team to verify settings are correct and the customer has a good experience\. To submit your PrivateLink\-enabled product: 

1.  Email the following information to the <ulink url="https://aws\.amazon\.com/marketplace/management/contact\-us/"><emphasis role="strong">&MKTlong; Seller Operations</emphasis></ulink> team: 

   1.  The endpoint from Section 2, step 4 and the AWS account used to create the endpoint\. The name will be similar to this: com\.amazonaws\.vpce\.us\-east\-1\.vpce\-svc\-0daa010345a21646 

   1.  The user\-friendly DNS name for your service\. \(This is the DNS name that AWS Marketplace customers will use to access your product\.\) 

   1.  The AWS account you used to request certificates in Section 2, step 6, and the private DNS name AWS Marketplace customers will use to access the VPC endpoint\. 

       The AWS Marketplace MCO team will verify your company’s identity \(your company name\) and the DNS name to use for the service you are registering \(such as api\.vpce\.example\.com\)\. After the information is verified, the DNS name will override the default base endpoint DNS name assigned in Section 2, step 4\. 

## Customer Access to VPC Endpoints<a name="customer-access-to-vpc-endpoints"></a>

 AWS Marketplace customers will discover your service in a way that is similar to the way they discover other AWS services when creating a VPC endpoint\. Customers creating a VPC endpoint cannot discover your service unless: 
+  You follow the process described in Section 3 to create or use an existing product\. 
+  Customers have subscribed to your service\. 
+  You have whitelisted the customer account they are using to discover your service\. 

 When the customer creates the VPC endpoint, they have the option to associate a private hosted zone with their VPC\. The hosted zone contains a record set for the default private DNS name for the service that resolves to the private IP address of the endpoint network interfaces in their VPC\. 

 Any customer\-hosted endpoint, including AWS Marketplace services, can provide permissions to all accounts \(the "\*" permission\)\. However, when you use this approach, the services will not be listed in the **Describe** calls or console unless you search by the service name\. To display the services in the **Describe** calls, the customer's account must be explicitly whitelisted by the service\. 

 To access your service, AWS Marketplace customers: 

1.  Discover and subscribe to your service on AWS Marketplace\. 

1.  Use the AWS Command Line Interface \(CLI\), API, or the Amazon VPC console to discover your service and then establish a VPC endpoint to connect to your service in the subnets and AZs your customers choose\. The endpoints will appear as elastic network interfaces in the subnets\. Local IP addresses and region and zonal DNS names are assigned to the endpoints\. 


|  **Client\-side DNS Name**  |  **Name**  | 
| --- | --- | 
|   Regional   |   Vpce<0dc9a211a78c90f8>\.api\.vpce\.example\.com   | 
|   IAD2 \(1a \)   |   **us\-east\-1a**\-Vpce<0dc9a211a78c90f8>\.api\.vpce\.example\.com   | 
|   IAD2 \(1b \)   |   **us\-east\-1b**\-Vpce<0dc9a211a78c90f8>\.api\.vpce\.example\.com   | 

 If you provided a default private DNS name and if the customer chooses **Enable Private DNS Name** \(associated a private hosted zone\) when creating a VPC endpoint, the customer will see the regional default private DNS name to connect to your service: 


|  **Name**  |  **Alias**  |  **Alias Hosted Zone ID**  |  **\(Notes\)**  | 
| --- | --- | --- | --- | 
|  api\.example\.com  |  vpce<0dc9a211a78c90f8>\. api\.vpce\.example\.com  |  Z00AABBCCDD  |   IAD1   IAD2   | 

## Appendix: Checklists<a name="appendix-checklists"></a>

 Use the following checklists to ensure that you have completed the configuration and testing of your product before you submit it to the MCO team\. 

### Product Creation Checklist<a name="product-creation-checklist"></a>
+  Create \(or use an existing\) VPC and then configure it\. 
+  Create and configure a network load balancer within the VPC\. 
+  Register your service with your network load balancer by creating a VPC endpoint service\. 
+  Provide the AWS account ID you used to configure the VPC endpoint to MCO\. 
+  Provide the default endpoint service name \(for example, com\.amazonaws\.vpce\.us\-east\-1\.vpce\-svc\-0bbb070044a2164\) to MCO\. 
+  Provide a user\-friendly service DNS name \(required\) to override the randomly generated service DNS name\. Request SSL certificates from ACM for the subdomain used for your user\-friendly service DNS name\. Provide these certificates and the AWS account ID you used to request them to the MCO team\. 
+  Provide a private DNS name\. \(Recommended, but not mandatory\.\) 
+  Create a process to inform and allow your AWS Marketplace customer the option to connect to your service using AWS PrivateLink technology: 
  +  AWS Marketplace customer’s AWS account ID\. 
  +  Whitelist the customer’s AWS account ID \(for example, account: arn:aws:iam::123456789012:root\)\. 

### Product Testing<a name="product-testing"></a>
+  Verify your service is configured and reachable\. 
+  Verify your service is reachable over the network load balancer\. 
+  Verify your customer’s ability to create a VPC endpoint and access your service\. \(Use an account you own, but different from the one used to set up your service\.\) 