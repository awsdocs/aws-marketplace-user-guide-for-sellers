# Private Offers<a name="private-offers-overview"></a>

Private offers are a purchasing program that allows providers and subscribers to negotiate custom prices and end user licensing agreement \(EULA\) terms for software purchases in AWS Marketplace\.

## How Private Offers Work<a name="private-offer-how-it-works"></a>

You can create and manage all of your private offers from the **Offers** page in the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management)\. You specify the product that the offer is being made for and the AWS account ID \(or IDs\) for the subscriber \(or subscribers\) you're creating the offer for\. AWS Marketplace Management Portal generates a unique ID and URL for the offer\.

In addition to private offers, you can also offer enterprise contract private offers, which use the enterprise contract EULA\.

 When you create a private offer, you can extend the offer to up to 25 accounts\. The offer is visible only to the accounts that you create the offer for\. Subscribers can't view the offer unless you extend the offer to either their linked account or to their master payer account\. You can't force service limits in the offer, so the subscriber can use as much of your product at the negotiated prices as they want, unless you enforce a limit in your product\.

**Note**  
The subscriber isn't notified that you created a private offer\. You can provide the URL for the custom offer to the subscriber, or they can navigate to your product through AWS Marketplace\.

When the subscriber navigates to your product's subscription page, a banner indicates that a private offer is available\. After the subscriber accepts the offer, they're invoiced for the purchase using the same portal tools used for all AWS Marketplace transactions\. 

Private offers are tracked in seller reports\. For more information, see [Reporting for Private Offers](#reporting-for-seller-private-offers)\.

### Private Offer Experience for Subscriber<a name="private-offer-sub-experience"></a>

After you create a private offer and notify the potential subscriber, they will have steps they must perform to accept the offer\. For more information about the subscriber experience for private offers, see [Private Offers](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-private-offers.html) in the *AWS Marketplace Subscribers Guide*\.

To receive the terms of the offer, the subscriber must accept the offer before the offer expiration date\. After the offer expires, the terms are no longer valid\. You must re\-create the private offer for the subscriber to accept the terms\. As the provider, you can provide a URL to the fulfillment page for the offer, or the customer can navigate to your product page on AWS Marketplace and choose the link in the banner to view the private offer\.

## Private Offer Limitations<a name="private-offer-limitations"></a>

When working with private offers, keep the following limitations in mind:
+  You can't create private offers for second party \(2P\), AMI monthly, SaaS redirect, or AMI\-based delivery using AWS CloudFormation products, or for limiting customer usage\. 
+ For private offers with the flexible payment scheduler, it is possible to break upfront commitments into multiple payments over time if subscribers are on invoicing terms with AWS\.

## Supported Product Types<a name="supported-products-private-offers"></a>

Currently, AMI and SaaS products are supported for private offer\.

### Private Offers for AMI Products<a name="ami-private-offers"></a>

You can provide private offers pricing for AMI contracts\. The offer can be any custom duration in days, up to 3 years \(1,095 days\)\. License entitlements begin on the date the subscriber accepts the private offer\. For AMI private offers with flexible payment schedules, you can set the number of instances agreed to in the contract, for the duration of the contract\. You can also define a custom hourly price for those same instances if the buyer uses more\. 

### Private Offers for SaaS Products<a name="saas-private-offers"></a>

SaaS private offer products can't change the pricing level for a given pricing tier based on timing\. For example, an offer can't charge $0\.80/hour for three months and then change pricing to $0\.60/hour thereafter for the same pricing tier\. For SaaS contracts, private offers don't monitor usage\.

Subscribers can manually upgrade to new contracts levels at any time, but it is up to the independent software vendor \(ISV\) to define contract tiers, enforce service limitations, and advise subscribers to manually upgrade to higher contract tiers when needed\. The duration dimensions that appear on a SaaS contract private offer matches the durations enabled when the public product listing was created\. For SaaS contracts, this can be 1 month, 1 year, 2 years, and/or 3 years\. 

## Private Offers through Consulting Partners<a name="consulting-private-offers"></a>

If you are a consulting partner, you can negotiate special terms with an ISV to offer their products to subscribers\. With this type of offer, you are listed as seller\-of\-record\.

For more information, see [Consulting Partner Private Offers](consulting-partner-offers.md)\.

## Offer Submission Process<a name="offer-submission-process"></a>

 You can create simple private offers using the AWS Marketplace Management Portal\. The following procedure is for creating relatively uncomplicated private offers\. If you are creating a private offer that we consider more complex, you must follow the [Custom Private Offers](#custom-private-offers) process\. The following are examples of private offers that we consider more complex: 
+  Bring your own license model \(BYOL\) 
+  Upfront billing for a suite of products 
+  Unlimited access to a license for one cost 

**To create a private offer**

1.  Sign in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management) and choose **Offers**\. 

1. On the **Manage Private Offer** page, choose **CREATE AN OFFER**\. 

1. On the **Create Private Offer** page, select the product from the drop\-down list and enter the AWS account ID \(or IDs\) of the AWS Marketplace subscriber\. If your subscriber is paying for the product in installments, select **Allow buyers to pay for this product in installments \(ISV only\)**\. Verify the information that you entered and then choose **NEXT**\. 
**Note**  
Selecting **Allow buyers to pay for this product in installments \(ISV only\)** enables you to offer your subscriber a payment schedule with annual payments that aren't evenly distributed, multiple payments for a multi\-year deal, or quarterly payments\. Subscribers must be on invoicing terms with AWS to receive a flexible payment schedule on their private offer\. For more information, see [Flexible Payment Scheduler](flexible-payment-scheduler.md)\.

1. On the **Create an Offer** page, verify the product name and subscriber ID\.

1. If the product offering is for an AMI hourly or AMI annual pricing model, specify the **Contract duration**, by choosing a radio button or entering a custom duration in number of days\.
**Note**  
 The duration of the offer can be up to 1,095 days\. 

1.  In **Input offer price**, enter the pricing information that you negotiated with the customer\. If you have installment payments for the private offer, specify the number of units and the payment schedule for the contract duration\. For more information about installment payments, see [Flexible Payment Scheduler](flexible-payment-scheduler.md)\. 

1. In **Upload End User License Agreement**, drag and drop or upload your EULA PDF file\.

1. In **Offer Expiration and Acceptance Date**, enter the number of days that the offer is valid for\.
**Note**  
This is the number of days after the customer accepts the offer that the terms of the agreement are active\. After the number of days has lapsed, the price and EULA revert to the terms provided in the public offering\. 

1. For **Buyer needs to accept the offer by**, enter the date when the offer is no longer available if not accepted\.
**Note**  
This is the date that the offer becomes null and void\. On that date, the subscriber won't be able to accept the offer under the custom terms that you have specified\. 

1.  Choose **REVIEW OFFER**\. 

1.  On the **Review Offer** page, verify the offer information and the PDF file\. Then do one of the following:
   +  If the offer is correct, choose **EXTEND OFFER**\. 
   +  If the offer is incorrect, choose **EDIT OFFER** and make any required changes\. 

The offer should appear on the **Manage Private Offer** page in approximately 45 minutes\. To view the offer, sign in to the AWS Marketplace Management Portal and choose **Private Offer**\. This opens the **Manage Private Offer** landing page\. 

## Custom Private Offers<a name="custom-private-offers"></a>

Custom private offers are offers that are manually published by the AWS Marketplace business development operations team\. This process must be used to create private offers for Bring Your Own License model \(BYOL\), billing upfront for a suite of products, and unlimited access to a license for one\-cost contracts\. The steps for each private offer type are different\. The AWS Marketplace business development operations team will contact you if they need information specific to your private offer request\.

To request a custom private offer, [contact us](https://aws.amazon.com/marketplace/management/contact-us/) or work with your customer advisor or AWS Marketplace business development operations team contact\. We will email you instructions, including forms that you must complete and return for review\. After you have returned the completed forms, we'll review them to ensure that they conform with existing billing mechanisms and meet the minimum deal threshold\.

If the offer is approved, the process takes 5–7 business days from first contact with AWS Marketplace\. When your private offer is published on AWS Marketplace, we'll email you with a link to the private offer, which is visible to the subscriber in the AWS Marketplace Management Portal\. 

Custom private offers are tracked in seller reports just like other private offers\. For more information, see [Reporting for Private Offers](#reporting-for-seller-private-offers)\.

The following process outlines how custom private offers are created and implemented: 

1.  If the product isn't public, the [AWS Marketplace Managed Catalog Operations \(MCO\)](https://aws.amazon.com/marketplace/management/contact-us/) team creates a new product to build the offer from\. You need to complete the product load form and submit it to the AWS Marketplace Customer Desk\. The product is published using the standard publishing process\. This adds another 3–5 business days to build the offer\. 

1. You and the subscriber must agree to new pricing dimensions or the EULA that constitutes the private offer\. For custom private offers that AWS manually publishes, a custom transaction request form is required to delineate the details of the offer\. If the subscriber uses the normal subscription invoicing process, you must sign the transaction request form\. If the subscriber uses nonstandard invoicing, both you and the subscriber must sign the transaction request form\. To get the form or to submit the completed one, [contact us](https://aws.amazon.com/marketplace/management/contact-us/) or contact your customer advisor or AWS Marketplace business development operations team contact\. 

1.  Your private offer is published based on the product in milestone 1 and the subscription detail in the transaction request form\. The offer appears on the subscriber’s **AWS Marketplace Manage Private Offer** page\. 

1. A banner indicates that a private offer is available for the subscriber\. After the they accept the offer, they're invoiced for the purchase using the same tools used for all AWS Marketplace transactions\. If the offer used nonstandard invoicing, AWS bills the subscriber directly, and the subscriber is granted access to the product in their library\. 

### Custom Private Offers with Flexible Payment Scheduler<a name="flexible-private-scheduler-link"></a>

 To create a custom private offer with a flexible payment schedule, see [Flexible Payment Scheduler](flexible-payment-scheduler.md)\. 

## Reporting for Private Offers<a name="reporting-for-seller-private-offers"></a>

Private offers appear on the existing seller reports and in the reports relevant to the offer\. The [Monthly Billed Revenue Report](monthly-billed-revenue-report.md) report is generated every month and has offer visibility and offer ID information\. When an invoice gets generated for a subscriber, it appears in the report, covering the appropriate billing period\.

 The **Offer ID** field contains the unique offer ID generated for the private offer\. It's blank unless the report entry is for a private offer\. The **Offer Visibility** field indicates whether the report entry is a public or private offer\. For all private offers, the entry is marked private\. 