# Private offer upgrades and renewals<a name="private-offers-upgrades-and-renewals"></a>

For SaaS contract and SaaS contract with consumption products, you can offer upgrades and renewals by using a private offer on any active agreements\. For example, you can do this to grant new entitlements, offer pricing discounts, adjust payment schedules, or change the end user license agreement \(EULA\) to use [standardized license terms](standardized-license-terms.md)\. You can also change the number of units and payment schedule, and add a custom end date\. 

The difference between an *offer* and an *agreement* is whether the buyer accepted its terms:
+ An **offer** is a set of terms for a buyer's use of a product\. Offers can be public or private\. 
+ An **agreement ** is an offer that a buyer accepted\. Agreements include purchased and free products that a seller made available via a public or private offer\. 

This page describes how to amend active agreements for SaaS contract and SaaS contract with consumption products\.

This feature is available to all AWS Marketplace sellers, including independent software vendors \(ISVs\) and consulting partners\. You can't amend an agreement to specify a seller of record that's different from the seller of record from the original agreement\. 

To use this feature, you must have permissions to use the **Agreements** tab in the AWS Marketplace Management Portal\. For information, see [Permissions for AWS Marketplace sellers](detailed-management-portal-permissions.md#seller-ammp-permissions)\.

## Supported product types<a name="private-offers-upgrades-and-renewals-supported-products"></a>

Currently the following product types support private offer renewals and upgrades:
+ SaaS contracts
+ SaaS contracts with consumption

## Submission process for upgrades and renewals<a name="private-offers-upgrades-and-renewals-process"></a>

You can create private offer upgrades and renewals from the AWS Marketplace Management Portal by using the following procedure\. 

**To create private offer upgrades and renewals**

1.  Sign in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management) and choose **Agreements**\. 

1. On the **Agreements** page, create an upgrade or renewal private offer in one of the following ways:
   + Choose a check box next to an agreement, and then choose **Create agreement\-based offer**\.
   + Choose an agreement ID to view the agreement details\. On the **Agreement summary** page, review the agreement's existing information and terms to verify that this is the agreement you want to amend, and then choose **Create agreement\-based offer**\. 

1. On the **Agreement offer details** page, enter a custom offer name\.
**Tip**  
Entering descriptive custom offer names can help you distinguish between your active offers on the **Offers** page\. Custom offer names are also visible to buyers\.  
AWS recommends that you specify a custom offer name that includes any additional identifying details, such as your own IDs and purchase order numbers\. Using high\-level descriptions like **upgrade** or **renewal** and custom company names are also recommended\. Don't use any personally identifiable data \(for example, first or last names, phone numbers, or addresses\)\. You can enter up to 150 characters for this field\. 

1. Edit the information for any dates, dimensions, payment schedule, and EULA that you want to change\. Then choose **Next**\.

1. On the **Review and create** page, review the information\. When ready, choose **Create agreement\-based offer**\.

The new private offer appears on the **Manage Private Offer** page in approximately 45 minutes\. To view the offer, sign in to the AWS Marketplace Management Portal and choose **Offers** to open the **Manage Private Offer** page\. 

Similar to the process for creating a private offer, the buyer isn't notified that you created a new private offer\. Instead, you provide the URL for the new private offer to the buyer\. From there, the buyer has the option to accept it or to continue to operate under the original agreement:
+ If the buyer accepts the private offer upgrade or renewal, the new agreement takes effect immediately and the agreement is listed on the **Agreements** page in the AWS Marketplace Management Portal\. Any remaining scheduled payments from previous agreements are cancelled\.

  Buyers accept agreement\-based private offers the same way they accept private offers\. For more information about the buyer experience for private offers, see [Private offers](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-private-offers.html) in the *AWS Marketplace Buyer Guide*\.
+ If the buyer doesn't accept the private offer upgrade or renewal before it expires, the original agreement remains in effect with no changes\. 

## Reporting for upgrades and renewals<a name="private-offers-upgrades-and-renewals-reporting"></a>

Upgrade and renewal private offers appear on the existing seller reports and in the reports relevant to the offer\. The [Daily customer subscriber report](daily-customer-subscriber-report.md) report and [Daily business report](daily-business-report.md) report are generated daily\. The [Monthly billed revenue report](monthly-billed-revenue-report.md) report is generated monthly\.

In the Daily customer subscriber report, the **Subscription intent** field indicates whether the report entry is a new private offer\. The **Previous offer ID** field indicates the ID of the offer that preceded the new offer, if one exists\. For all private offers, the entry is marked private\. 

Currently, agreements data is not shown in data feeds\.