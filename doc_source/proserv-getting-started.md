# Getting started with professional services products<a name="proserv-getting-started"></a>

 This topic describes how to get started with a professional services product, and goes through the steps to create your first product, and how to offer it to your customers\. Your product definition tells your customers about the services that you offer and why they should select your company for those services\. AWS Marketplace then allows them to contact you\. You agree on a contract, and then you create a private offer that allows them to purchase your services for a fixed cost\.

**Topics**
+ [Prerequisites](#proserv-prereqs)
+ [Creating a professional services product](#proserv-create)
+ [Creating private offers](#proserv-create-offer)
+ [Editing product information](#proserv-edit-product)
+ [Editing product pricing](#proserv-edit-pricing)
+ [Editing product visibility](#proserv-edit-visibility)
+ [Removing a professional services product](#proserv-remove-product)

## Prerequisites<a name="proserv-prereqs"></a>

To sell professional services on AWS Marketplace, you must complete the following prerequisites:
+ Have access to the AWS Marketplace Management Portal\. This is the tool that you use to register as a seller and manage the products that you sell on AWS Marketplace\. To learn more about getting access to the AWS Marketplace Management Portal, see [Policies and permissions for AWS Marketplace sellers](detailed-management-portal-permissions.md)\.
+ Register as an AWS Marketplace seller, and, if you want to charge for your products, submit your tax and banking information\. To learn more about becoming an seller, see [Getting started as a seller](user-guide-for-sellers.md)\.
+ You must have a professional services product to offer that is related to at least one public product in AWS Marketplace\. Your product must either directly support those products, or offer services that drive subscriptions to that AWS Marketplace product\.

**Note**  
Your product must be listed in at least one of these primary categories: Assessments, Implementation, Managed services, Premium support, or Training\.   
For more information about professional services product guidelines, see [Requirements for professional services products ](proserv-product-guidelines.md)\.

## Creating a professional services product<a name="proserv-create"></a>

The following procedure describes how to create a new professional services product in the AWS Marketplace Management Portal\.

**To create a professional services product**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the **Products** menu, select **Professional services**\. This page shows you all professional services products that you have already created, as well as any requests you have made for creating or modifying these products\.

1. On the **Current professional service products** tab, select **Create professional service product**\.

1. On the **Create product** page, provide the information for your product, and select **Submit**\. For more information about the details that you must provide, see [Providing details for a professional services product](proserv-product-details.md)\.

1. \(Optional\) From the **Products** menu of AWS Marketplace Management Portal, select **Professional services**, then choose the **Requests** tab\. Verify that you see your product request with the correct **Product title**, and that the **Request status** is **Under review**\. Your product should be created in limited preview mode within a few minutes\.

**Note**  
You can return to the **Requests** tab of the **Professional services** page to see the status of your request at any time\. Any errors in the creation process will appear here\. You can select the request to see the request details or to fix errors\.

When your product is initially created, it's only accessible to your AWS account \(the one you used to create the product\)\. If you view the product from the **Professional services** page, you can select **View on AWS Marketplace** to view the product details as they appear in AWS Marketplace for buyers\. This detail listing isn't available to other AWS Marketplace users, unless you extend a private offer to them\.

To learn how to make the product available publicly, see [Editing product visibility](#proserv-edit-visibility)\.

## Creating private offers<a name="proserv-create-offer"></a>

When a potential buyer views your product on AWS Marketplace, they can't purchase it directly\. When they attempt to subscribe, they are redirected to request a [private offer](marketplace/latest/userguide/private-offers-overview.html) from you\. AWS Marketplace sends an email message to your AWS Marketplace seller account root user email address, informing you that the customer has requested a private offer\. The following procedure describes how to respond to this request\.

**Note**  
You can create private offers with prices up to $250,000 through the AWS Marketplace Management Portal\. To create a private offer higher than $250,000, approval is required\. For more information, contact your AWS Marketplace Business Development representative, or send an email message with your details to the AWS Marketplace Business operations team at [ mpcustdesk@amazon\.com](mailto:mpcustdesk@amazon.com)\.

**To create a private offer for a professional services product**

1. Contact the customer to resolve any questions you have about the request\. Agree on the offer terms before creating the private offer in AWS Marketplace\. The buyer is not obligated to purchase your product, so it makes sense to agree before creating the offer\.

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. Select **Offers** from the menu, then select **Create private offer**\.

1. On the **Create private offer** page, select the product that you want to create a private offer for\. Only currently available products are included\.

1. Enter the **Buyer account Ids**that you want to extend a private offer to\. You can include up to 25 accounts in a single private offer\. If the buyer used the request an offer feature, the email message that you received includes the buyer account Id for the requesting account\.

1. Choose whether to allow buyers to pay for the product in installments\. Typically, short contracts are paid in one payment\. Longer contracts may have the option to pay in installments, but this is part of the agreement that you come to with the buyer\. Select **Next**\.

1. Complete the offer details, including the following information:
   + **Custom offer name** – Provide enough detail that you and the customers will recognize the offer\. Include your company or product name and a description of the product\. Do not include any personally identifiable information, including names, phone numbers, or addresses\.
   + **Agreement end date** – The date that the agreed\-to services end\. For example, if you are offering support for 1 year, enter a date that is 1 year away from the date that the service will be available\.
   + **Product dimensions** – The prices and units for the service that you are offering, as follows:
     + Lump sum payment offers – You can list each of the dimensions with their associated price \(for example, you could have dimensions called *Silver*, *Gold*, and *Platinum*\)\. The buyer can choose and pay for their preference\. 
     + Offers that include a payment schedule – You must choose a single dimension and provide a payment schedule with amounts and dates for each payment\.
**Note**  
If you want to create a zero dollar offer, you must select **I want to enable zero dollar prices** for confirmation\. This precaution helps to prevent you from accidentally creating a free offer\.
   + **Service agreement** – Documents that define your service agreement with the customer\. The documents that you upload \(in text or PDF formats\) are appended together into a single PDF document, so make sure that the file name is not required to understand the content\.
   + **Offer expiration date** – The date the offer expires\. This determines how long the buyer has to accept the offer and is unrelated to when the professional service will be available\.

1. Select **Next** when you're done editing the options\.

1. On the **Review offer** page, make sure that the offer details are correct, and then choose **Create offer**\.
**Note**  
Your offer may take some time to be published\. After it's published, you can view the offer on the **Manage offers** page\. If you need to edit an offer \(that has not yet been accepted\), you can do so from that page\.

1. After the offer is published, and available on the **Manage private offers** page, from the **Actions** menu for that offer, select **Copy offer URL**, and then send it in an email message to the buyer to accept\.

## Editing product information<a name="proserv-edit-product"></a>

The following procedure describes how to edit the product information for an existing professional services product in the AWS Marketplace Management Portal\.

**To edit product information**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the **Products** menu, select **Professional services**\. This page shows you all professional services products that you have already created, as well as any requests you have outstanding for creating or modifying these products\.

1. Select an existing product that you would like to edit\. Then, from the **Request changes** menu, select **Update product information**\.

1. Make the changes to the details\. For more information about the fields you can edit, see [Providing details for a professional services product](proserv-product-details.md)\.

1. Select **Submit** to create the request\.

1. \(Optional\) If you are not already on the **Requests** tab of the **Professional services** page, then from the **Products** menu of AWS Marketplace Management Portal, select **Professional services**, then choose the **Requests** tab\. Verify that you see your request with the correct **Product title**, and that the **Request status** is **Under review**\. Your product will be updated with the changes you requested within a few minutes\. If there is an error, you can view it here and resubmit your edits after fixing the errors\.

## Editing product pricing<a name="proserv-edit-pricing"></a>

The following procedure describes how to edit the pricing information for an existing professional services product in the AWS Marketplace Management Portal\.

**To edit product pricing**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the **Products** menu, select **Professional services**\. This page shows you all professional services products that you have already created, as well as any requests you have made for creating or modifying these products\.

1. Select an existing product that you would like to edit, then from the **Request changes** menu, select **Update pricing dimensions**\.
**Note**  
You can only add new pricing dimensions through the AWS Marketplace Management Portal\. To modify or remove previously created dimensions, contact the [ AWS Marketplace Seller Operations team](https://aws.amazon.com/marketplace/management/contact-us/) with your request\. In your request, include the product ID and details about what dimensions you want to change or remove\.

1. Add any new pricing dimensions that you want\. For more information about the pricing fields, see [Providing details for a professional services product](proserv-product-details.md)\.

1. Select **Submit** to create the request\.

1. \(Optional\) From the **Products** menu of AWS Marketplace Management Portal, select **Professional services**, then choose the **Requests** tab\. Verify that you see your request with the correct **Product title**, and that the **Request status** is **Under review**\. Your product will be updated with the changes you requested within a few minutes\. If there is an error, you can view it here and resubmit your edits after fixing the errors\.

## Editing product visibility<a name="proserv-edit-visibility"></a>

By default, products are created with limited visibility—a new product is only visible from your account\. You can add other test accounts, or make the product publicly visible in the AWS Marketplace\.The following procedure describes how to edit the visibility of an existing professional services product in the AWS Marketplace Management Portal\.

**To edit product visibility**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the **Products** menu, select **Professional services**\. This page shows you all professional services products that you have already created, as well as any requests you have outstanding for creating or modifying these products\.

1. Select an existing product that you would like to edit\. Then, from the **Request changes** menu, select **Update product visibility**\.

1. Select **Contact us**\. This launches a Contact Us page with the product information for the AWS Marketplace Seller Operations team to review and make the change\.

1. Add details of your request, including whether you want the product to be public or private\. If private, provide the account IDs you want to access, and then select **Submit** to send your request,

**Note**  
To make a product visible in the public AWS Marketplacecatalog requires a product review by the AWS Marketplace Seller Operations team to ensure that the product meets the product guidelines \(see [Requirements for professional services products ](proserv-product-guidelines.md)\)\. The request can take several days to complete\.

## Removing a professional services product<a name="proserv-remove-product"></a>

The following procedure describes how to remove an existing professional services product from the AWS Marketplace Management Portal\.

**To remove a product**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the **Products** menu, select **Professional services**\. This page shows you all professional services products that you have already created, as well as any requests you have outstanding for creating or modifying these products\.

1. Select an existing product that you would like to edit\. Then, from the **Request changes** menu, select **Unpublish a product**\.

1. Select **Contact us**\. This launches a **Contact Us** page with the correct information for the AWS Marketplace Seller Operations team to review and make the change\.

1. Complete any additional information requested in the **Contact Us** page template, and select **Submit** to send your request\.

**Note**  
The request can take several days to complete\. Products with active offers will be moved to restricted state until the last active subscription or contract is completed and then removed from AWS Marketplace\. Products in restricted state are only visible to customers with active offers and sellers will not be able to extend new offers on these products\.