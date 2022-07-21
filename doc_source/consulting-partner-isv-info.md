# Creating a resell opportunity for a consulting partner as an ISV<a name="consulting-partner-isv-info"></a>

As an ISV, you can authorize consulting partners to resell your products by creating a resale *opportunity* for that partner\. You can specify a discount percentage or custom price per product dimension to create a wholesale price for the consulting partner\. The partner can mark up the wholesale price when creating their consulting partner private offer for a buyer\. For more information about consulting partner private offers, see [Extending a private offer based on an opportunity](consulting-partner-info.md#consulting-partner-recurring-discount)\.

**Note**  
If the particular terms of the authorization that you want to create are not possible using the AWS Marketplace Management Portal, you can fill out an * AWS Marketplace Reseller Author form*\. To request and return the form, reach out to your AWS Marketplace channel account manager or send an email message to [mpcustdesk@amazon\.com](mailto://mpcustdesk@amazon.com)\.

The following procedure outlines how ISVs can create an opportunity for a consulting partner\. To use this feature, you must have permissions to use the **Partners** tab in the AWS Marketplace Management Portal\. For more information, see [Policies for AWS Marketplace sellers](detailed-management-portal-permissions.md#seller-managed-policies)\.

**To create a reseller opportunity for a consulting partner as an ISV**

1. Sign in to the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/) with your AWS Marketplace Seller account\.
**Tip**  
Be sure that you are signed out from another AWS account before signing in with your AWS Marketplace Seller account\.

1. Choose the **Partners** tab, and then choose **Create opportunity**\.

1. On the **Opportunity details** page, enter the **Opportunity name** and **Opportunity description**\.
**Note**  
The information you enter in **Opportunity name** and **Opportunity description** will be visible to consulting partners in their seller reports\.

1. For **Resellers**, choose the channel partner \(reseller\) that you want to authorize from the dropdown list\. You can select resellers by name or account ID\.
**Note**  
If a reseller doesn't appear in the list, they may need to register first\. Only registered resellers can be authorized for an opportunity\. For more information, see [Creating a private offer as a consulting partner](consulting-partner-info.md)\.

1. Select which of your **Products** are part of this opportunity\.
**Tip**  
Press and hold down the **Ctrl** key to select multiple products at once\.

1. Choose the **Discount** that you want to apply\. 

   **Discount types** can be issued in multiple ways:
   + **Percentage Discount** – Applies one discount rate \(a percentage\) to all selected products\.
   + **Individual Pricing** – Applies specific discounts to specific products\.
   + **Flexible payment schedule** – Sets a flexible payment schedule for a Channel Partner opportunity\.

1. Select the **Duration** of the opportunity\.

   **Opportunity time length** can be issued in multiple ways:
   + **Single Use** – Applies to one opportunity and is no longer applicable after the channel partner creates the private offer\.
   + **Specific Time Duration** – Lasts for a specific time duration that is no longer applicable after a date selected by the ISV\.
   + **No Set Time Duration** – Lasts until ended by one of the involved parties\.

1. \(Optional\) For SaaS contract products, add or remove custom **Product dimensions** and modify the **Additional usage fees** to customize your opportunity\.

1. \(Optional\) Set one or more **Buyer account IDs** to specify that the opportunity is only for those buyers\.

1. \(Optional\) Select the **End User License Agreement \(EULA\)** version or upload the EULA to be included in the opportunity\.

1. \(Optional\) Select the **Reseller Contract for AWS Marketplace \(RCMP\)** or upload a custom contract to be included in the opportunity\.

1. Select **Review opportunity**, and make sure that the information is correct\.

1. Select **Create opportunities** to finalize the opportunity and authorize the consulting partners\.

   The **Opportunities created** table is updated to display relevant opportunity details including **Opportunity name**, **Product name**, **Reseller name**, **Discount**, **Created date**, and **Status**\.

After opportunities are created, you can't extend their dates\. However, you can revoke an opportunity and re\-create it at any time\. When you revoke an opportunity, new offers can't make use of that discount\. Any existing offers are unaffected and retain their opportunity discount\.

You can also clone an opportunity by selecting the opportunity and then choosing **Clone**\. This will prepopulate everything and then you can edit fields

You can add up to 10 email addresses to receive notifications when a channel partner uses resell authorization\. To set up email notifications, see [Manage notifications](notifications.md#manage-notifications)\.