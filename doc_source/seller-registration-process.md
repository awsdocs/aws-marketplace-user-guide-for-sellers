# Seller registration process<a name="seller-registration-process"></a>

By registering as a seller for AWS Marketplace, you can sell your products and services to other AWS Marketplace customers\. 



Registering as a seller requires the following steps:

1. **Create your public profile** – You provide the information that is displayed in AWS Marketplace to buyers that tells them about your company, such as your company name and logo\. After you complete this process, you can sell products for free\. To sell paid products, you must complete steps two and three\.

1. **Provide your tax information** – To appropriately assess, report, and \(where applicable\) withhold taxes on your paid sales, you must provide your tax and value added tax \(VAT\) information\.

1. **Provide your banking information** – You provide your US bank information so that AWS Marketplace can pay you for your sales\.

1. \(Optional\) **Enroll in the US tax calculation service** – You can optionally enroll in this service to calculate your US state sales and use tax for products you sell on AWS Marketplace\.

These steps are described in more detail in the following sections\.

After you have completed registering your account as a seller, you can create products to sell to buyers through AWS Marketplace\. For more information, see [Preparing your product](product-preparation.md)\.

You can use AWS Identity and Access Management \(IAM\) to configure your primary AWS account to allow multiple users with various permissions to access the AWS Marketplace Management Portal\. For more information, visit [Controlling access to AWS Marketplace Management Portal](marketplace-management-portal-user-access.md)\. 

## Creating your public profile<a name="seller-public-profile"></a>

The first step to register is to select the AWS account to use as your primary AWS Marketplace account, and provide the information that is displayed to potential buyers in the AWS Marketplace console\.

**Note**  
 Once you use an AWS account to list a product on AWS Marketplace, you cannot change the account associated with the product\. You can use an existing account or register a new account\. This account will be the seller of record for your products in AWS Marketplace and will be used for reporting, disbursement, and communication from AWS Marketplace to you\.

**To create your public profile**

1. From the [ AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour/) \(AMMP\), choose **Register now** and then sign in to your chosen seller AWS account\.

1. Select **Add public profile ** to provide your seller information\.

Once you have completed the public profile, you can publish and sell free products\. To sell paid products, you must provide your tax and banking information\.

## Providing tax information<a name="tax-info-for-sellers"></a>

You must provide your tax, and value added tax \(VAT\) where applicable, information so that AWS Marketplace can accurately report and withhold taxes on your product sales\.

**To provide your tax information**

1. Sign in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/), and choose **Settings**\.

1. Select **Complete tax information** in the **Payment Information** section\.

1. After you have completed the tax information, return to the **Settings** page and select **Complete VAT information**, if it is available\.

**Note**  
The VAT information section is only available if you are in an AWS Region that supports VAT\.

## Providing US bank account information<a name="us-bank-account-for-eu-sellers"></a>

A US bank account is required for all sellers who want to sell paid software in AWS Marketplace\. AWS Marketplace only disburses to US bank accounts\.

**Note**  
For a list of countries where you can offer paid products in AWS Marketplace, see [Eligible jurisdictions for paid products](user-guide-for-sellers.md#eligible-jurisdictions)\.

**To provide bank information**

1. Sign in to the [ AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/), and choose **Settings**\.

1. Select **Complete banking information** in the **Payment Information** section\.

1. Provide the required information about your US bank account\.

**Note**  
If you have not yet provided your tax information \(and value added tax information, where applicable\), you will not be able to provide your banking information\.

If you do not already have a US bank account, you may be able to obtain one through Hyperwallet\. Hyperwallet can provide you with a US account, which you can provide to AWS Marketplace for your AWS Marketplace disbursements\. 

Hyperwallet is an independent service provider that may enable you to transfer funds to another bank account in a supported currency\. For a limited time, you will not be required to pay certain Hyperwallet service fees in connection with AWS Marketplace disbursements\. 
+  By adding your Hyperwallet account details to your AWS Marketplace seller account, you agree and acknowledge that AWS Marketplace will share your name, email address, and account number with Hyperwallet to confirm your status as an AWS Marketplace seller\. 
+  Additional fees may apply to your use of Hyperwallet services \(including transfer fees and foreign exchange fees required to transfer funds into your local currency\), as well as foreign exchange rates\. Hyperwallet’s service fee will be waived for a limited time, and only with respect to AWS Marketplace disbursements of the proceeds from your Paid products into your Hyperwallet account\. Consult the Fees section of the Hyperwallet site or contact Hyperwallet for more information and to review applicable fees\. Visit the [Hyperwallet support site](https://wssellers.hyperwallet.com/hw2web/consumer/page/contact.xhtml) to learn more about their services\.

**To begin registration with Hyperwallet and obtain your US bank account information**

1. Sign in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/), and choose **Settings**, then select **Complete banking information** in the **Payment Information** section\.

1. If you do not have a Hyperwallet account, and need one for use in AWS Marketplace, choose **No** in response to **Do you have a US bank account?** and **Are you registered with Hyperwallet?** You will be provided with a personal identification number \(PIN\) and link to sign up for Hyperwallet\.

1.  After you have activated your Hyperwallet account, follow the steps described on the Hyperwallet registration portal to complete registration and receive your deposit account information\. 

1.  When you have obtained an account from Hyperwallet, add your Hyperwallet account information to your AWS account by signing in to the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/)\. Then, choose **Settings**, then select **Complete banking information** in the **Payment Information** section\. 

## AWS Marketplace Tax Calculation Service<a name="tax-calculation-service"></a>

AWS Marketplace Tax Calculation Service provides the ability to calculate and collect US sales and use tax for existing and new products\. Some states are not eligible for Tax Calculation Service because AWS Marketplace is required by law to collect and remit applicable sales tax attributable to taxable sales of your products to customers based in these states\. To use the service, configure your tax nexus settings for your seller profile, and then assign product tax codes to your products\. 

 To configure your tax nexus settings, open the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/settings), and under the **Settings** tab configure the applicable tax nexus settings\. Then, assign product tax codes \(PTCs\) to your products through the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/settings)\. We recommend that you review the [AWS Marketplace Tax Methodology](https://s3.amazonaws.com/aws-mp-seller-tax-terms/AWS_Marketplace_Tax_Methodology_Doc.pdf) and [AWS Marketplace Product Tax Code Guidance](https://s3.amazonaws.com/aws-mp-seller-tax-terms/Product_Tax_Codes_for_US_Sales_Tax.pdf) in their entirety before completing this process\. For product types not supported by the **Products** tab submission process, download a product load form by choosing **File Upload** from the **Assets** tab\. You must edit and upload the updated product load form\.

 Once you have completed these two steps, US sales and use tax calculation will be enabled\. Note the following: 
+  Activation of your tax nexus settings takes from 5 to 48 hours\. 
+  Tax nexus settings must be configured before you can assign PTCs\. 
+  PTC assignment happens 24 hours after the AWS Marketplace team approves and publishes your product, which may take 3\-5 days from the time you submit your product change request\. 
+  When tax calculation begins, estimated sales tax charges will be included in customer invoices\. Sales tax will be calculated based on factors including, but not limited to, the customer’s billing address, the tax code of your product, and your tax nexus settings\. The resulting sales tax charge, if applicable, will be included in the customer’s invoice and identified as a US sales tax charge under the specific product sold by your company\. Note that customer invoices will show your company's Legal Name, which you provided when you registered to become an AWS Marketplace seller\. 
+  The collected sales tax funds are sent with your monthly disbursement, and the US Sales and Use Tax Report is available to you on the fifteenth of the month, detailing what taxes were collected\. You are responsible for remitting your own taxes\. 

 If you enroll for the AWS Marketplace Tax Calculation Service, we also recommend that you register for the [Amazon Tax Exemption Program](https://aws.amazon.com/marketplace/management/settings) \(ATEP\)\. You are not required to use this service\. However, we recommend that all AWS Marketplace sellers who use the Tax Calculation Service participate in ATEP\. Participation helps to reduce the number of tax\-only refunds that will need to be processed to qualified customers registered in ATEP\. 

 You can edit or delete the tax nexus information on the [Tax Calculation Service Settings](https://aws.amazon.com/marketplace/management/settings) page in the AWS Marketplace Management Portal\. 

 For more information, visit [AWS Marketplace Sellers](https://aws.amazon.com/tax-help/marketplace/) on [Amazon Web Service Tax Help](https://aws.amazon.com/tax-help/) to learn more about where AWS collects sales tax, VAT, or GST on your sales and remits such taxes to the local tax authorities, in the name of AWS, Inc\. 

**Note**  
Your use of the Tax Calculation service is governed by the [ AWS Marketplace US Tax Collection Support Terms and Conditions](https://s3.amazonaws.com/aws-mp-seller-tax-terms/AWS_Marketplace_Tax_Support_Terms_and_Conditions.pdf?icmpid=docs_marketplace_helppane)

## Disbursement and buyer billing<a name="disbursement"></a>

AWS acts as the billing mechanism on your behalf\. The two most common payment options available to buyers are *credit card* and *invoicing*\.

The following is information about the billing for AWS Marketplace subscriptions:
+ Purchases with upfront payments are billed immediately upon subscription\.
+ Billing schedules for private offers are agreed upon between the buyer and seller\.
+ Invoice payment terms \(including bill due date\) are agreed upon between the buyer and AWS\. The terms are *not* disclosed to vendors\.
+ Private offers using the flexible payment scheduler are required to be on *invoicing* as the payment option\.
+ You can validate the invoicing using the [Monthly billed revenue report](monthly-billed-revenue-report.md)\. This report summarizes invoicing by AWS on your behalf\. This report contains a Transaction Reference key to match and provide visibility to the invoice creation date and invoice due date\.

The following is information about how you as the seller get your disbursement:
+ A valid [payment method](https://portal.aws.amazon.com/gp/aws/developer/account?ie=UTF8&action=payment-method), a [registered US bank account](https://aws.amazon.com/marketplace/management/seller-settings/account/bank), and a submitted W9 form are required for disbursement\.
+ Sellers of paid products are required to provide a W\-8, value added tax \(VAT\) or good and services tax \(GST\) registration number, and a US bank account\. [Hyperwallet](https://wssellers.hyperwallet.com/) can provide you with a US bank account, which you can provide to AWS Marketplace for your AWS Marketplace disbursements\. 
+  AWS disburses payments monthly directly to the bank account associated with the seller account, minus AWS Marketplace service fees\. 
+  AWS disburses payment via ACH transfer after the buyer pays an invoice\. 
+ AWS disbursements are made once a month between the 7th and 10th of the month\. The date will be the same for a seller each month\. The [Disbursement report](monthly-disbursement-report.md) will reflect your disbursement date\.
+ AWS disbursements cover a rolling monthly period \(starting when the seller account was created\)\.
+  Funds are disbursed only after they are collected from the customer\. 
+ Payments take approximately 1–2 business dates to arrive in the seller's bank following the disbursement date\. The exact timing is subject to the bank and the time zone\.
+ The disbursement report is updated in the AWS Marketplace Management Portal 3–5 days after the disbursement\.
+ Details about disbursed funds and uncollected funds are available in the monthly disbursement report, including any open account receivables\.
+  If you participate in the AWS Marketplace Tax Calculation Service, any US sales and use tax collected from customers will be included in your monthly disbursement\. 

## Already a seller?<a name="already-a-seller"></a>

Manage your products into incremental channel revenue by taking advantage of the go\-to\-market activities made available in the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour)\. Activities include the following:
+ Measure the results of your marketing efforts within hours, including the usage and revenue driven by your campaigns\. 
+ Enable customer service representatives to retrieve customer data in real time\. 
+ Upload files needed to create and manage your products, and monitor progress as we process them\. 