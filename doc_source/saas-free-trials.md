# SaaS free trials<a name="saas-free-trials"></a>

Sellers can create software as a service \(SaaS\) free trial offers in the AWS Marketplace Management Portal \(AMMP\)\. Customers can evaluate software products before making large purchase decisions by using the SaaS free trial option\. After a customer subscribes to your product, your product performs entitlement checks the same way it does for paid customers\.

Each AWS account can only use a free trial for a SaaS product once\. The free usage amount granted during a free trial is not shared across linked accounts in an AWS organization\. Different linked accounts within a single main payer account can create their own individual free trials\.

**Note**  
If you use Seller Data Delivery Service \(SDDS\), you'll receive an [Agreement details trial report](https://docs.aws.amazon.com/marketplace/latest/userguide/supplementary-reports.html) in your Amazon Simple Storage Service \(Amazon S3\) bucket\. The report includes agreement details such as the subscriber name and ID, offer ID, and agreement start and end dates\. As a seller, you'll also receive [Amazon Simple Notification Service \(Amazon SNS\) notifications](https://docs.aws.amazon.com/marketplace/latest/userguide/saas-notification.html) when new subscriptions are created\. Amazon SNS notifications include an `isFreeTrialTermPresent` flag to identify free trial agreements\.

## Creating a SaaS free trial offer<a name="creating-saas-free-trial"></a>

Sellers can create SaaS free trial offers in the AWS Marketplace Management Portal \(AMMP\)\.

**To create a SaaS free trial offer**

1. Sign in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management)\. 

1. On the AWS Marketplace Management Portal, choose either:
   + **Create or manage offers**
   + The **Offers** tab

1. On the **Offers** page, choose the **Public free trials** tab to review all SaaS free trials\. 

1. Choose **Create free trial offer**\. Sellers can create one SaaS free trial offer per each public SaaS product\.

1. For **Offer fundamentals**, select your **Product** and then choose **Next**\.

1. In **Free trial settings**:

   1. Enter the number of days for your **Free trial length \(days\)**\.

      The duration of free trials range from 7–90 days\. 

   1. View the **Product dimensions** from your existing public offer\.

      You can't change the product dimensions for SaaS subscription free trials\.

      You can set the quantity limits per each dimension for SaaS contract free trials, and **Remove** or **Add dimensions**\.

1. View the **Service agreement**\.

   For SaaS subscription free trials, the EULA from the public offer applies to the free trial offer\.

   For SaaS contract free trials, for the **EULA version**, you can select either **Standard contract for AWS Marketplace** or **Custom EULA** and then choose **Review offer**\.

1. Verify and review all information for the offer, and then choose **Create offer**\.

## Cancelling a SaaS free trial offer<a name="cancelling-saas-free-trial"></a>

Sellers can cancel free trial offers at any time from the AWS Marketplace Management Portal\.

To cancel a SaaS free trial offer

1. Sign in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management)\.

1. On the AWS Marketplace Management Portal, choose either:
   + **Create or manage offers**
   + The **Offers** tab

1. On the **Offers** page, select the offer\.

1. Choose **View offer**\.

1. Choose **Cancel offer**\.

After an offer is canceled, active agreements for this offer are active until expiration\. New agreements for a canceled offer can't be created\.