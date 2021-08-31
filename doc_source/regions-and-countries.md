# Regions and countries for your AWS Marketplace product<a name="regions-and-countries"></a>

When you create a product in AWS Marketplace, you choose the AWS Regions where it is available\. You also choose the countries where buyers can purchase your product from\. These two properties are similar, but they are not the same\. For example, a buyer might be located in, and purchasing from, the United States but is installing your product in the Europe \(Frankfurt\) Region\. In order for this buyer to purchase your product, you must include both the United States in your list of countries, and the Europe \(Frankfurt\) Region in your list of Regions\.

## AWS Regions<a name="product-regions"></a>

 When creating or editing server or machine learning product information, you can limit your product to specific AWS Regions where your users can install and use the product\.

 For server products, including Amazon Machine Image \(AMI\)\-, container\-, and AWS CloudFormation\-based products, you can select specific Regions where the product is available\. You can also choose to automatically make your product available in new US Regions, non\-US Regions, or all Regions as they become available\.

 For machine learning products, you can either select specific Regions, or all Regions including future Regions as they become available\.

 For more information about AWS Regions, see [ AWS service endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the AWS General Reference\.

## Countries<a name="product-countries"></a>

 By default, your product is available to buyers in all countries where AWS Marketplace is available\. For new and existing server and software as a service \(SaaS\) products, you can control product availability in specific countries for tax, compliance, support, or marketing purposes\.

 There are exceptions to this functionality:
+  **Previous purchases** – After updating your product with a new list of countries, buyers that have already subscribed to your product will still have access while their subscription is active\.
+  **Private offers** – When you limit your product to buyers in specific countries, it does not limit private offers\. When you create a private offer to a specific buyer, it is available to that buyer, even if they are in a country that you did not include in your specified countries\.

**Note**  
Customer eligibility is determined at an AWS linked account level\. For more information, see [How does AWS determine the Location of your account?](https://aws.amazon.com/tax-help/location/)  
Customers that share their entitlement can only activate the entitlement in a region you have allowed\. For more information about managing entitlements, see [Sharing subscriptions in an organization](https://docs.aws.amazon.com/marketplace/latest/buyerguide/organizations-sharing.html) in the *AWS Marketplace Buyer Guide*\.