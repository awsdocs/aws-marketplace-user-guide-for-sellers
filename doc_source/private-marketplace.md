# Private marketplaces<a name="private-marketplace"></a>

With a private marketplace, you can control which products your users can procure from AWS Marketplace\. It is built on top of AWS Marketplace, and enables your IT administrators to create and customize a curated digital catalog of approved independent software vendors \(ISVs\) and products that conform to their in\-house policies\. Your business users and engineering teams can find, buy, and deploy products from your private marketplace, and ensure that all available products comply with your organization’s policies and standards\. 

Your private marketplace is shared across [AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/)\. AWS Organizations enables you to create a series of accounts linked for permissions and payments\. When controls are initiated for your AWS Organizations, they are applied to every account in the organization\. The private marketplace experience is modeled on AWS Organizations\. Your IT administrators can also apply company branding to your private marketplace with your company’s logo, messaging, and color scheme\. 

You have full visibility into your AWS Marketplace spending by product, and can also find full subscription details\. Private marketplace provides you with a broad catalog of products to choose from, in addition to fine\-grained control of those products\. 

**Notes**  
Currently, support for [data products](buyer-data-products.md) in private marketplaces is limited\. The private marketplace banner isn't shown on the product listing pages for data products, so you can't add data products from these pages\. However, you can still allow private marketplace users to subscribe to data products\. To do so, add data products to your private marketplace from the administrator's page on the Private Marketplace portal\. 
You can't add [desktop products](buyer-desktop-products.md) to a private marketplace\. 

## Viewing product detail pages<a name="product-detail-page-visit"></a>

Members of your organization can only subscribe to products you have added to your private marketplace\. They can browse and see the detail page for any product, but the subscription button is enabled only for products you have added to your private marketplace\. If a product is not currently in your private marketplace, the user sees a red banner at the top of the page\.

If software requests are enabled, organization members can choose **Create request** on the product details page\. When organization members choose **Create request**, they submit a request to the administrator to make the product available on your private marketplace\.

## Subscribing to a product in a private marketplace<a name="subscribing-to-a-product-in-a-private-marketplace"></a>

To subscribe to a product in your private marketplace, navigate to the product's details page and choose **Continue**\. This redirects you to the product's subscription page\. On the subscription page, you can make your configuration selections, and then choose **Subscribe**\.

If the product is not approved in your private marketplace, **Subscribe** isn't available\. A red banner at the top of the page indicates that the product is not currently approved for procurement\. If software requests are enabled, you can choose **Create request** to submit a request to your administrator requesting that the product be added to your private marketplace\.

## Adding a product to your private marketplace<a name="request-adding-a-product-to-your-private-marketplace"></a>

 You can request that your administrator add a product that is not in your private marketplace\. To make a request, navigate to the product's details page, choose **Create request**, enter a request to your administrator that the product be added to your private marketplace, and then submit your request\. To track your request status, on the left dropdown menu, choose **Your Private Marketplace Requests**\.