# Submitting your product for publication<a name="product-submission"></a>

You use the product submission process to make your products available on AWS Marketplace\. Products can be quite simple, for example, a single Amazon Machine Image \(AMI\) that has one price structure\. Or, products can be quite complicated, with multiple AMIs, AWS CloudFormation templates, and complex pricing options and payment schedules\. You define your product offering and submit it through the AWS Marketplace Management Portal in one of two ways:
+ Using the **Products** tab – For products that are less complex, you use the **Products** tab to completely define and submit your request\.
+ Using the **Assets** tab – For products that are more complex and require more definition, you download a product load form \(PLF\), add product details, and then upload the completed form using the **File upload** option\.

**Note**  
Data product providers must use the AWS Data Exchange console to publish products\. For more information, see [Publishing Products](https://docs.aws.amazon.com/data-exchange/latest/userguide/publishing-products.html) in the *AWS Data Exchange User Guide*\.

 We recommend that you start by using the **Products** tab to determine which approach to use\. The following table lists configurations and the approach you use to submit your request\. The first column is the pricing model for your product, and the other three columns are how the product is deployed to the customer\. 


| Pricing model  | Products launched using single\-node AMI | Products launched with AWS CloudFormation | Products launched as software as a service \(SaaS\) | 
| --- | --- | --- | --- | 
|  Bring Your Own License \(BYOL\)  |  Products tab  |  Assets tab  |     | 
|  Free  |  Products tab  |  Assets tab  |     | 
| Paid Hourly  |  Products tab  |  Assets tab  |     | 
| Paid Hourly with Annual  |  Products tab  |  Assets tab  |     | 
| Paid Monthly  |  Products tab  |  Assets tab  |     | 
|  Hourly with Monthly  |  Assets tab  |  Assets tab  |     | 
| Paid Usage \(AWS Marketplace Metering Service\) |  Products tab  |  Assets tab  |     | 
| Contract Pricing | Products tab |  |  | 
|  SaaS Subscription  |     |     |  Products tab  | 
|  SaaS Contract  |     |     |  Products tab  | 
|  SaaS Legacy  |     |     |  Assets tab  | 

 You can submit products individually or, if you use a product load form, you can submit multiple products or product updates at the same time\. You cannot submit multiple products at the same time using the **Products** tab\. If you are unclear on what products can be submitted in what manner, start by using the **Products** tab\. If you have any problems making your submissions, contact the [AWS Marketplace Managed Catalog Operations \(MCO\)](https://aws.amazon.com/marketplace/management/contact-us/) team\.

## Using the Products tab<a name="using-the-products-tab"></a>

 To access the **Products** tab, log in to the AWS Marketplace Management Portal\. From the **Products** tab, choose either **Server**, **SaaS**, or **Machine learning**, depending on the type of product you are managing\. A dashboard for that product type appears that contains all of your current products\. If you choose the **Requests** tab, the dashboard displays any outstanding requests you have and your completed request history\. Once you start creating a new product request, you can save your work in progress, and if necessary, create your request in several different sessions\.

 When you are ready to submit your product request, the request is reviewed by the AWS Marketplace team\. You can monitor the status of your request on the product page for the type of product you are requesting\. For new products, after your request is approved for publication, you receive a limited listing URL that you can use to preview and approve your submission\. Your product offer is not published until you approve the submission\. When you request an update to an existing product, the update is published without the need for you to review and approve the change\. This includes adding or removing versions, and metadata changes\. 

 You track the status of your requests under the **Requests** tab\. The status will be one of the following: 
+  **Draft** – You have started the request process but have not submitted your request\. 
+  **Submitted** – You have completed and submitted your request, and it is under review\. 
+  **Action Required** – The AWS Marketplace team has reviewed your request and needs more information\. 
+  **Approval Required** – The AWS Marketplace team has created the limited listing URL for your product\. You must review and either approve or reject the URL before AWS Marketplace will publish\. If you approve, the status changes to **Publishing Pending** while the site gets published\. If you reject, the status returns to **Draft** so you can modify the request\. 
+  **Publishing Pending** – You have approved the mock\-up of your request and AWS Marketplace is publishing your product\.
+  **Expired** – You started the request process but did not complete it within six months, so the request expired\. 

 If you have an entry with a status of **Submitted**, you can retract the submission\. If you have an entry with a status of **Draft**, you can delete the request\. This will allow you to start over\. When you delete a **Draft** entry, the entry is moved to the **Request History** tab\. 

 To add your product in the AWS GovCloud \(US\) AWS Region, you must [have an active AWS GovCloud \(US\) account](http://docs.aws.amazon.com/govcloud-us/latest/UserGuide/getting-started-sign-up.html) and comply with the AWS GovCloud \(US\) requirements, including export control requirements\. 

## Company and product logo requirements<a name="seller-and-product-logos"></a>

 Your company logo and the logo for your products must conform to the following AWS Marketplace guidelines so that the user experience is uniform when browsing AWS Marketplace: 

 **Product logo specifications** – Your product logo image should have a transparent or white background and be 120 to 640 pixels in size, with a 1:1 or 2:1 \(wide\) ratio\. 

 **Company logo specifications** – Your company logo image should have a transparent background and be 220 x 220 pixels in size, allowing for 10 pixels of padding on each side within\. 

## Requirements for submitting paid repackaged software<a name="paid-repackaged-software"></a>

If you are submitting a paid listing of either a repackaged open\-source software \(for example, open source AMI or container products with paid support\), or software that was originally created by a vendor other than you \(for example, reselling an AMI with Windows operating system\), the following requirements must be met before submission:
+ The product title must indicate the value added by your repackaging\. Examples of product titles include: *Hardened <Product>*, *<Product> with added packages*, *<Product1> on <Product2>*\.
+ The product title must not contain any other language that is not otherwise supported with documentation\. For example, the product title may not use the words *certified*, *original*, or *free* unless these are substantiated in the product details that you provide\.
+ The product short description must include a clear statement summarizing the product charges\. The short description must begin with the phrase *This product has charges associated with it for\.\.\.*\. For example, if a product includes charges for support from the seller, then the product description should state: *This product has charges associated with it for seller support*\.
+ The product logo must be same as the company logo which was used during your seller registration process\. The product logo can differ from your company logo only if you use the official software logo, whereby you must receive explicit permission from the original software vendor\. If explicit permission is obtained, a link to that documentation must be included in the notes section of the change request \(or in the **Enter a brief description** field of the **File Uploads** page when using the product load form\)\.
+ For AMI products, the AMI name must not be reused from the original product\. The AMI name must begin with the seller name and follow this format: \[Seller Name\] \[name\-given\-to\-ami\]\.

If the paid listing is for a standalone software product that was not created by your company and there is no intellectual property added to the product \(for example, bundling additional software libraries or adding special configuration\) then, along with the earlier requirements, the following requirements must also be met:
+ Product title must include the seller name \(along with the value added, as described earlier\)\. The seller name is the name used during seller registration\. For example, *<Product> with maintenance support by <seller>*\.
+ The first line of the product's long description must begin with the phrase *This is a repackaged software product wherein additional charges apply for\.\.\.* \(or, if it's open source, *This is a repackaged open source software product wherein additional charges apply for\.\.\.*\)\. Then, the long description must include a clear statement summarizing what you are charging for, as well as additional details describing those features\. For example, the long description of an open source product charging for additional support might start as: *This is a repackaged open source software product wherein additional charges apply for support with \{SLA Details\}*\.

## AWS CloudFormation\-launched product \(free or paid\) or usage\-based paid AMI product<a name="aws-cloudformation-launched-product-free-or-paid-or-usage-based-paid-ami-product"></a>

Use a product load form \(PLF\) to submit products that AWS Marketplace customers launch by using AWS CloudFormation templates\. The PLF **** is available through the AWS Marketplace Management Portal \(AMMP\)\. 

### Submitting your product<a name="submitting-your-product"></a>

1.  From the [AMMP](https://aws.amazon.com/marketplace/management/products/?), download the product load form \(PLF\) for your product\. 

1.  Add your product definition, which includes product information \(title, description, highlights\), technical information \(AMI\_ID, Regions, instance types, OS\), and pricing details \(pricing model, Free Trial\)\. 

1.  Submit your PLF following the instructions under the Instructions table of the spreadsheet\. 

The AWS Marketplace team reviews your product for policy and security compliance, software vulnerabilities, and product usability\. If there are any questions or issues with a request, the AWS Marketplace team will contact you via an email message to discuss your request\. Once approved, a mock\-up of your product's page is created\. After you review the page, you accept or reject the mock\-up\. Once approved, we add the page to the AWS Marketplace\.

### Updating your product<a name="updating-your-product"></a>

 For products that you created by using the product load form \(PLF\), you also use the PLF to make changes to those products\. You can make changes to the original PLF you completed or, if it's not available, you can start with a new PLF\. Just like using the **Products** tab, you can add a new version, remove existing versions, and update pricing, instance types, Region availability, and metadata\. To make an update, you prepare any updated product the same way you prepare a new product\. After the product update is prepared, follow these steps: 

1.  Use your existing PLF or, from the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/), under the **Assets** tab, choose **File upload**\. Under **Product load forms and seller guides**, you can download the PLF for your product\.

1.  Update your product submission in the PLF\. 

1.  From the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/products/?), under the **Assets** tab, choose **File Upload**\. 

1.  On the **File Uploads** page, upload your updated PLF and any AWS CloudFormation templates\. The file uploader provides a secure transfer mechanism and a history of submitted files\. The uploader automatically notifies the AWS Marketplace team to begin processing your request\. Include a description of the submission \(adding new version, changing price, changing metadata, and so forth\)\. 

Your product submission is reviewed for policy and security compliance, software vulnerabilities, and product usability\. If there are any questions or issues with a request, the AWS Marketplace team will contact you via an email message\. Updates to existing product pages are processed and released directly without additional reviews\.

## Product changes and updates<a name="product-changes-and-updates"></a>

 Sellers can submit changes to their product at any time, and they will be processed as described earlier\. However, some changes can only be made every 90 or 120 days, or when pending changes are in place\. Examples include price changes and AWS Region or instance type changes\. Common changes include: 
+  **New Version** – New versions of the software and rollouts of patches or updates\. At your request, we can notify customers who have subscribed to your AWS Marketplace content about the availability of new versions or send upgrade instructions on your behalf\. 
+  **Metadata change** – Changes to product information \(Description, URLs, and Usage Instructions\)\. 
+  **Pricing Change** – A change to the pricing amount\. A notification to current customers is sent after the request is complete\. 
+  **Pricing Model Change** – A change to the pricing model \(for example, Hourly, Free, Hourly\_Annual\)\. Not all pricing model changes are supported, and all requests to change models must be reviewed and approved by the AWS Marketplace team\. Any change from a free to a paid model presents significant impact to existing customers\. An alternative is to propose a new product with additional features and encourage current customers to migrate\. 
+  **Region or Instance change** – Adding or removing instances types or Regions\. 
+  **Product takedown \-** Remove a product page from AWS Marketplace to prevent new customers from subscribing\. A notification to current customers is sent after the request is complete\. 

## Timing and expectations<a name="timing-and-expectations"></a>

 While we strive to process requests as quickly as possible, requests can require multiple iterations and review by the seller and AWS Marketplace team\. Use the following as guidance for how long it will take to complete the process: 
+  Total request time normally takes 2–4 weeks of calendar time\. More complex requests or products can take longer, due to multiple iterations and adjustments to product metadata and software\. 
+  Review and processing of requests typically requires 3 business days\. We will notify you if there are any issues that require additional action\. 
+  We require a completed product request and AMI at least 45 days in advance of any planned events or releases, so we can prioritize the request accordingly\. 

 If you have any questions about your request, contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

## Submitting AMIs to AWS Marketplace<a name="submitting-amis-to-aws-marketplace"></a>

 All AMIs built and submitted to AWS Marketplace must adhere to all product policies\. We suggest a few final checks of your AMI prior to submission: 
+  Remove all user credentials from the system; for example, all default passwords, authorization keys, key pairs, security keys or other credentials\. 
+  Ensure that root login is disabled or locked\. Only sudo access accounts are allowed\. 
+  If you are submitting an AMI to be deployed into the AWS GovCloud \(US\) Region, you need to [have an active AWS GovCloud account](http://docs.aws.amazon.com/govcloud-us/latest/UserGuide/getting-started-sign-up.html) and agree to the [AWS GovCloud Requirements](https://aws.amazon.com/service-terms/), including applicable export control requirements\. 

### AMI self\-service scanning<a name="ami-self-service-scanning"></a>

 Self\-service AMI scanning is available within the AWS Marketplace Management Portal\. With this feature, you can initiate scans of your AMIs and receive scanning results quickly—typically in less than an hour—with clear feedback in a single location\. 

**To begin sharing and scanning your AMI with self\-service scanning**

1. Navigate to [https://aws\.amazon\.com/marketplace/management/manage\-products/](https://aws.amazon.com/marketplace/management/manage-products/)\. 

1. Select the AMI to share\.

1. View your scan results\.

After your AMI has successfully been scanned, you can follow the current process to submit it to the AWS Marketplace Seller Operations team by [uploading](https://aws.amazon.com/marketplace/management/product-load/) your product load form \(PLF\)\. If you have any issues, contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

To include your AMI in the self\-service scanning list, the AMI must be in the `us-east-1` \(N\. Virginia\) Region and owned by your AWS Marketplace seller account\. If you need to grant other accounts access to the AWS Marketplace Management Portal, you must register those accounts as sellers\. For more information, see [Seller registration process](seller-registration-process.md)\. 

### AMI cloning and product code assignment<a name="ami-cloning-and-product-code-assignment"></a>

After your AMI is submitted, AWS Marketplace creates cloned AMIs for each Region that you have indicated that software should be available in\. During this cloning and publishing process, AWS Marketplace attaches a product code to the cloned AMIs\. The product code is used to both control access and to meter usage\. All submissions must go through this AMI cloning process\. 

## Final checklist<a name="final-checklist"></a>

 To help avoid delays in publishing your product, use this checklist before you submit your product request\. 

 **Product usage** 
+  Production\-ready\. 
+  Does not restrict product usage by time or other restrictions\. 
+  Compatible with 1\-click fulfillment experience\. 
+  Everything required to use the product is contained within the software, including client applications\. 
+  Default user uses a randomized password and/or creation of initial user requires verification that the buyer is authorized to use the instance using a value unique to the instance such as instance ID\. 

 **For free or paid products** 
+  No additional license is required to use the product\. 
+ Paid repackaged software meets the AWS Marketplace [Requirements for submitting paid repackaged software](#paid-repackaged-software)\.
+  Buyer does not have to provide personally identifiable information \(for example, an email address\) to use the product\. 

**AMI preparation**
+  Use hardware virtual machine \(HVM\) virtualization and 64\-bit architecture\. 
+  Does not contain any known vulnerabilities, malware, or viruses\. 
+  Buyers have operating system\-level administration access to the AMI\. 
+  Run your AMI through AMI Self\-Service Scanning\. 

 **For Windows AMIs** 
+  Use the most recent version of `Ec2ConfigService`, as described in [Configuring a Windows Instance Using EC2Config Service](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2config-service.html)\. 
+  The `Ec2SetPassword`, `Ec2WindowsActivate`, and `Ec2HandleUserData` plugins are enabled, as described in [Configuring a Windows Instance Using EC2Config Service](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2config-service.html)\.
+  No Guest Accounts or Remote Desktop Users are present\. 

 **For Linux AMIs** 
+  Root login is locked and disabled\. 
+  No authorized keys, default passwords, or other credentials are included\. 
+  All required fields are completed\. 
+  All values are within specified character limits\. 
+  All URLs load without error\. 
+  Product image is at least 110px wide and between a 1:1 and 2:1 ratio\. 
+  Pricing is specified for all enabled instance types \(for hourly, hourly\_monthly, and hourly\_annual pricing models\)\. 
+  Monthly pricing is specified \(for hourly\_monthly and monthly pricing models\)\. 

 If you have any questions or comments about automated AMI building, contact the [AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/) team\. 