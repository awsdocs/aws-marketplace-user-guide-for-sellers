# Submitting your product for publication<a name="product-submission"></a>

You use the product submission process to make your product\(s\) available on AWS Marketplace\. Products can be quite simple, for example a single Amazon Machine Image \(AMI\) that has one price structure\. Or, can be quite complicated, with multiple AMIs, AWS CloudFormation templates, and complex pricing options and payment schedules\. You define your product offering and submit it through the AWS Marketplace Management Portal in one of two ways\.
+ Using the **Products** tab – For products that are less complex, you use the **Products** tab to completely define and submit your request\.
+ Using the **Assets** tab – For products that are more complex and require more definition, you download a product load form, add product details, and then upload the completed form using the **File upload** option\.

**Note**  
Data product providers must use the AWS Data Exchange console to publish products\. For more information, see [Publishing Products](https://docs.aws.amazon.com/data-exchange/latest/userguide/publishing-products.html) in the *AWS Data Exchange User Guide*\.

 We recommend that you start by using the **Products** tab to determine which approach to use\. Existing or new product configurations might be added that might enable you to use the more automated, **Products** tab method\. The following table lists some configuration and the approach you use to submit your request\. The first column is the pricing model for your product, the other three columns are how the product is deployed to the customer\. 


| Pricing model  | Products launched using single\-node AMI | Products launched with AWS CloudFormation | Products launched as software as a service \(SaaS\) | 
| --- | --- | --- | --- | 
|  Bring Your Own License \(BYOL\)  |  Products tab  |  Assets tab  |     | 
|  Free  |  Products tab  |  Assets tab  |     | 
|  Hourly  |  Products tab  |  Assets tab  |     | 
|  Hourly with Annual  |  Products tab  |  Assets tab  |     | 
|  Monthly  |  Assets tab  |  Assets tab  |     | 
|  Hourly with Monthly  |  Assets tab  |  Assets tab  |     | 
|  Usage \(MMS\)  |  Assets tab  |  Assets tab  |     | 
|  SaaS Subscription  |     |     |  Products tab  | 
|  SaaS Contract  |     |     |  Products tab  | 
|  SaaS Legacy  |     |     |  Assets tab  | 

 You can submit products individually, or, if you use a product load form can submit multiple products or product updates at the same time\. You cannot submit multiple products at the same time using the **Products** tab\. If you are unclear on what products can be submitted in what manner, start by using the **Products** tab\. If you have any problems making your submissions, contact the [AWS Marketplace Managed Catalog Operations \(MCO\)](https://aws.amazon.com/marketplace/management/contact-us/) team\.

## Using the Products tab<a name="using-the-products-tab"></a>

 To access the **Products** tab, log in to the AWS Marketplace Management Portal\. From the **Products** tab, choose either **Server**, **SaaS**, or **Machine learning**, depending on the type of product you are managing\. A dashboard for that product type appears that contains all of your current products\. If you choose the **Requests** tab, the dashboard displays any outstanding requests you have, as well as view your completed request history\. Once you start creating a new product request, you can save your work in progress, and if necessary, create your request in several different sessions\.

 When you are ready to submit your product request, the request is reviewed by the AWS Marketplace team\. You can monitor the status of your request on the product page for they type of product you are requesting\. For new products, once your request is approved for publication, you receive a limited listing URL that you use to preview and approve your submission\. Your product offer is not published until you approve the submission\. When you request an update to an existing product, the update is published without the need for you to review and approve the change\. This includes adding/removing versions, and metadata changes\. 

 You track the status of your requests under the **Requests** tab\. The status will be one of the following: 
+  Draft – you have started the request process but have not submitted your request\. 
+  Submitted – you have completed and submitted your request and it is under review\. 
+  Action Required – AWS Marketplace has reviewed your request and needs more information\. 
+  Approval Required – AWS Marketplace has created the limited listing URL for your product and you must review and approve or reject the URL before AWS Marketplace will publish\. If you approve, the status changes to **Publishing Pending** while the site gets published\. If you reject, the status returns to **Draft** so you can modify the request\. 
+  Publishing Pending – You have approved the mock\-up of your request and AWS Marketplace is publishing your product\.
+  Expired – You started the request process, but did not complete within six months so the request expired\. 

 If you have an entry with a status of **Submitted**, you can retract the submission\. If you have an entry with a status of **Draft**, you can delete the request\. This will allow you to start over\. When you delete a **Draft** entry, the entry is moved to the **Request History** tab\. 

 To add your product in the AWS GovCloud \(U\.S\.\) region, you must [have an active AWS GovCloud \(U\.S\.\) account](http://docs.aws.amazon.com/govcloud-us/latest/UserGuide/getting-started-sign-up.html) and comply with the AWS GovCloud \(U\.S\.\) requirements, including export control requirements\. 

## Company and product logo requirements<a name="seller-and-product-logos"></a>

 Your company logo and the logo for your products need to conform to our guidelines so that the user experience is uniform when browsing AWS Marketplace\. 

 **Product Logo Specifications** – Your product logo image should have a transparent or white background and be 120 to 640 pixels in size, with a 1:1 or 2:1 \(wide\) ratio\. 

 **Company Logo Specifications** – Your company logo image should have a transparent background and be 220 x 220 pixels in size, allowing for 10 pixels of padding on each side within\. 

## AWS CloudFormation\-launched product \(free or paid\) or usage\-based paid AMI product<a name="aws-cloudformation-launched-product-free-or-paid-or-usage-based-paid-ami-product"></a>

 Products that AWS Marketplace customer launch by using AWS CloudFormation templates must be submitted using the **Product Load Form** available through the AMMP\. 

### Submitting your product<a name="submitting-your-product"></a>

1.  From the [AMMP](https://aws.amazon.com/marketplace/management/products/?), download the Product Load Form for your product\. 

1.  Add your product definition, which includes product information \(title, description, highlights\), technical information \(AMI\_ID, regions, instance types, OS\), and pricing details \(pricing model, Free Trial\)\. 

1.  Submit your form following the instructions under the Instructions table of the spreadsheet\. 

AWS Marketplace reviews your product for policy and security compliance, software vulnerabilities, and product usability\. If there are any questions or issues with a request, the AWS Marketplace team will contact you via email to discuss your request\. Once approved, a mock\-up of your product's page is created\. After your review the page, you accept or reject the mock\-up\. Once approved, we add the page to the AWS Marketplace\.

### Updating your product<a name="updating-your-product"></a>

 The Product Load Form is used to make one or more changes to the products you created using the Product Load Form\. You can make changes to the original product load form you completed, or, if not available you can start with a new load form\. Just like using the **Products** tab, you can add a new version, remove existing versions, and update pricing, instance types, region availability, and metadata\. To make an update, you prepare any updated product the same way you do new products\. Once the product is prepared: 

1.  Use your existing product load form, or, from the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/), under the **Assets** tab, choose **File upload**\. Under **Product load forms and seller guides**, you can download the product load form for your product\.

1.  Update your product submission in the product load form\. 

1.  From the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/products/?), under the **Assets** tab, choose **File Upload**\. 

1.  On the **File Uploads** page, upload your updated product load form, and any AWS CloudFormation templates\. The file uploader provides a secure transfer mechanism and a history of submitted files\. The uploader automatically notifies the AWS Marketplace team to begin processing your request\. Include a description of the submission \(adding new version, changing price, changing metadata, etc\.\)\. 

Your product submission is reviewed for policy and security compliance, software vulnerabilities, and product usability\. If there are any questions or issues with a request, the AWS Marketplace team will contact you via email\. Updates to existing product pages are processed and released directly without additional reviews\.

## Product changes and updates<a name="product-changes-and-updates"></a>

 Sellers can submit changes to their product at any time, and they will be processed as described above\. However, some changes can only be made every 90 or 120 days, or when pending changes are in place\. Examples include price changes, and region/instance type changes\. Common changes include: 
+  **New Version** \- New versions of the software, rollouts of patches or updates\. At your request, we can notify customers who have subscribed to Your Marketplace Content about the availability of new versions or send upgrade instructions on your behalf\. 
+  **Metadata change** \- Changes to product information \(Description, URLs, and Usage Instructions\)\. 
+  **Pricing Change** \- A change to the pricing amount\. A notification to current customers is sent once the request is complete\. 
+  **Pricing Model Change** \- A change to the pricing model \(for example, Hourly, Free, Hourly\_Annual\)\. Not all pricing model changes are supported and all requests to change models must be reviewed and approved by AWS Marketplace\. Any change from a free to a paid model presents significant impact to existing customers\. An alternative is to propose a new product with additional features and encourage current customers to migrate\. 
+  **Region or Instance change** \- Adding or removing instances types or Regions\. 
+  **Product takedown \-** Remove a product page from AWS Marketplace to prevent new customers from subscribing\. A notification to current customers is sent after the request is complete\. 

## Timing and expectations<a name="timing-and-expectations"></a>

 While we strive to process requests as quickly as possible, requests can require multiple iterations and review by the seller and AWS Marketplace teams\. Use the following as guidance for how long it will take to complete the process: 
+  Total request time normally takes 2\-4 weeks of calendar time\. More complex requests or products can take longer, due to multiple iterations and adjustments to product metadata and software\. 
+  Review and processing of requests typically requires 3 business days\. We will notify you if there are any issues that require additional action\. 
+  We require a completed product request and AMI at least 45 days in advance of any planned events or releases so we can prioritize the request accordingly\. 

 If you have any questions about your request, contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

## Submitting AMIs to AWS Marketplace<a name="submitting-amis-to-aws-marketplace"></a>

 All AMIs built and submitted to AWS Marketplace must adhere to all product policies\. We suggest a few final checks of your AMI prior to submission: 
+  Remove all user credentials from the system; all default passwords, authorization keys, key pairs, security keys or other credentials\. 
+  Ensure that root login is disabled or locked\. Only sudo access accounts are allowed\. 
+  If you are submitting an AMI to be deployed into the AWS GovCloud \(US\) region, you need to [have an active AWS GovCloud account](http://docs.aws.amazon.com/govcloud-us/latest/UserGuide/getting-started-sign-up.html) and agree to the [AWS GovCloud Requirements](https://aws.amazon.com/service-terms/), including applicable export control requirements\. 

### AMI self\-service scanning<a name="ami-self-service-scanning"></a>

 Self\-service AMI scanning is available within the AWS Marketplace Management Portal\. With this feature, you can initiate scans of your AMIs and receive scanning results quickly – typically in less than an hour – with clear feedback in a single location\. 

**To begin sharing and scanning your AMI with this new service**

1. Navigate to [https://aws\.amazon\.com/marketplace/management/manage\-products/](https://aws.amazon.com/marketplace/management/manage-products/)\. 

1. Select the AMI to share\.

1. View your scan results\.

After your AMI has successfully been scanned, you can follow the current process to submit it to the AWS Marketplace Seller and Catalog Operations team by [uploading](https://aws.amazon.com/marketplace/management/product-load/) your product load form\. If you have any issues, contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

To include your AMI in the self\-service scanning list, the AMI must be in the `us-east-1` \(N\. Virginia\) Region and owned by your AWS Marketplace seller account\. If you need to grant other accounts access to the AWS Marketplace Management Portal, you must register those accounts as sellers\. For more information, see [Seller registration process](seller-registration-process.md)\. 

### AMI Cloning and product code assignment<a name="ami-cloning-and-product-code-assignment"></a>

After your AMI is submitted, AWS Marketplace will create cloned AMIs for each region that you have indicated that software should be available\. During this cloning and publishing process, AWS Marketplace will attach a product code to the cloned AMIs\. The product code is used to both control access and to meter usage\. All submissions must go through this AMI cloning process\. 

## Final checklist<a name="final-checklist"></a>

 To help avoid delays in publishing your product, use this checklist before you submit your product request\. 

 **Product usage** 
+  Production\-ready 
+  Does not restrict product usage by time or other restrictions 
+  Compatible with 1\-click fulfillment experience 
+  Everything required to utilize the product is contained within the software including client applications 
+  Default user utilizes a randomized password and/or creation of initial user requires verification that the buyer is authorized to use the instance using a value unique to the instance such as instance ID 

 **For free or paid products:** 
+  No additional license is required to use the product 
+  Buyer does not have to provide personally identifiable information \(e\.g\. email address\) to use the product **AMI preparation** 
+  Utilizes hardware virtual machine \(HVM\) virtualization and 64\-bit architecture 
+  Does not contain any known vulnerabilities, malware or viruses 
+  Buyers have OS\-level administration access to the AMI 
+  Run your AMI through AMI Self Service Scanning 

 **For Windows AMIs:** 
+  Utilizes the most recent version of Ec2ConfigService 
+  Ec2SetPassword, Ec2WindowsActiviate and Ec2HandleUserData are enabled 
+  No Guest Accounts or Remote Desktop Users are present 

 *For Linux AMIs:* 
+  Root login is locked/disabled 
+  No authorized keys, default passwords or other credentials are included 
+  All required fields are completed 
+  All values are within specified character limits 
+  All URLs load without error 
+  Product image is at least 110px wide and between a 1:1 and 2:1 ratio 
+  Pricing is specified for all enabled instance types \(for hourly, hourly\_monthly and hourly\_annual pricing models\) 
+  Monthly pricing is specified \(for hourly\_monthly and monthly pricing models\) 

 If you have any questions or comments about automated AMI building, contact the [AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/) team\. 