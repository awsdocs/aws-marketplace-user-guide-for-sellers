# Private offers<a name="private-offers-overview"></a>

Private offers are a purchasing program that allows sellers and buyers to negotiate custom prices and end user licensing agreement \(EULA\) terms for software purchases in AWS Marketplace\.

**Tip**  
You can negotiate EULA terms for each private offer, or you can use or amend [standardized license terms](standardized-license-terms.md) to simplify the procurement process\.

## How private offers work<a name="private-offer-how-it-works"></a>

You can create and manage all of your private offers from the **Offers** page in the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management)\. You specify the product that the offer is being made for and the AWS account ID \(or IDs\) for the buyer you're creating the offer for\. AWS Marketplace Management Portal generates a unique ID and URL for the offer\. For instructions on creating private offers, see [Consulting partner creates](https://s3.us-west-2.amazonaws.com/external-mp-channel-partners/Consulting+Partner+Creates+(1).pdf)\. 

 When you create a private offer, you can extend the offer to up to 25 accounts\. The offer is visible only to the accounts that you create the offer for\. Buyers can't view the offer unless you extend the offer to either their linked account or to their master payer account\. You can't force service limits in the offer, so the buyer can use as much of your product at the negotiated prices as they want, unless the product already has a limit\.

AWS Marketplace buyers can access third\-party financing for private offers\. For more information, see [Customer financing is now available in AWS Marketplace](https://s3.us-west-2.amazonaws.com/external-mp-channel-partners/Financing+External+Briefing+Document+Customer+Facing.pdf)\.

**Note**  
The buyer isn't notified that you created a private offer\. You can provide the URL for the custom offer to the buyer, or they can navigate to your product through AWS Marketplace\.

When the buyer navigates to your product's subscription page, a banner indicates that a private offer is available\. After the buyer accepts the offer, they're invoiced for the purchase using the same portal tools used for all AWS Marketplace transactions\. Accepted offers become *agreements*, and are also referred to as *contracts* or *subscriptions*\.

For SaaS contract and SaaS contract with consumption products, you can offer upgrades and renewals on agreements that were made when buyers accepted private offers\. For example, you can do this to grant new entitlements, offer pricing discounts, adjust payment schedules, or change the end user license agreement \(EULA\) to use standardized license terms\. For more information, see [Private offer upgrades and renewals](private-offers-upgrades-and-renewals.md)\.

Private offers are tracked in seller reports\. For more information, see [Reporting for private offers](#reporting-for-seller-private-offers) and the [Seller reports guide](https://s3.us-west-2.amazonaws.com/external-mp-channel-partners/Seller+Reports+Guide.pdf)\.

### Private offer experience for buyer<a name="private-offer-sub-experience"></a>

After you create a private offer and notify the potential buyer, they will have steps they must perform to accept the offer\. For more information about the buyer experience for private offers, see [Private offers](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-private-offers.html) in the *AWS Marketplace Buyer Guide*\.

To receive the terms of the offer, the buyer must accept the offer before the offer expiration date\. After the offer expires, the terms are no longer valid\. You must re\-create the private offer for the buyer to accept the terms\. As the seller, you can provide a URL to the fulfillment page for the offer, or the customer can navigate to your product page on AWS Marketplace and choose the link in the banner to view the private offer\.

## Private offers through consulting partners<a name="consulting-private-offers"></a>

If you are a consulting partner, you can negotiate special terms with an ISV to offer their products to buyers\. With this type of offer, you are listed as seller\-of\-record\.

For more information, see [Consulting partner private offers](consulting-partner-offers.md)\.

## Notes about private offers<a name="private-offer-limitations"></a>

When working with private offers, keep the following in mind:
+  You can't create private offers for second party \(2P\), AMI monthly, SaaS redirect, or AMI\-based delivery using AWS CloudFormation products, or for limiting customer usage\. 
+ For private offers with the flexible payment scheduler, it is possible to break upfront commitments into multiple payments over time if buyers are on invoicing terms with AWS\.

## Supported product types<a name="supported-products-private-offers"></a>

Currently, AMI and SaaS products are supported for private offers\.

### Private offers for AMI products<a name="ami-private-offers"></a>

You can provide private offers pricing for AMI contracts\. The offer can be any custom duration in days, up to 3 years \(1,095 days\)\. License entitlements begin on the date the buyer accepts the private offer\. For AMI private offers with flexible payment schedules, you can set the number of instances agreed to in the contract, for the duration of the contract\. You can also define a custom hourly price for those same instances if the buyer uses more\. 

### Private offers for SaaS products<a name="saas-private-offers"></a>

SaaS private offer products can't change the pricing level for a given pricing tier based on timing\. For example, an offer can't charge $0\.80/hour for three months and then change pricing to $0\.60/hour thereafter for the same pricing tier\. For SaaS contracts, private offers don't monitor usage\.

Buyers can manually upgrade to new contracts levels at any time, but it is up to the independent software vendor \(ISV\) to define contract tiers, enforce service limitations, and advise buyers to manually upgrade to higher contract tiers when needed\. The duration dimensions that appear on a SaaS contract private offer matches the durations enabled when the public product listing was created\. For SaaS contracts, this can be 1 month, 1 year, 2 years, and/or 3 years\. 

## Offer submission process<a name="offer-submission-process"></a>

 You can create simple private offers using the AWS Marketplace Management Portal using the following procedure\. 

**To create a private offer**

1.  Sign in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management) and choose **Offers**\. 

1. On the **Manage Private Offer** page, choose **CREATE AN OFFER**\. 

1. On the **Create Private Offer** page, select the product from the drop\-down list and enter the AWS account ID \(or IDs\) of the AWS Marketplace buyer\. If your buyer is paying for the product in installments, select **Allow buyers to pay for this product in installments**\. Verify the information that you entered and then choose **NEXT**\. 
**Note**  
Selecting **Allow buyers to pay for this product in installments \(ISV only\)** enables you to offer your buyer a payment schedule with annual payments that aren't evenly distributed, multiple payments for a multi\-year deal, or quarterly payments\. Buyers must be on invoicing terms with AWS to receive a flexible payment schedule on their private offer\. For more information, see [Flexible payment scheduler](flexible-payment-scheduler.md)\.

1. On the **Create an Offer** page, verify the product name and buyer ID\.

1. If the product offering is for an AMI hourly or AMI annual pricing model, specify the **Contract duration**, by choosing a radio button or entering a custom duration in number of days\.
**Note**  
 The duration of the offer can be up to 1,095 days\. 

1.  In **Input offer price**, enter the pricing information that you negotiated with the customer\. If you have installment payments for the private offer, specify the number of units and the payment schedule for the contract duration\. For more information about installment payments, see [Flexible payment scheduler](flexible-payment-scheduler.md)\. 

1. In **Upload End User License Agreement**, select from available options or upload your EULA PDF file\.

1. In **Offer Expiration and Acceptance Date**, enter the number of days that the offer is valid for\.
**Note**  
This is the number of days after the customer accepts the offer that the terms of the agreement are active\. After the number of days has lapsed, the price and EULA revert to the terms provided in the public offering\. 

1. For **Buyer needs to accept the offer by**, enter the date when the offer is no longer available if not accepted\.
**Note**  
This is the date that the offer becomes null and void\. On that date, the buyer won't be able to accept the offer under the custom terms that you have specified\. 

1.  Choose **REVIEW OFFER**\. 

1.  On the **Review Offer** page, verify the offer information and the PDF file, and then do one of the following:
   +  If the offer is correct, choose **EXTEND OFFER**\. 
   +  If the offer is incorrect, choose **EDIT OFFER** and make any required changes\. 

The offer should appear on the **Manage Private Offer** page in approximately 45 minutes\. To view the offer, sign in to the AWS Marketplace Management Portal and choose **Private Offer**\. This opens the **Manage Private Offer** landing page\. 

## Reporting for private offers<a name="reporting-for-seller-private-offers"></a>

Private offers appear on the existing seller reports and in the reports relevant to the offer\. The [Monthly billed revenue report](monthly-billed-revenue-report.md) is generated every month and has offer visibility and offer ID information\. When an invoice is generated for a buyer, it appears in the report covering the appropriate billing period\. For more information, see the [Seller reports guide](https://s3.us-west-2.amazonaws.com/external-mp-channel-partners/Seller+Reports+Guide.pdf)\. 

 The **Offer ID** field contains the unique offer ID generated for the private offer\. It's blank unless the report entry is for a private offer\. The **Offer Visibility** field indicates whether the report entry is a public or private offer\. For all private offers, the entry is marked private\. 