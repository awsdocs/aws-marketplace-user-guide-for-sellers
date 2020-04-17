# US sales and use tax report<a name="u.s.-sales-and-use-tax-report"></a>

This monthly report provides sellers with information about US sales and use tax that AWS collects from sales and use transactions in AWS Marketplace\. The report includes both products that sellers enroll in the AWS Marketplace US sales tax collection service and products that AWS is required to collect and remit tax on\.

For sales of products enrolled in the tax calculation service, the report includes calculated US sales and use tax for products with a product tax code\. Any products without a product tax code appear in this report with a tax value of $0\.00 USD\. For sales of products that are not eligible for the tax calculation service because of enacted marketplace facilitator rules, you will see amounts that AWS has collected and remitted as `AWS`, based on our internal tax decisions\. For more information, see [AWS Marketplace Sellers & Tax Collection](http://aws.amazon.com/tax-help/marketplace) on Amazon Web Services Tax Help\.

To map transactions between the disbursement report and this report, use the `Transaction Reference ID`\.

This report is available on the AWS Marketplace Management Portal under the **Reports** tab\. If you're enrolled in the AWS Marketplace commerce analytics service, you can use API calls to pull down sections of this report\. For more information, see [AWS Marketplace Commerce Analytics Service](commerce-analytics-service.md)\. 

## Publication schedule<a name="publication-schedule-5"></a>

This report is published monthly on the fifteenth day of each month at 00:00 UTC\. The report covers the previous calendar month from the first day of the month at 00:00 UTC through the last day of the month at 23:59 UTC\. For example, the report that is published on May 15 covers from April 1 at 00:00 UTC through April 30 at 23:59 UTC\. 

## US sales and use tax records<a name="section-1-us-sales-and-use-tax-records"></a>

 This section lists data for US sales tax amounts that result from software charges\. 


| Column name  | Description  | 
| --- | --- | 
| Line Item ID  | A unique identifier for a line item\. Refund transactions have the same line item ID as their forward tax transactions\.  | 
| Customer Bill ID  | The unique identifier for a customer bill\.  | 
| Product Name  | The name of the product purchased\.  | 
| Product Code  | The unique identifier for the product\. | 
| Product Tax Code  | A standard code to identify the tax properties for a product\. You choose the properties when you create or modify the product\.  | 
| Seller ID  | A unique identifier for the seller of record of the transaction\.  | 
| Seller Name  | The legal name of the seller\.  | 
| Transaction Date  | The date of the transaction\.  | 
| Total Adjusted Price  | The final price for the transaction\.  | 
| Total Tax  | The total tax that is charged for the transaction\.  | 
| Base Currency Code  | The base currency code for all AWS Marketplace transactions\. This entry is always USD\.  | 
| Bill to City  | The billing address city that is associated with the payer account that we bill software charges to\. | 
| Bill to State  | The billing address zip code that is associated with the payer account that the software charges are billed to\. | 
| Bill to Postal Code  | The billing address postal code that is associated with the payer account that the software charges are billed to\.  | 
| Bill to Country  | The two\-character country code that is associated with the payer account that the software charges are billed to\. This report uses ISO 3166\-1 alpha\-2 standard\.  | 
| Transaction Type Code  |  The type code of the transaction\. Valid values: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/u.s.-sales-and-use-tax-report.html) Refund transactions share the line item ID with their original forward transactions\.   | 
| Display Price Taxability Type  | The taxability type for the price that appears to customers\. All AWS Marketplace offerings are exclusive\.  | 
| Tax Location Code Taxed Jurisdiction  | The vertex geocode that is associated with the taxed location\.  | 
| Tax Type Code  | The type of tax that is applied to the transaction\. The possible values are None, Sales, and SellerUse\.  | 
| Jurisdiction Level  | The jurisdiction level of the address that is used for tax location\.  The possible values are State, County, City, and District\.  | 
| Taxed Jurisdiction  | The name of the taxed jurisdiction\.  | 
| Taxable Sale Amount  | The amount of the transaction that is taxable, by jurisdiction level\.  | 
| Nontaxable Sale Amount  | The amount of the transaction that is nontaxable, by jurisdiction level\.  | 
| Tax Amount  | The tax that is charged at the jurisdiction level\.  | 
| Tax Jurisdiction Tax Rate  | The tax rate that is applied at the jurisdiction level\.  | 
| Tax Calculation Reason Code  | Whether the transaction is taxable, not taxable, exempt, or zero\-rated, organized by the jurisdiction level\.  | 
| Date Used For Tax Calculation  | The date that is used for calculating tax on the transaction\.  | 
| Customer Exemption Certificate ID  | The certificate ID of the exemption certificate\.  | 
| Customer Exemption Certificate ID Domain  | Where the certificate is being stored in Amazon systems\.  | 
| Customer Exemption Certificate Level  | The jurisdiction level that supplied the exemption\.  | 
| Customer Exemption Code  | The code that specifies the exemption: for example, RESALE\.  | 
| Customer Exemption Domain  | The Amazon system that is used to capture the customer exemption information, if information is available\.  | 
| Customer Reference ID  | A unique identifier that isn't the account ID\. It helps track usage, revenue and subscriptions by customers\. | 
| Transaction Reference ID  | A unique identifier for the transaction that helps you correlate transactions across AWS Marketplace reports\.  | 
| Payer Reference ID  | A unique identifier that isn't the account ID\. It's associated with the account that fees are billed to\. It helps with tracking usage, revenue, and subscriptions by customers across all of the AWS Marketplace financial reports\. | 
| Tax Liable Party | This field will either be populated with Seller or AWS\. If the seller is the tax liable party, they are responsible for their own collection and remittance obligations based on their tax decision\. If AWS is the tax liable party sales tax will be collected and remitted by AWS\. For more information, see [AWS Marketplace Sellers & Tax Collection](http://aws.amazon.com/tax-help/marketplace) on Amazon Web Services Tax Help\. | 