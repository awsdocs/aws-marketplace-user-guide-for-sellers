# Private Offers<a name="private-offers"></a>

 AWS Marketplace Seller Private Offers is a purchasing program that allows an AWS Marketplace customer and an AWS Marketplace seller to negotiate custom price and end user licensing agreement \(EULA\) terms for a software purchase\. You must be enrolled in the [AWS Marketplace Enhanced Data Sharing Program](enhanced-data-sharing-program.md) and contact your AWS Marketplace representative to participate in this program\. 

In addition to Private Offers, there are also Enterprise Contract Private Offers, which use the Enterprise Contract EULA\. Many private offers can be handled directly by the seller using the **Offers** tab in the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour) \(AMMP\)\. 

 Some private offers may require the assistance of the AWS Marketplace Customer Desk \(mpcustdesk@amzon\.com\)\. These offers might include custom private offers that can’t be defined using AMMP or private offers that involve multiple parties, such as a consulting partner creating a private offer\. 

 As the seller, you use the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour) \(AMMP\) on the **Offers** tab to create the private offer\. You specify the product for which the offer is being made and the payer account's customer ID for the customer or customers you are creating the offer for\. AMMP generates a unique ID and URL for the offer\. The customer is not notified that you created a private offer\. You can provide the link to the customer, or the customer can navigate to your product through AWS Marketplace\. On your product page, after the customer navigated to the subscription page, they will see a banner that indicates a private offer is available\. After the customer accepts the offer, they are invoiced for the purchase using the same portal tools used for all AWS Marketplace transactions\. 

 In AWS Marketplace reports, there are two columns that help you identify private offer transactions\. The **Offer ID** column contains the identifier for the offer signed by the customer\. The **Offer Visibility** column indicates whether the offer is public or private\. The Monthly Billed Revenue report is generated every month and has Offer Visibility and Offer ID information\. When an invoice gets generated for a customer it will appear in the Monthly Billed Revenue report covering the appropriate billing period\. 

## Offer Submission Process<a name="offer-submission-process"></a>

 This process is for creating relatively uncomplicated private offers\. If you are creating a private offer with any of the following, you must follow the [Custom Private Offers](#custom-private-offers) process: 
+  Bring Your Own License \(BYOL\) 
+  Upfront billing for a suite of products 
+  Unlimited access to a license for one cost 

**Note**  
 Private offers can't be created for 2P, AMI Monthly, SaaS redirect, or AMI\-based delivery using AWS CloudFormation products, or for limiting customer usage\. 

 To create a private offer: 

1.  From the AMMP landing page, choose the **Offers** tab\. 

1.  On the **Manage Private Offer** page, choose **CREATE AN OFFER**\. 

1.  On the **Create Private Offer** page, use the drop\-down list to select the product and type the AWS account ID of the AWS Marketplace customer\. If you are allowing your customer to pay for the product in installments, select **Allow buyers to pay for this product in installments \(ISV only\)**\. Verify the information you entered is correct, and then choose **NEXT**\. 

    **Note**: Selecting **Allow buyers to pay for this product in installments \(ISV only\)** allows you to offer your customer a payment schedule with annual payments that are not evenly distributed, multiple payments for a multi\-year deal, or quarterly payments\. For instructions on configuring your private offer for installment payments, see [Flexible Payment Scheduler](flexible-payment-scheduler.md)\. 

1.  On the **Create an Offer** page, verify the product name and buyer ID are correct\. Under **Step 1: Input Offer price**, enter the pricing information you negotiated with the customer\. 

1.  Under **Step 2: Upload End User License Agreement**, drag and drop or upload the EULA PDF file\. 

1. Under **Step 3: Offer Expiration and Acceptance Date**, in **This offer switches back to public offer after \_\_\_\_ Days**, enter the number of days for which the offer is valid\. **Note**: This is the number of days after the customer accepts the offer that the terms of the agreement are active\. After the number of days has lapsed, the price and EULA revert to the terms listed in the public offering\. 

1.  Under **Step 3: Offer Expiration and Acceptance Date**, in **Buyer needs to accept the offer by**, enter the date the offer will no longer be available if not accepted\. **Note**: This is the date that the offer will become null and void, and the customer is no longer be able to accept the offer under the custom terms you’ve specified\. 

1.  On the **Create an Offer** page, choose **REVIEW OFFER**\. 

1.  On the **Review Offer** page, verify the offer information was correctly entered, and review the PDF file\. 

   1.  If the offer is correct, choose **EXTEND OFFER**\. 

   1.  If the offer is incorrect, choose **EDIT OFFER**, and then make any required changes\. 

 You have now completed the offer submission process\. The offer should appear on the **Manage Private Offer** page in approximately 45 minutes\. To view the offer, from AMMP, choose the **Private Offer** tab\. This will open the **Manage Private Offer** landing page\. 

## Custom Private Offers<a name="custom-private-offers"></a>

 Custom Private Offers are offers that are manually published by the AWS Marketplace Business Development \(BD\) Operations team\. This process must be used to create private offers for Bring Your Own License \(BYOL\), billing upfront for a suite of products, and unlimited access to a license for one cost contracts\. The steps for each private offer type are different\. The BD team will contact you if they need information specific to your private offer request\. 

 To request a custom private offer, email the AWS Marketplace Customer Desk \(**mpcustdesk@amazon\.com**\) team, or work with your Customer Advisor or Business Development contact\. The team will email you instructions, including forms that you must complete and return for review\. After you have returned the completed forms, the team will review the offer to ensure it conforms with existing billing mechanisms and meets the minimum deal threshold\. If approved, the process takes from 5\-7 business days from first contact with AWS Marketplace\. When your private offer is published on AWS Marketplace, the AWS Marketplace Customer Desk team will email you a link to the private offer and the offer will be visible to the buyer in their AWS Marketplace portal\. 

 These are the process milestones: 

1.  **Determine the product listing that will be used to publish the private offer** If the listing is not public, then the AWS Managed Catalog Operations \(MCO\) team will create a new listing from which the offer is built\. You need to complete the Product Load Form and submit it to AWS Marketplace Customer Desk \(**mpcustdesk@amazon\.com**\)\. The listing will be published using the standard publishing process\. This adds another 3\-5 business days to build the offer\. 

1.  **Agree to offer details with your customer** You and the customer must agree to new pricing dimensions or the EULA that constitutes the private offer\. For custom private offers that are manually published by AWS, a custom transaction request form \(TRF\) is required to delineate the details of the offer\. If the customer uses the normal subscription invoicing process, you must sign the TRF but the customer does not\. If the customer uses non\-standard invoicing, you and the customer must sign the TRF\. To get the TRF, or to submit the completed TRF, email the AWS Marketplace Customer Desk \(**mpcustdesk@amazon\.com**\) or contact your Customer Advisor or Business Development contact\. 

1.  **Private offer is published after your completed TRF is received** Your private offer will be published based on the listing in milestone 1 and the subscription detail in the TRF\. The offer will appear on the customer’s **AWS Marketplace Manage Private Offer** page\. 

1.  **Customer subscribes to private offer** The customer will see a banner that indicates a private offer available is available\. After the customer accepts the offer, they are invoiced for the purchase using the same tools used for all AWS Marketplace transactions\. If the offer used non\-standard invoicing, then AWS will bill the customer directly and the customer will be granted access to the product in their library\. 

 Custom private offers that go through this process will appear in reports just like other private offers\. 

## Custom Private Offers with Flexible Payment Scheduler<a name="flexible-private-scheduler-link"></a>

 To create a custom private offer with a flexible payment schedule, see [Flexible Payment Scheduler](flexible-payment-scheduler.md)\. 

## Experience for the Buyer of a Seller Private Offer<a name="experience-for-the-buyer-of-a-seller-private-offer"></a>

 As you create and execute a private offer, you and the customer will have steps to complete\. The experience for the customer is: 

1.  A customer with a private offer can access the offer directly by the link provided to them\. The link might come from the seller of record or the AWS Customer Desk, or through the banner at the top of the page for the product the private offer is for\. The link takes the customer to the product fulfillment page, which requires the customer to authenticate with credentials \(root IAM user\) for the AWS account the offer was extended to \- the payor account for the customer\. Private offers must be accessed from the AWS Marketplace page\. Customers can also find the most recent private offer by visiting the public product's detail page and choosing **Continue** to access the product's fulfillment page\. After authenticating with the account’s credentials, the customer sees a blue banner indicating they have a private offer\. Follow the link in the banner to access the most recently created private offer for that product\. 

1.  When the customer is ready to accept the private offer, the customer chooses **Accept Offer** in the pricing box\. From that point until the expiration date noted in the pricing box, any running instances, annual software purchases, metering records, or contract purchases, will be charged at the rates shown in the private offer\. Customer use of the software does not change from customer usage of a product with a public offer\. Whether a deployed instance or a new instance, customer usage will be charged at the new private offer price once the offer is accepted\. 

 Subscribing to the private offer does not require launching a new instance of the software\. Accepting the private offer will modify the price of existing instances to correspond to the private offer price\. If a product offers 1\-click launch, the customer can deploy a new instance of the software\. If a product defaults to 1\-click launch, the customer can accept a private offer without launching a new instance by choosing **Manual Launch** on the fulfillment page\. As with all AWS Marketplace products, the customer can use the EC2 console to deploy more instances\. 

## Reporting for Seller Private Offers<a name="reporting-for-seller-private-offers"></a>

 AWS Marketplace Seller Private Offers appear on the existing seller reports available to you, and are listed in the reports relevant to the offer\. The **Offer ID** and **Offer Visibility** fields contain information about the offers\. 

![\[Example of Private Offers Reporting\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/private-offers-07.png)

 The **Offer ID** field contains the unique offer ID generated for the private offer in step 4 of the offer submission process\. It is blank unless the report entry is for a private offer\. The **Offer Visibility** field indicates whether the report entry is a public or private offer\. For all AWS Marketplace Seller Private Offers, the entry is marked private\. 

## Frequently Asked Questions<a name="frequently-asked-questions"></a>

### Product Listings<a name="product-listings"></a>

 **Q\. Which product types are not supported by the Custom Private Offer program?** 

 AMI Monthly, products delivered using AWS CloudFormation templates, 2P products, and SaaS Redirect products\. 

 **Q\. How do I know which product listing to use? Can the product listing I want to use support a custom private offer? ** 

 Contact the AWS Marketplace Customer Desk \(**mpcustdesk@amazon\.com**\), your business development contact, or your customer advisor\. 

### Forms and Buyer Information<a name="forms-and-buyer-information"></a>

 **Q\. Can I use only the customer’s AWS account on the TRF? ** 

 Yes\. AWS Marketplace can find all linked AWS accounts from just an AWS account that is a payer account\. Some customers have multiple payer accounts, so confirm the account structure with the customer early in your discussions\. 

 **Q\. What does the customer need to know about master payer accounts and how to subscribe to a custom private offer?** 

 The master payer account must subscribe to the private offer first\. This ensures that the private pricing stays in sync across AWS Marketplace systems and the linked accounts\. 

### Private Offer Publishing<a name="private-offer-publishing"></a>

 **Q\. How long will it take to publish my custom private offer?** 

 Depending on the offer requirements, expect between five and seven business days\. 

### General Questions<a name="general-questions"></a>

 **Q\. Are Private Offers available in the AWS GovCloud \(US\) region?** 

 Yes, Private Offers are available for the AWS GovCloud \(US\) region provided that the users have AWS GovCloud \(US\) accounts\. 

 **Q\. I created an AWS Marketplace Seller Private Offer listing, but my customer is not getting the terms and conditions I provided in the offer\. Why?** 

 To receive the terms of the offer, the customer must accept the offer\. You can provide a URL to the fulfillment page for the offer, or the customer can navigate to your product page on AWS Marketplace and choose the page banner that indicates there is a private offer available\. 

 **Q\. Are instance sizes in the same order on the Private Offer page as they are on the product details page?** 

 Not necessarily\. The order of instance size may be different than they appear on the product detail page\. As you enter prices for instance size, verify the pricing you set if for it\. 

 **Q\. I created an offer but cannot view the fulfillment page\. Why?** 

 By default, only the customer can see the fulfillment page for the private offer\. To view the fulfillment page, you must include your account when you create the offer\. 

 **Q\. Is there a limit to the number of AWS accounts I can add to an offer?** 

 Yes\. You can add 10 AWS accounts that are payer accounts to an offer\. 

 **Q\. Does an AWS Marketplace Seller Private Offer listing enforce service limits?** 

 No\. A buyer \(customer\) can use or deploy as much of a service at the negotiated rate unless the ISV limits the service in some way, such as by limiting usage based on the reported entitlements for SaaS contracts products\. 

 **Q\. Can an AWS Marketplace Seller Private Offer listing update tiered pricing levels for SaaS metering automatically?** 

 No\. AWS Marketplace Seller Private Offer listings cannot change the pricing level for a given pricing tier based on timing\. For example, an offer cannot charge $0\.80/hour for three months and then change pricing to $0\.60/hour thereafter for the same pricing tier\. 

 **Q\. Can an AWS Marketplace Seller Private Offer listing upgrade contracts for SaaS Contracts products automatically?** 

 For SaaS contracts, Private Offer listings do not monitor usage\. Buyers are able to manually upgrade to new contracts levels at any time, but it is up to the ISV to define contract tiers, enforce service limitations, and advise customers to manually upgrade to higher contract tiers when needed\. 

 **Q\. What is the difference between Seller Private Offers and Seller Private Offers for AWS MP Channel?** 

 Seller Private Offers are self\-service\. They can be created by the seller without AWS Marketplace involvement\. Seller Private Offers for AWS MP Channel is used to create a custom Seller Private Offer that requires AWS Marketplace engagement and support\. Creating an offer that has multiple sellers of record also requires AWS Marketplace engagement and support\. 

 **Q\. What does the release of Seller Private Offers for AWS MP Channel mean for consulting partners?** 

 Seller Private Offers for AWS MP Channel enables consulting partners to receive custom pricing and EULA terms through AWS Marketplace\. Through the use of Private Offer for MP Channel, consulting partners may consolidate more of their purchase on their AWS bill, take advantage of consolidated billing, cost analytics, and renewal management\. Consulting partners can lower their software costs while buying through AWS Marketplace\. If desired, consulting partners can also receive a specific EULA to cover any required custom terms\. 

 **Q\. Do I need to make any changes to billing settings of my account?** 

 Yes\. You must set your billing preferences to invoicing, not credit card billing\. 

 **Q\. How do I get set up on Net Invoicing Terms?** 

 Contact your AWS Marketplace Channel Account Manager at **awsmp\-cam@amazon\.com** or **mpcustdesk@amazon\.com**\. 

 **Q\. Can I use Seller Private Offers for AWS MP Channel from the EC2 Console? ** 

 No, all Seller Private Offers for AWS MP Channel must start on the AWS Marketplace site to review specific terms\. After you subscribe to an AMI\-based product, you can use the AMI ID to deploy the product from the EC2 console\. After a private offer is accepted, any products initially deployed through the EC2 console will receive the new price\. 

 **Q\. How do I check my usage of products purchased with a Seller Private Offers for AWS MP Channel?** 

 Products with a private offer show up like any other AWS Marketplace product on your monthly bill\. You can also use detailed billing to view your usage\. Each will have a line item corresponding to each type of usage\. The product title will be appended with “\- Private Offer\.” 

 **Q\. Does a Seller Private Offers for AWS MP Channel listing enforce service limits?** 

 Seller Private Offers for AWS MP Channel listings do not enforce a service limit\. A consulting partner can use or deploy as much of a service at the negotiated rate unless the seller limits the service in some way, such as by limiting usage based on the reported entitlements for SaaS contracts products\. 

 **Q\. Can a Seller Private Offers for AWS MP Channel listing automatically update tiered pricing levels for SaaS metering?** 

 No\. Seller Private Offers for AWS MP Channel listings cannot change the pricing level for a given pricing tier based on timing\.  For example, an offer cannot charge $0\.80/hour for three months and then change pricing to $0\.60/hour thereafter for the same pricing tier\. 

 **Q\. Can a Seller Private Offers for AWS MP Channel listing automatically upgrade contracts for SaaS Contracts products?** 

 For SaaS contracts, Private Offers for AWS MP Channel listings do not monitor usage\. Consulting partners can manually upgrade to new contract levels at any time, but it is up to the seller to define contract tiers, enforce service limitations, and advise customers to manually upgrade to higher contract tiers when needed\. 

 **Q\. I am having trouble with creating my offer\. How do I get support?** 

 Contact the AWS Marketplace Customer Desk team at **mpcustdesk@amazon\.com**\. 

 **Q\. I want to create an offer and cannot figure out how to do it through the AMMP\. How do I get support?** 

 Contact the AWS Marketplace Customer Desk \(**mpcustdesk@amazon\.com**\) team\. 

 **Q\. I am having trouble or have questions with my offer\. How do I get support?** 

 Contact the AWS Marketplace Customer Desk team at **mpcustdesk@amazon\.com** or an AWS Marketplace Channel Account Manager at **awsmp\-cam@amazon\.com**\. 