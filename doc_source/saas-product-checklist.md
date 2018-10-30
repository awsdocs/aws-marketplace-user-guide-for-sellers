# SaaS Listing Checklist<a name="saas-product-checklist"></a>

Use this checklist to make sure your software as a service \(SaaS\) product is ready to list on AWS Marketplace\. 


**AWS Marketplace Integration Checklist**  

| Category | Requirements | 
| --- | --- | 
| Access | Submitted a Seller Registration Form with the desired AWS account for Marketplace usage | 
| Access | Completed the Seller registration, including T&Cs, bank account, W8/W9 tax form | 
| Access | Cross\-Account Roles configured for registered Marketplace Account | 
| Product Listing | Completed the self\-service listing form in the Management Portal | 
| Product Listing | Provided AWS account IDs for testing in the “notes” section of Self\-Service Listing tool | 
| Product Listing | Provided a URL of EULA in \.txt format in Self\-Service Listing | 
| Product Listing | Received your product code and SNS topic info from MCO | 
| Product Listing | Subscribed to SNS topic & created an SQS queue to subscribe to the SNS topic – info here | 
| Billing Solution | Can send metering records to the BatchMeterUsage API each hour for each customer | 
| Billing Solution | Validated that the costs appear as expected on bills generated for test accounts | 
| Billing Solution | Test for situations such as invalid customer IDs, canceled subscriptions, etc\. | 
| Listing | Submit the Self\-Service Listing back to MCO for publishing to public | 
| Registration | Implemented an HTTPS registration page that can accept HTTP POST requests | 
| Registration | Can accept new customer registrations | 
| Registration | Are NOT storing the registration token in a cookie | 
| Registration | Are using ResolveCustomer to obtain the productcode and customerID from AWS token | 
| Registration | Resolve the Registration Token received from AWS with no delays | 
| Registration | Test that you are not blocked from registering with email services addresses like Gmail | 
| Registration | Test you can accept incomplete registrations and multiple registration attempts | 
| Subscriptions | Test that you can handle Unsubscribe\-Pending and Unsubscribe\-Success messages | 
| Subscriptions | Send final metering records within an hour of receiving an Unsubscribe Pending message | 
| Security | The AWS root account does not have API keys, has a strong password, and is associated with a hardware multi\-factor authentication \(MFA\) device\. All administrative access is through IAM\-created identities\. No shared accounts\. | 
| Security | IAM roles are used for all programmatic EC2 access\. No hard\-coding of credentials into scripts, headers, or source code\. | 
| Security | Comprehensive logging and log consolidation\. | 
| Security | Well\-defined public and private subnet boundaries that isolate application services, database and file systems access\. Distinct data class definitions that demarcate sensitive data and segregate public and private data\. | 
| Security | Private data encryption in transit and at rest with scheduled key rotation\. | 
| Security | Security incident tools and access in place and routinely scheduled incident response exercises that accommodate timely investigation and recovery\. | 
| Reliability | The system adapts to changes in demand scaling up and down as required and employs load balancing to ensure high performance\. The system also provides edge\-based cacheing as required\. | 
| Reliability | Recovery time and point objectives are specified and disaster recovery is scheduled at regular intervals\. Component failure is self\-healing via automated triggers and notifications\. | 