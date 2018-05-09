# Product Support Connection<a name="product-support-connection"></a>

## Product Support Connection<a name="product-support-connection"></a>

 AWS Marketplace Product Support Connection \(PSC\) is a feature that allows AWS Marketplace customers to provide contact information in the AWS Marketplace website for the purposes of obtaining and accessing product support from AWS Marketplace Sellers\. AWS Marketplace shares the provided data with participating Sellers via an API to enable a better support experience\. Customers can choose to add contact details during or after a purchase of PSC\-enabled AWS Marketplace products, and Sellers can retrieve the Customer contact data, along with relevant product subscription details, by calling a pull\-based API\. 

 Your staff can use the Customer Support Eligibility tool to access near\-real\-time information about a customer's subscription to your products and provide fast, personalized service\. AWS Marketplace Management Portal makes it easy to get started: enter a customer's AWS account ID to retrieve subscription and usage information from their account\. 

 You also have the option to enroll your products in AWS Marketplace Product Support Connection \(PSC\)\. For products that are enrolled in PSC, AWS Marketplace customers can choose to provide contact information \(including name, organization, email address, and phone number\) via the AWS Marketplace web site for the purposes of obtaining and accessing product support\. If you enroll in PSC, AWS Marketplace will share the provided data with you via an API to help enable a more seamless support experience\. 

### How does AWS Marketplace Product Support Connection benefit me as a Seller?<a name="how-does-aws-marketplace-product-support-connection-benefit-me-as-a-seller"></a>

 Participating in PSC can make it easier for you to provide support to customers that subscribe to your products on AWS Marketplace\. The data available through the program lets you keep customer contact information up to date in your support or CRM system\(s\)\. If an AWS Marketplace customer shares contact information through PSC and then contacts you for support, you will be able to quickly access and verify the customer’s identity and product subscription details\. 

### What information will AWS Marketplace Product Support Connection collect from customers?<a name="what-information-will-aws-marketplace-product-support-connection-collect-from-customers"></a>

 We collect first and last name, job title, company name, email address, telephone number, country, and zip code\. Providing contact details is optional, but if a customer chooses to provide contact details, then organization, first and last name, email, and telephone number are required fields\. All provided details, along with the customer’s AWS account number, product ID, product code, and subscription start date, are available to participating Sellers via a pull\-based API\. Customers can add information for up to 5 contacts per product subscription, and they can also edit or delete their contact details later\. 

### Will I receive contact details for every customer subscribed to my product?<a name="will-i-receive-contact-details-for-every-customer-subscribed-to-my-product"></a>

 Not necessarily\. Entering and sharing contact information is optional for customers, although we recommend that customers share at least one contact for supported products in order to receive a better product support experience\. 

### At what point in the purchase process does a customer become eligible for PSC?<a name="at-what-point-in-the-purchase-process-does-a-customer-become-eligible-for-psc"></a>

 Customers have the option to provide contact details for PSC during or after a subscription to a PSC\-enabled product\. For AMI\-based products, customers that choose Annual or Monthly subscription options are charged for the product when they subscribe; customers that choose hourly subscriptions are charged when they launch an instance\. For more information about what it means for customers to subscribe to a product, please visit the [AWS Marketplace Help Pages](https://aws.amazon.com/marketplace/help/200799470)\. 

### Will I receive data about a customer’s product usage?<a name="will-i-receive-data-about-a-customers-product-usage"></a>

 No; at this time, PSC collects contact details and subscription information only\. Usage data is not currently collected as part of this program\. 

## Seller Requirements<a name="seller-requirements"></a>

### What do I need to do to qualify to participate in AWS Marketplace Product Support Connection?<a name="what-do-i-need-to-do-to-qualify-to-participate-in-aws-marketplace-product-support-connection"></a>

 To participate, there are specific policies you must follow: 
+  You must list commercially supported, enterprise production versions of your software with a dedicated support email address \(or equivalent contact method\) that is usable by customers and AWS Customer Support\. 
+  You must compensate your sales force for all AWS Marketplace transactions that occur in a sales territory or named account segment\. Communication on AWS Marketplace compensation must be sent to your Global Field, and AWS must receive a copy of that communication\. 
+  Your Customer Support teams must outline a policy regarding how you plan to provide support for AWS Marketplace customers, and should provide AWS Marketplace with a copy of your policy\. This guidance must be provided to your Customer Support teams in order for AWS Marketplace to engage with your Customer Support\. 
+  Any customer information provided to you through the API should be added to your systems within one business day\. In addition, customers must have the ability to opt out of the program at any time\. The data available through the PSC API will indicate when a customer has deleted contact details and wishes to be removed from the program\. 

 If you have any questions about these program requirements, please reach out to the AWS Marketplace Seller Operations team at aws\-mp\-seller\-ops@amazon\.com\. 

### What steps do I need to complete in order to participate in Product Support Connection?<a name="what-steps-do-i-need-to-complete-in-order-to-participate-in-product-support-connection"></a>

 You must complete the following steps in order to participate: 

1.  Using the static test dataset that is available, integrate with the PSC API so that data provided through the API will be added to your backend CRM or support system\(s\) within no more than one business day\. See “Integrating with the Seller API” and “Handling Customer Data” below for more details\. 

1.  Provide a list of the product\(s\) you would like to enroll in the program to the AWS Marketplace team \(aws\-marketplace\-seller\-ops@amazon\.com\)\. This will ensure that your products are flagged for enrollment in PSC\. See “Enrolling Your Products” below for more details\. 

1.  Work with the AWS Marketplace team to ensure that your product detail pages contain a valid support email address or equivalent contact method\. 

1.  Provide a description \(about 1 page\) of the support processes you plan to follow for AWS Marketplace customers, and submit your description to aws\-marketplace\-seller\-ops@amazon\.com\. This description should outline your planned support processes in a few paragraphs and should be provided to AWS Marketplace in addition to being communicated to your internal support team\. This document is for AWS Marketplace internal use and helps us track the customer experience across products that are enrolled in PSC\. See below for a list of questions your writeup should address\. 

1.  You can optionally customize your Welcome email, which customers receive after subscribing to your product, to describe your PSC support processes or give your customers more information about product support\. Please reach out to aws\-marketplace\-seller\-ops@amazon\.com if you wish to customize your Welcome email content\. 

### What information should I include in my description of support processes?<a name="what-information-should-i-include-in-my-description-of-support-processes"></a>
+  Which product listing\(s\) will you enroll in PSC? 
+  Have you already built and tested a way to pull data from the API and port it to your support systems? 
  +  If yes, please describe how you import this data to your support systems? 
  +  If no, when do you expect to have this implemented? Please describe your planned approach\. 
+  Please summarize your support process for AWS Marketplace customers that participate in PSC\. 
  +  How can AWS Marketplace PSC customers contact you to receive support for these products \(email, phone, other methods\)? 
  +  If PSC customers contact you for support, how long will it typically take before they receive a reply? 
  +  Do you have different support levels for different AWS Marketplace products? If so, please describe your support tiers and what they cover\. 
  +  What communications do you plan to send to customers under your support policy? If you plan to send proactive communications, please describe what you plan to send\. 
  +  After customers enter their data in the AWS Marketplace site, how long will it take for the data to appear in your support system\(s\)? 
  +  If a customer opts out of PSC, what is your process for deleting their contact data? 
  +  Do you have a web page describing the support you offer for AWS Marketplace customers? If so, please provide it\. 

## Enrolling Your Products<a name="enrolling-your-products"></a>

### How do I enroll products in PSC?<a name="how-do-i-enroll-products-in-psc"></a>

 After reviewing the program requirements, contact the AWS Marketplace Seller Catalog Operations team to provide a list of the products you would like to enroll in PSC\. You can enroll new or existing AMI\-based product listings in the program\. Please allow 1\-2 weeks for your request to be processed\. You will need to verify that you have completed integration with the API before your products can be enabled for PSC\. As described above, you must also provide a valid support email address on your product listing page\(s\), and you should provide a writeup describing the data handling and support process you plan to follow for AWS Marketplace customers\. 

## Handling Customer Data<a name="handling-customer-data"></a>

### How can I use the data available through Product Support Connection?<a name="how-can-i-use-the-data-available-through-product-support-connection"></a>

 Information you receive under the PSC program constitutes “Subscriber Information” under the Terms and Conditions for AWS Marketplace Sellers \(the “Seller Terms”\) and may only be used in accordance with the Seller Terms \(including Section 3\.8 thereof\)\. The data cannot be used for marketing or other purposes not related to product support\. 

### How should I handle and store customer data provided through AWS Marketplace Product Support Connection?<a name="how-should-i-handle-and-store-customer-data-provided-through-aws-marketplace-product-support-connection"></a>

 You must handle customer data in accordance with applicable law and your privacy policy; we recommend that customer data should be encrypted in transit and at rest\. The provided customer data constitutes Subscriber Information under the Seller Terms and can only be used for providing product support\. 