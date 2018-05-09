# U\.S\. Sales and Use Tax Report<a name="u.s.-sales-and-use-tax-report"></a>

 This monthly report provides sellers with information about U\.S\. sales and use taxes collected by Amazon from sales and use transactions in AWS Marketplace\. The report only includes products enrolled by sellers in the AWS Marketplace U\.S\. Sales Tax program\. 

## Publication Schedule<a name="publication-schedule-5"></a>

 Monthly, on the 15th of the month, by 5:00 PM Pacific Time\. 

## Section 1: US Sales and Use Tax Records<a name="section-1-us-sales-and-use-tax-records"></a>

### Data Coverage Period<a name="data-coverage-period-17"></a>

 Includes US sales tax amounts resulting from software charges from the previous calendar month\. 


|  **Column Name**  |  **Purpose**  | 
| --- | --- | 
|  Line Item Id  |  Unique identifier of a line item\. Refund transactions have the same Line Item Id as their forward tax transactions  | 
|  Customer Bill Id  |  Unique identifier of a customer bill  | 
|  Product Name  |  Title of the product purchased  | 
|  Product Code  |  A unique identifier representing the individual software product  | 
|  Product Tax Code  |  A standard code to identify the tax properties of a product, selected by the seller  | 
|  Seller Id  |  Unique identifier of a seller of record for the transaction  | 
|  Seller Name  |  The legal name of the seller  | 
|  Transaction Date  |  The date of the transaction  | 
|  Total Adjusted Price  |  The final price for the transaction  | 
|  Total Tax  |  The total tax charged for the transaction  | 
|  Base Currency Code  |  This is the base currency code for all AWS Marketplace transactions, which is always USD  | 
|  Bill to City  |  The city of the customer's billing address  | 
|  Bill to State  |  The state of the customer's billing address  | 
|  Bill to Postal Code  |  The postal code of the customer's billing address  | 
|  Bill to Country  |  The country of the customer's billing address  | 
|  Transaction Type Code  |   The type code of the transaction: AWS, REFUND, TAXONLYREFUND\.  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/u.s.-sales-and-use-tax-report.html)  Refund transaction share Line Item Id with their original forward transactions   | 
|  Display Price Taxability Type  |  Taxability type for the price displayed to customers\. All AWS Marketplace offerings are exclusive  | 
|  Tax Location Code Taxed Jurisdiction  |  Vertex Geocode associated with the taxed location  | 
|  Tax Type Code  |  Type of tax applied to the transaction\. Possible values: None, Sales, SellerUse  | 
|  Jurisdiction Level  |  Jurisdiction level of address used for tax location\.  Possible values: State, County, City, District  | 
|  Taxed Jurisdiction  |  Name of the taxed jurisdiction  | 
|  Taxable Sale Amount  |  Amount of transaction that is taxable, by jurisdiction level  | 
|  Nontaxable Sale Amount  |  Amount of transaction that is nontaxable, by jurisdiction level  | 
|  Tax Amount  |  Tax charged at the jurisdiction level  | 
|  Tax Jurisdiction Tax Rate  |  Tax rate applied at the jurisdiction level  | 
|  Tax Calculation Reason Code  |  By jurisdiction level, an indicator of whether the transaction is taxable, not taxable, exempt, or zero\-rated  | 
|  Date Used For Tax Calculation  |  Date used for calculating tax on the transaction  | 
|  Customer Exemption Certificate Id  |  Certificate ID representing the exemption certificate  | 
|  Customer Exemption Certificate Id Domain  |  This value corresponds to where the certificate is being stored within Amazon systems  | 
|  Customer Exemption Certificate Level  |  The jurisdiction level that supplied the exemption  | 
|  Customer Exemption Code  |  Code specifying the exemption, e\.g\. “RESALE”  | 
|  Customer Exemption Domain  |  This is the Amazon system that is used to capture the customer exemption information, if any  | 
|  Customer Reference Id  |  A unique ID \(not AWS Account Number\) associated with the AWS account to which fees are billed, to help track usage, revenue, and subscriptions by customers  | 
|  Transaction Reference Id  |  A unique identifier representing the transaction which can be used to correlate transactions across AWS Marketplace reports  | 