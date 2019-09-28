# Pricing for SaaS Subscriptions<a name="saas-subscriptions"></a>

 For SaaS subscriptions, AWS Marketplace bills your customers based on the metering records that you send to us\. 

 To add a product using the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour/), select the **Products** tab and choose **SaaS**\. Then, from **Create SaaS Product** choose **SaaS Subscriptions** from the dropdown menu\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-pricing-subscriptions-screenshot.png)

 To describe your product and pricing model, complete the following views:
+ **Onboarding** – Banking and tax information for your product
+  **General** – Product name, URL, and other metadata to make your product discoverable in AWS Marketplace
+  **Pricing** – How you will price your product
+  **Notes** – \(Optional\) Specific notes or instructions to the AAWS Marketplace team for publishing your product

To set your pricing, select the category that best describes your product’s pricing\. The pricing category appears to customers on the AWS Marketplace website\. You can choose from bandwidth \(GBps, MBps\), data \(GB, MB, TB\), hosts, requests, tiers, or users\. If none of the predefined categories fit your needs, you can choose the more generic **units** category\. 

Next, define your pricing dimensions\. Each pricing dimension represents a feature or service that you can set a per\-unit price for\. Examples of dimensions include users, hosts scanned, and GB of logs ingested\. You can define up to 24 dimensions\. For each dimension you define, you must add the following information: 
+ **Dimension API Name** – The API name used when sending metering records to the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html)\. This name indicates which dimension your customer used\. This name is visible in billing reports\. The name doesn't need to be reader\-friendly because you're the only one with access to your reports\. After you set the name, you can't change it\. 
+ **Dimension Description** – The customer\-facing statement that describes the dimension for the product\. The description \(administrators per hour, per Mbps bandwidth provisioned, etc\.\) can be no more than 70 characters and should be user\-friendly\. After the product is published, you can't change this description\. 
+ **Dimension Price** – The software charge per unit for this product\. This ﬁeld supports three decimal places\. 