# Seller Private Offers<a name="private-offers-overview"></a>

 AWS Marketplace seller private offers are a purchasing program that allows you and AWS Marketplace customers to negotiate custom price and end user licensing agreement \(EULA\) terms for a software purchase\. 

**Note**  
 Private offers are available in AWS GovCloud \(US\-East\) and AWS GovCloud \(US\-West\)\. 

 You must be enrolled in the [AWS Marketplace Enhanced Data Sharing Program](enhanced-data-sharing-program.md) and contact your AWS Marketplace representative to participate in this program\. In addition to AWS Marketplace seller private offers, you can also offer enterprise contract private offers, which use the enterprise contract EULA\. You can directly handle many private offers by using the **Offers** tab in the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management)\. 

 Some private offers might require the assistance of the AWS Marketplace Customer Desk mpcustdesk@amazon\.com\. For example, custom private offers that can’t be defined using AWS Marketplace Management Portal or private offers that involve multiple parties, such as a consulting partner creating a private offer\. 

 As the seller, you use the AWS Marketplace Management Portal on the **Offers** tab to create the private offer\. You specify the product that the offer is being made for and the payer account's customer ID for the customer or customers who you're creating the offer for\. AWS Marketplace Management Portal generates a unique ID and URL for the offer\. The customer isn't notified that you created a private offer\. You can provide the link to the customer, or they can navigate to your product through AWS Marketplace\. When the customer navigates to your product's subscription page, a banner indicates that a private offer is available\. After the customer accepts the offer, they're invoiced for the purchase using the same portal tools used for all AWS Marketplace transactions\. 

 In AWS Marketplace reports, there are two columns that help you identify private offer transactions\. The **Offer ID** column contains the identifier for the offer signed by the customer\. The **Offer Visibility** column indicates whether the offer is public or private\. The [Monthly Billed Revenue Report](monthly-billed-revenue-report.md) report is generated every month and has offer visibility and offer ID information\. When an invoice gets generated for a customer, it appears in the report, covering the appropriate billing period\. 

 You can create simple private offers using the AWS Marketplace Management Portal\. The following process is for creating relatively uncomplicated private offers\. If you are creating a private offer that we consider more complex, you must follow the [Custom Private Offers](#custom-private-offers) process\. The following are examples of private offers that we consider more complex: 
+  Bring your own license model \(BYOL\) 
+  Upfront billing for a suite of products 
+  Unlimited access to a license for one cost 

**Note**  
 You can't create private offers for second party \(2P\), AMI monthly, SaaS redirect, or AMI\-based delivery using AWS CloudFormation products, or for limiting customer usage\. 

 When you create a private offer, you can extend the offer to up to 10 accounts, and the offer is only visible to the accounts that you create the offer for\. You can't view the offer unless you extend the offer to your account when creating the private offer\. You can't force service limits in the offer, so the customer can use as much of your product at the negotiated prices as they want, unless you enforce a limit within your product\. Private offers are not available to customers set up for credit card billing with AWS\. 

**Key points for private offers for AMI\-based products**
+ You can provide private offers pricing for AMI contracts\. The offer can be any custom duration in days, up to 3 years \(or 1,095 days\)\.
+ License entitlements begin on the date the buyer accepts the private offer\.
+ Buyers must be on invoicing terms in order to receive a flexible payment schedule with their private offer\.
+ For AMI private offers with flexible payment schedules, you can set the number of instances agreed to in the contract, for the duration of the contract\. You can also define a custom hourly price for those same instances if the buyer uses more\. 

**Key points for private offers for SaaS\-based products**
+  AWS Marketplace seller private offer products can't change the pricing level for a given pricing tier based on timing\. For example, an offer can't charge $0\.80/hour for three months and then change pricing to $0\.60/hour thereafter for the same pricing tier\. 
+  For SaaS contracts, private offers don't monitor usage\. Buyers can manually upgrade to new contracts levels at any time, but it is up to the ISV to define contract tiers, enforce service limitations, and advise customers to manually upgrade to higher contract tiers when needed\. 
+  The duration dimensions that appear on a SaaS contract private offer matches the durations enabled when the public product listing was created\. For SaaS contracts, this is 1 month, 1 year, 2 years, and/or 3 years\. 
+  Buyers must be on invoicing terms in order to receive a flexible payment schedule with their private offer\. 

**Key points for private offers for consulting partner private offers**
+  If you are a consulting partner, through consulting partner private offers you can negotiate special terms with an ISV\. With this type of offer, both you and the ISV are listed as sellers\-of\-record\. This type of private offer requires AWS Marketplace engagement and support\. 
+ For any type of private offer, the customer must configure their AWS account to use invoicing\. Consulting partner private offers work the same way\. You must configure your AWS account for invoicing to accept a private offer\.

## Offer Submission Process<a name="offer-submission-process"></a>

**To create a private offer**

1.  Sign in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management) and choose **Offers**\. 

1. On the **Manage Private Offer** page, choose **CREATE AN OFFER**\. 

1. On the **Create Private Offer** page, select the product from the drop\-down list and enter the AWS account ID of the AWS Marketplace customer\. If your customer is paying for the product in installments, select **Allow buyers to pay for this product in installments \(ISV only\)**\. Verify the information that you entered and then choose **NEXT**\. 
**Note**  
Selecting **Allow buyers to pay for this product in installments \(ISV only\)** enables you to offer your customer a payment schedule with annual payments that aren't evenly distributed, multiple payments for a multi\-year deal, or quarterly payments\. For instructions on configuring your private offer for installment payments, see [Flexible Payment Scheduler](flexible-payment-scheduler.md)\.

1. On the **Create an Offer** page, verify the product name and buyer ID\.

1. If the product offering is for an AMI hourly or AMI annual pricing model, specify the **Contract duration**, by choosing a radio button or entering a custom duration in number of days\.
**Note**  
 The duration of the offer can be up to 1,095 days\. 

1.  In **Input offer price**, enter the pricing information that you negotiated with the customer\. If you have installment payments for the private offer, specify the number of units and the payment schedule for the contract duration\. For more information on installment payments, see [Flexible Payment Scheduler](flexible-payment-scheduler.md)\. 

1. In **Upload End User License Agreement**, drag and drop or upload your EULA PDF file\.

1. In **Offer Expiration and Acceptance Date**, enter the number of days that the offer is valid for\.
**Note**  
This is the number of days after the customer accepts the offer that the terms of the agreement are active\. After the number of days has lapsed, the price and EULA revert to the terms provided in the public offering\. 

1. For **Buyer needs to accept the offer by**, enter the date when the offer is no longer available if not accepted\.
**Note**  
This is the date that the offer becomes null and void, and the customer can't accept the offer under the custom terms that you have specified\. 

1.  Choose **REVIEW OFFER**\. 

1.  On the **Review Offer** page, verify the offer information and the PDF file\. Then do one of the following:
   +  If the offer is correct, choose **EXTEND OFFER**\. 
   +  If the offer is incorrect, choose **EDIT OFFER** and make any required changes\. 

The offer should appear on the **Manage Private Offer** page in approximately 45 minutes\. To view the offer, sign in to the AWS Marketplace Management Portal and choose **Private Offer**\. This opens the **Manage Private Offer** landing page\. 

## Custom Private Offers<a name="custom-private-offers"></a>

 Custom private offers are offers that are manually published by the AWS Marketplace business development operations team\. This process must be used to create private offers for Bring Your Own License model \(BYOL\), billing upfront for a suite of products, and unlimited access to a license for one\-cost contracts\. The steps for each private offer type are different\. The BD team will contact you if they need information specific to your private offer request\. 

 To request a custom private offer, email the AWS Marketplace Customer Desk \(mpcustdesk@amazon\.com\) team or work with your customer advisor or BD contact\. The team will email you instructions, including forms that you must complete and return for review\. After you have returned the completed forms, the team review the offer to ensure that it conforms with existing billing mechanisms and meets the minimum deal threshold\. If the offer is approved, the process takes 5–7 business days from first contact with AWS Marketplace\. When your private offer is published on AWS Marketplace, the AWS Marketplace Customer Desk team emails you a link to the private offer, which is visible to the buyer in their AWS Marketplace portal\. 

 These are the process milestones: 

1.  If the product isn't public, the [AWS Marketplace Managed Catalog Operations \(MCO\)](https://aws.amazon.com/marketplace/management/contact-us/) team creates a new product to build the offer from\. You need to complete the product load form and submit it to the AWS Marketplace Customer Desk\. The product is published using the standard publishing process\. This adds another 3–5 business days to build the offer\. 

1. You and the customer must agree to new pricing dimensions or the EULA that constitutes the private offer\. For custom private offers that AWS manually publishes, a custom transaction request form \(TRF\) is required to delineate the details of the offer\. If the customer uses the normal subscription invoicing process, you must sign the TRF, but the customer doesn't\. If the customer uses nonstandard invoicing, you and the customer must sign the TRF\. To get the TRF or to submit the completed TRF, email the AWS Marketplace Customer Desk or contact your customer advisor or BD contact\. 

1.  Your private offer is published based on the product in milestone 1 and the subscription detail in the TRF\. The offer appear on the customer’s **AWS Marketplace Manage Private Offer** page\. 

1.  A banner indicates that a private offer available is available for the customer\. After the customer accepts the offer, they're invoiced for the purchase using the same tools used for all AWS Marketplace transactions\. If the offer used nonstandard invoicing, AWS bills the customer directly, and the customer is granted access to the product in their library\. 

 Custom private offers that go through this process appear in reports just like other private offers\. 

## Custom Private Offers with Flexible Payment Scheduler<a name="flexible-private-scheduler-link"></a>

 To create a custom private offer with a flexible payment schedule, see [Flexible Payment Scheduler](flexible-payment-scheduler.md)\. 

## Experience for the Buyer of a Seller Private Offer<a name="experience-for-the-buyer-of-a-seller-private-offer"></a>

 As you create and execute a private offer, you and the customer have steps to complete\. The experience for the customer is as follows: 

1.  A customer with a private offer can access the offer directly by the link provided to them\. The link might come from the seller of record or the AWS Marketplace Customer Desk, or through the banner at the top of the page for the product that the private offer is for\. The link takes the customer to the product fulfillment page, which requires the customer to authenticate with credentials \(root IAM user\) for the account that the offer was extended to: the payer account for the customer\. Private offers must be accessed from the AWS Marketplace page\. Customers can also find the most recent private offer by visiting the public product's detail page and choosing **Continue** to access the product's fulfillment page\. After authenticating with the account’s credentials, the customer has a blue banner indicating that they have a private offer\. To access the most recently created private offer for that product, the customer follows the link in the banner\. 

1.  When the customer is ready to accept the private offer, the customer chooses **Accept Offer** in the pricing box\. From that point until the expiration date noted in the pricing box, any running instances, annual software purchases, metering records, or contract purchases are charged at the rates shown in the private offer\. Customer use of the software doesn't change from customer usage of a product with a public offer\. Whether for a deployed instance or a new instance, customer usage is charged at the new private offer price after the offer is accepted\.

**Note**  
 To receive the terms of the offer, your customer must accept the offer\. You can provide a URL to the fulfillment page for the offer, or the customer can navigate to your product page on AWS Marketplace and choose the page banner that indicates there is a private offer available\. 

 Subscribing to the private offer doesn't require launching a new instance of the software\. Accepting the private offer modifies the price of existing instances to correspond to the private offer price\. If a product offers 1\-click launch, the customer can deploy a new instance of the software\. If a product defaults to 1\-click launch, the customer can accept a private offer without launching a new instance by choosing **Manual Launch** on the fulfillment page\. As with all AWS Marketplace products, the customer can use the Amazon EC2 console to deploy more instances\. 

## Reporting for Seller Private Offers<a name="reporting-for-seller-private-offers"></a>

 AWS Marketplace seller private offers appear on the existing seller reports and in the reports relevant to the offer\. The **Offer ID** and **Offer Visibility** fields contain information about the offers\. 

![\[Example of Private Offers Reporting\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/private-offers-07.png)

 The **Offer ID** field contains the unique offer ID generated for the private offer\. It's blank unless the report entry is for a private offer\. The **Offer Visibility** field indicates whether the report entry is a public or private offer\. For all AWS Marketplace seller private offers, the entry is marked private\. 