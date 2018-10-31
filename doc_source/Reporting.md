# Seller Reports<a name="Reporting"></a>

 AWS Marketplace provides you the ability to retrieve reports for your listings\. The information available includes data on your listings, customers, financials, usage, and any U\.S\. Sales and Use Tax collected for use of your software\. Different reports provide data covering daily and monthly time periods\. All reports are generated as \.csv files so you can open with a variety of tools, or import into other systems\. You can download and view sample reports [here](https://s3.amazonaws.com/awsmp-loadforms/AWS+Marketplace+-+Seller+Reporting+Examples.zip)\. 

 AWS Marketplace strives to deliver as much data as possible to allow your listings and business to be successful on AWS Marketplace, we also adhere to strict Amazon standards and tenets around protecting customer data and not sharing personally identifiable information\. We will sometimes obfuscate or genericize customer data or specific details\. 

## Accessing Your Reports<a name="accessing-your-reports"></a>

 AWS Marketplace provides you two ways to obtain your reports: 

1.  Use the [AWS Marketplace Commerce Analytics Service](commerce-analytics-service.md) to request reports via API and retrieve them from an S3 bucket\. 

1.  Access and download reports on the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour) under the Reports tab\. 

 To protect customer privacy and trust, we do not share individually\-identifying customer information such as email addresses\. However, for sales compensation purposes we share certain entity\-level information about your customers through the AWS Marketplace Enhanced Data Sharing Program\. If you have enabled AWS Marketplace Product Support Connection for your products, customers who purchase your products can elect to share contact information with you that can be used for support purposes\. 

### Reports via CAS<a name="reports-via-cas"></a>

 AWS Marketplace Commerce Analytics Service \(CAS\) allows you to programmatically access your AWS Marketplace data via an API interface\. The interface provides you a way to automate the download and data ingestion of your information\. We highly recommend this method for accessing your AWS Marketplace data\. 

### Reports via Portal<a name="reports-via-portal"></a>

 All AWS Marketplace reports are available for download in the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/reports/), including reports for prior reporting periods\. Report notifications will be sent to the email address associated with the AWS account you registered with to sell on AWS Marketplace\. 

## Report Types<a name="report-types"></a>

 There are several reports available to track daily and monthly data\. Included in the reports is information about usage that has been billed to AWS customers, information about payment received from customers, and money being disbursed to you\. Disbursement does not occur until payment is received from the AWS customer\. Description of common terms: 

 **Billed** – AWS customers are billed at the beginning of every month for the metered usage incurred in the previous month\. Customers are also billed immediately when they purchase annual AMI subscriptions or SaaS contracts\. 

 **Payment** – Payment is due immediately for AWS customers who pay with a credit card\. Some customers have other payment arrangements with AWS billing that can change when their payment is due\. For instance, those that are invoiced\. 

 Disbursement – Payments from AWS customers are disbursed to you every month of a regular cycle, and the reporting for disbursements is available to you a few days later\. 

 The table below provides an overview of the types of reports and their purpose\. We recommend you download and view the [sample reports](https://s3.amazonaws.com/awsmp-loadforms/AWS+Marketplace+-+Seller+Reporting+Examples.zip)\. 


|  **Report Name**  |  **Description**  | 
| --- | --- | 
|  Daily Customer Subscriber Report  |  This report tells you the AWS account ID of every customer subscribed to your products, including the number of current and new annual subscriptions for each day\.  | 
|  Daily Business Report  |  This report provide information on daily usage by AWS customers, and projects the estimated revenue expected from customer usage\.  | 
|  Monthly Billed Revenue Report  |  This is a monthly report which gives you the revenue that has been billed to customers for usage of your software product as a result of hourly usage, or annual and monthly fees incurred\.  | 
|  Monthly Disbursement Report  |  This report breaks down money collected and disbursed to you for usage of your software product since your previous disbursement\.  | 
|  U\.S\. Sales and Use Tax Report  |  This is part of the AWS Marketplace Tax Calculation Service and reports on U\.S\. sales and use taxes calculated for your products\.  | 
|  Daily Ref Tag \(dashboard\)  |  This report references the same information from your [Marketing Dashboard](https://aws.amazon.com/marketplace/management/marketing/), providing insight into clicks and conversions for your ref tag links\.  | 
|  Weekly Ref Tag \(dashboard\)  |  This is a weekly summary of your product’s ref tag data, and the clicks and conversions associated with them\.  | 

### Daily Customer Subscription Report<a name="daily-customer-subscription-report"></a>

 This report is available daily and tells you every AWS account ID which is subscribed to your products, including the number of current and new annual subscriptions for each day\. Note that this report does not specify current or past usage, only that a customer is subscribed to your listing\. 

### Daily Business Report<a name="daily-business-report"></a>

 This report helps AWS Marketplace sellers understand how their products are being used by AWS customers on a daily basis, and projects the estimated revenue expected from that usage\. The data in this report includes a unique identifier per customer \(not the AWS Account Number\) that can be used to identify an AWS customer across report types and across days\. Sellers can track customer usage patterns and estimated customer spend with this ID, as well as gain insights into free trial and annual data\. 

### Monthly Billed Revenue<a name="monthly-billed-revenue"></a>

 This is a report on a monthly cadence which gives you the revenue that has been billed to the customers for usage of your software product as a result of hourly usage, or annual and monthly fees incurred\. Please note that the amounts in this report reflect revenue billed to customers, not amounts actually collected from customers\. 

### Disbursement Report<a name="disbursement-report"></a>

 This monthly report breaks down money received from customers and disbursed to you\. 

## Uncollected Funds FAQ<a name="uncollected-funds-faq"></a>

 **Q: What does “Uncollected mean in my Disbursement Report?** 

 **A:** The amount not paid yet by customers \(during the specified timeframe\)\. 

 **Q: Why are there uncollected amounts listed in my report and when will they be disbursed?** 

 **A:** We can only disburse money that was successfully collected from subscribers\. Once funds are collected, they will be disbursed at the next settlement date\. Please also note that some customers are on different payment terms\. 

 **Q: Why are there discrepancies between the Monthly Billing \(Revenue Report\) and Disbursement?** 

 **A:** The Monthly Billing Report shows you how subscribers are changing within a given week \(new, current, and cancelled\)\. It´s really a snapshot of activity\. The disbursement report gives you details on fees that we successfully collected and disbursed to you in a given reporting period\. The following things can affect Billing vs\. Disbursement: 
+  Some of our larger customers are on net terms, meaning that while they consume services in one month, the actual fees will only be collected in the following month\(s\)\. 
+  Payments for customers on credit cards can fall through if a customer fails to update credit card details in our systems or credit cards becoming invalid\. Those fees will show up as uncollected\. 

 **Q: What steps does AWS take to address the issue of non\-paying users?** 

 A: AWS takes several steps to follow\-up with customers on their payment, and will take action on accounts that are determined to be delinquent\. 

 **Q: How does a customer end up on different net terms?** 

 **A:** AWS customers must go through a thorough approval process which includes a review of how much they’re spending, payment history, and credit checks\. 

## U\.S\. Sales and Use Tax Report<a name="u.s.-sales-and-use-tax-report"></a>

 This monthly report provides sellers with information about U\.S\. sales and use taxes calculated by Amazon from transactions in AWS Marketplace\. You will only receive this report if you enroll in the AWS Marketplace Tax Calculation Service\. The report includes calculated U\.S\. sales and use tax for products that have a Product Tax Code applied\. Any products without a Product Tax Code will appear in this report with a tax value of $0\.00\. 

 To identify whether tax funds were collected, you should refer to your monthly Disbursement Report\. Transactions can be mapped between the Disbursement Report and U\.S\. Sales and Use Tax Report by using the shared Transaction Reference ID\. 

## Daily Ref Tag<a name="daily-ref-tag"></a>

 This report presents the information from your [Marketing Dashboard](https://aws.amazon.com/marketplace/management/marketing/) and provides insight into clicks and conversions for ref tag links that customers use to get to your AWS Marketplace listing\. 
+  The report covers the previous 24 hour calendar period, and is can be downloaded from the [Marketing Dashboard](https://aws.amazon.com/marketplace/management/marketing/) of your AWS Marketplace Management Portal\. 
+  This report is not emailed\. 
+  Video for [Getting Started with AWS Marketplace Marketing Analytics](https://www.youtube.com/watch?v=hOxkyU73hJ0)\. 
+  [Additional help](https://aws.amazon.com/marketplace/help/201349870) on setting up ref tags\. 
+  You cannot make calls to the Commerce Analytics Service \(CAS\) for this report\. 
+  The filename is formatted as reftag\_daily\_breakdown\_report\_YYYY\-MM\-DD\.csv where the date is the date the report was generated\. 

 The report contains 1 section relating to customer billing activity: 

1.  Clicks and Conversions \- A breakdown of every ref tag used with your products and the amount of clicks, conversions, estimated usage, and estimated revenue associated with them\. 

## Weekly Ref Tag<a name="weekly-ref-tag"></a>

 This report presents the information from your [Marketing Dashboard](https://aws.amazon.com/marketplace/management/marketing/), summarized by week, and provides insight into clicks and conversions for ref tag links that customers use to get to your AWS Marketplace listing\. The query used to generate your reftag reports looks for distinct customer sessions \(grouped by day, reftag, and page ASIN\) and reports them as clicks\. The report does not measure conversion to paid\. 
+  The report covers the previous 7 Day calendar period, and is normally generated and available weekly, usually by 5:00pm PST \(Midnight UTC\)\. The specific period covered is included in the report\. 
+  Video for [Getting Started with AWS Marketplace Marketing Analytics](https://www.youtube.com/watch?v=hOxkyU73hJ0)\. 
+  [Additional help](https://aws.amazon.com/marketplace/help/201349870) on setting up ref tags\. 
+  You cannot make calls to the Commerce Analytics Service \(CAS\) for this report\. 
+  Please note only ref tags that contain '\_ptnr\_' are included in this report plus any SEM/Online ad ref tags that start with 'ads\_'\. 
+  The filename is formatted as weekly\_reftag\_report\_YYYY\-MM\-DD\.csv where the date is the date the report was generated\. 

 The report contains 1 section relating to customer billing activity: 

1.  Clicks and Conversions \- A breakdown of every ref tag used with your products and the amount of clicks and conversions associated with them\. 

## Reporting Frequently Asked Questions \(FAQ\)<a name="reporting-frequently-asked-questions-faq"></a>

### General<a name="general"></a>

 **Q: How can others from my team access reports in the AWS Marketplace Management Portal?** 

 **A:** You can control access to the AWS Marketplace Management Portal using IAM users\. 

 **Q: Can we unsubscribe from new report email notifications?** 

 **A:** Yes you can\. Send your request for cancel your subscription to **aws\-marketplace\-seller\-ops@amazon\.com**\. 

 **Q: Why didn’t I receive a Daily Customer Subscriber or Daily Business Report today?** 

 **A:** Reports are only generated when there is relevant data available that our system can enter in to them\. For example, if you have no subscribers on any of your products, then the Daily Customer Subscriber report won’t be generated\. If you still believe this is an error, contact **aws\-marketplace\-seller\-ops@amazon\.com** and the team will investigate\. 

 **Q: Can you share more information about customers?** 

 **A:** No\. Refer to the AWS Marketplace Enhanced Data Sharing Program documentation for more information\. 

 **Q: Can I run my own custom reports?** 

 **A:** No, this is not a currently supported feature\. However, you can use the [AWS Marketplace Commerce Analytics Service API](https://s3.amazonaws.com/awsmp-loadforms/AWS-Marketplace-Commerce-Analytics-Service-Onboarding-and-Technical-Guide.pdf) to download report data in a machine\-readable format\. 

 **Q: What is Refund in the Disbursement Report?** 

 **A:** Refund represents money returned from the seller to the customer\. It's represented as a negative amount since the money is deducted from the total disbursement amount\. 

 **Q: How can I tell which entries are for private offers?** 

 **A: Offer ID** and **Offer Visibility** columns have been added to reports to help distinguish private offer entries\. 

 **Q\. How is the US sales tax handled? ** 

 **A\.** For more information about AWS Marketplace’s Tax Calculation Service, please visit the AWS Marketplace Management Portal’s [Settings page](https://aws.amazon.com/marketplace/management/settings/)\. 

 **Q: Can a customer split a bill across several credit cards or do a direct invoicing?** 

 **A:** For pro\-rated Monthly fees, customers can do both split payments and direct invoicing\. However, for Annual subscriptions, customers can only do direct invoicing\. 

 **Q: Can I download past reports?** 

 **A:** You have access to past reports on management portal\. If you don't see the report there, contact **aws\-marketplace\-seller\-ops@amazon\.com** and we will look into it\. 

 **Q: Do reports include BYOL products?** 

 **A:** Information about your BYOL products are included in your Daily Business Report\. 

 **Q: Reftag Report \- How are clicks measured from your system?** 

 A: When you provide us with a reftag on the AWS Marketplace website, the reftag data is measured and recorded into logs\. These logs are then loaded into a table which is then queried on a daily basis\. 

 **Q: Reftag Report \- If I spin up an instance remotely from my product’s GUI or using an API, does your reporting account for that instance \(AMI\) and can I attribute that by the campaign? Or is the AMI instance only recorded when executed from the AWS console?** 

 A: We only track clicks and conversions made by the customer from the AWS Marketplace website\. 

### Commerce Analytics Service \(CAS\)<a name="commerce-analytics-service-cas"></a>

 **Q: What are the benefits of the AWS Marketplace Commerce Analytics Service?** 

 **A:** This new service allows you to programmatically access your AWS Marketplace data, removing the need for the inconvenient and potentially error\-prone process of manually downloading and processing reports from the AWS Marketplace Management Portal website\. Now, you can retrieve your products’ usage, subscribers, disbursement, and payment information using a modern API interface that allows you to automate the download and data ingestion of your information\. 

 **Q: What is the difference between the Commerce Analytics Service and a traditional API?** 

 **A:** The Commerce Analytics Service programmatically returns data asynchronously to a file in S3 rather than directly like a traditional API\. This is because of the nature of the data being potentially large and unbounded\. When the data has been delivered to your S3 bucket, we’ll send you a notification using Amazon Simple Notification Service \(SNS\)\. 

 **Q: What will happen to the existing reports on the AWS Marketplace Management Portal website?** 

 **A:** The current reports will remain accessible from the AWS Marketplace Management Portal website\. There are currently no plans to remove these reports\. In the future, as sellers fully integrate with the new service, we may consider retiring the existing reports\. 

 **Q: What are the requirements to start utilizing the service?** 

 **A:** You must be an active seller in the AWS Marketplace and you must enroll in the program through the AWS Marketplace Management Portal\. From the Management Portal, navigate to the Reports tab and follow the on\-screen instructions\. 

 **Q: What work will be required of my company to take advantage of the data provided in the AWS Marketplace Commerce Analytics Service?** 

 **A:** In order to automate your access to AWS Marketplace data, one of your technical resources needs to use the AWS Software Development Kit \(SDK\) to communicate with the AWS Marketplace Commerce Analytics Service\. The SDK supports multiple programming platforms such as \.NET, Java, Ruby, Command Line Interface, and many more\. 

 **Q: What can I do with the data provided in the AWS Marketplace Commerce Analytics Service?** 

 **A:** Data published by the Commerce Analytics Service is in a machine\-readable format, making it easy for you to import it into your existing systems, databases, or business intelligence and data analysis software\. You can also directly manipulate the data from the service, allowing you to aggregate and augment the data with your own internal data\. 

## Enhanced Data Sharing<a name="enhanced-data-sharing"></a>

 If you wish to receive de\-obfuscated customer information for the purpose of compensating your sales team for sales of products via AWS Marketplace, AWS Marketplace offers an additional Sales Compensation report\. Sales Compensation reports contain additional information such as customer email domain, customer AWS Account ID, and location in order to help you compensate your field, and use of such information is strictly limited to field sales team compensation\. 

 For more information about program requirements and how to sign up to receive this data, please review the AWS Marketplace Enhanced Data Sharing Program Guide\. 