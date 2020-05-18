# SaaS product integration checklist<a name="aws-marketplace-integration-checklist"></a>

Before your SaaS product goes live, use this checklist to verify that you have completed the required configuration\.


|  **Category**  |  **Requirements**  | 
| --- | --- | 
| Access  | Submitted a seller registration form with the desired AWS account for AWS Marketplace usage\.  | 
| Access  | Completed the seller registration, including terms and conditions, bank account, and W8 or W9 tax form\.  | 
| Access  | Configured cross\-account roles for the registered AWS Marketplace account\.  | 
| Product  | Completed the product request form in the AWS Marketplace Management Portal\.  | 
| Product  | Provided AWS account IDs for testing in the Notes tab of the Create product wizard in the AMMP\. | 
| Product  | Provided a URL of the EULA in \.txt format in the Products tab\.  | 
| Product  | Received your product code and Amazon SNS topic information from AWS Marketplace\.  | 
| Product  | Subscribed to the Amazon SNS topic and created an Amazon SQS queue to subscribe to the Amazon SNS topic\.  | 
| Billing Solution  | Validated you can send metering records to the BatchMeterUsage operation each hour for each customer for SaaS subscriptions products\. Can send metering records for additional usage by each customer for SaaS contracts products\.  | 
| Billing Solution  | Validated you can verify customer entitlements from the AWS Marketplace Entitlement Service for SaaS contracts products\.  | 
| Billing Solution  | Validated that the costs appear as expected on bills generated for test accounts\.  | 
| Billing Solution  | Tested for situations such as invalid customer IDs and canceled subscriptions\.  | 
| Product  | Submitted the product request back to AWS Marketplace for publishing\.  | 
| Registration  | Implemented an HTTPS registration page that can accept HTTP POST requests\.  | 
| Registration  | Validated you can accept new customer registrations\.  | 
| Registration  | Validated you are not storing the registration token in a cookie\.  | 
| Registration  | Validated you are using ResolveCustomer to obtain the ProductCode and CustomerIdentifier from the AWS token\.  | 
| Registration  | Validated you can resolve the registration token received from AWS with no delays\.  | 
| Registration  | Tested that you aren't blocked from registering with email services addresses such as Gmail\.  | 
| Registration  | Tested that you can accept incomplete registrations and multiple registration attempts\.  | 
| Subscription  | Test that you can handle unsubscribe\-pending and unsubscribe\-success messages\.  | 
| Subscription  |  Validated that you send ﬁnal metering records within an hour of receiving an `unsubscribe-pending` message\.   | 
| Security  | Validated the AWS root account doesn't have API keys, has a strong password, and is associated with a hardware multi\-factor authentication \(MFA\) device\. All administrative access is through identities created with AWS Identity and Access Management \(IAM\)\. No shared accounts\.  | 
| Security  | Validated that IAM roles are used for all programmatic Amazon Elastic Compute Cloud \(Amazon EC2\) access\. Credentials aren't hard\-coded into scripts, headers, or source code\.  | 
| Security  | Validated you maintain comprehensive logging and log consolidation\.  | 
| Security  | Verified you have well\-deﬁned public and private subnet boundaries that isolate application services and access to database and ﬁle systems\. Distinct data class deﬁnitions that demarcate sensitive data and segregate public and private data\.  | 
| Security  | Verified you have private data encryption in transit and at rest with scheduled key rotation\.  | 
| Security  | Validated you have security incident tools and access in place and routinely scheduled incident response exercises that accommodate timely investigation and recovery\.  | 
| Reliability  | Verified the system adapts to changes in demand, scaling up and down as required, and employs load balancing to ensure high performance\. The system also provides edge\-based caching as required\.  | 
| Reliability  | Validated recovery time and point objectives are speciﬁed, and disaster recovery is scheduled at regular intervals\. Component failure is self\-healing via automated triggers and notiﬁcations\.  | 