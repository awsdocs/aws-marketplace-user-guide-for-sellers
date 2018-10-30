# Daily Business Report<a name="DailyBuisnessReport"></a>

 The daily business report helps sellers understand how AWS customers are using their products on a daily basis and projects the estimated revenue expected from that usage\. The data includes a unique identifier per customer that can identify an AWS customer across report types and across days\. With this identifier, sellers can track customer usage patterns and estimated customer spend and gain insights into free trial and annual data\. The report has six sections: 

## Publication Schedule<a name="publication-schedule"></a>

 Daily, by 5:00 PM Pacific Time\. 

## Section 1: Usage by Instance Type<a name="section-1-usage-by-instance-type"></a>

### Data Coverage Period<a name="data-coverage-period"></a>

 Includes data from the 24\-hour period of the previous day\. 


|  **Column Name**  |  **Available for all sellers**  |  **Available for sellers enrolled in the Enhanced Data Sharing Program**  |  **Description**  | 
| --- | --- | --- | --- | 
|  Customer Reference ID  |  ✔  |  ✔  |  A unique ID \(not AWS account number\) associated with the AWS account subscribed to the product to help track usage, revenue and subscriptions by customers  | 
|  User’s State  |  ✔  |  ✔  |  The billing address state associated with the AWS account subscribed to the product  | 
|  User’s Country  |  ✔  |  ✔  |  The billing address country associated with the AWS account subscribed to the product  | 
|  Product Title  |  ✔  |  ✔  |  The title of the product  | 
|  Product Code  |  ✔  |  ✔  |  A unique identifier representing the individual software product  | 
|  Instance Type  |  ✔  |  ✔  |  The instance type associated with usage \(e\.g\., t2\.micro\)  | 
|  Usage Units  |  ✔  |  ✔  |  The number of units of usage associated with the product  | 
|  Usage Unit Type  |  ✔  |  ✔  |  The usage units associated with the usage unit count \(e\.g\., hours\)  | 
|  Offering Description  |  ✔  |  ✔  |  The description of how the product is being offered \(e\.g\., hourly, free trial, annual\)  | 
|  Estimated Revenue  |  ✔  |  ✔  |  The estimated revenue resulting from associated usage\. This is estimated as the billing is finalized at the end of the month  | 
|  Currency  |  ✔  |  ✔  |  The currency \(e\.g\. USD\) associated with the estimated revenue  | 
|  Offer ID  |  ✔  |  ✔  |  The identifier for the offer the subscriber signed  | 
|  Offer Visibility  |  ✔  |  ✔  |  Indicates whether the offer is a public, private, or enterprise contract offer  | 
|  Customer AWS Account Number  |   |  ✔  |  The AWS account number, associated with the AWS account that software charges are billed to | 
|  Customer Country  |   |  ✔  |  The billin­g address country associated with the AWS account to which software charges are billed  | 
|  Customer State  |   |  ✔  |  The billing address state associated with the AWS account that software charges are billed to | 
|  Customer City  |   |  ✔  |  The billing address city associated with the AWS account that software charges are billed to | 
|  Customer Zip Code  |   |  ✔  |  The billing address zip code associated with the AWS account that software charges are billed to  | 
|  Customer Email Domain  |   |  ✔  |  The email domain associated with the AWS account that software charges are billed to \(e\.g\., amazon\.com\) | 
|  Solution Title  |  ✔  |  ✔  |  The name of the solution  | 
|  Solution ID  |  ✔  |  ✔  |  The unique identifier for the solution  | 

## Section 2: Fees<a name="section-2-fees"></a>

 This section includes fee\-based transactions, including Annual, Monthly, and SaaS Contracts products\. 

### Data Coverage Period<a name="data-coverage-period-1"></a>

 Includes data from the 24\-hour period occurring 72 hours before the report was published\. 


|  **Column Name**  |  **Available for all sellers**  |  **Available for sellers enrolled in the Enhanced Data Sharing Program**  |  **Description**  | 
| --- | --- | --- | --- | 
|  Customer Reference ID  |  ✔  |  ✔  |  A unique ID \(not AWS Account Number\) associated with the AWS account subscribed to the product to help track usage, revenue and subscriptions by customers  | 
|  User’s State  |  ✔  |  ✔  |  The billing address state associated with the AWS account subscribed to the product  | 
|  User’s Country  |  ✔  |  ✔  |  The billing address country associated with the AWS account subscribed to the product  | 
|  Product Title  |  ✔  |  ✔  |  The title of the product  | 
|  Product Code  |  ✔  |  ✔  |  A unique identifier representing the individual software product  | 
|  Amount  |  ✔  |  ✔  |  The software usage fee\. If there is a refund, this value will be negative\. If this entry is for an AWS Marketplace SaaS contract, the amount represents the software fee for the dimension, not the entire contract\.  | 
|  Currency  |  ✔  |  ✔  |  The currency \(e\.g\. USD\) associated with the estimated revenue  | 
|  Fee Description  |  ✔  |  ✔  |  The reason for the fee \(e\.g\. monthly fee, annual fee, SaaS Contracts fee, refund, etc\.\)  | 
|  Customer AWS Account Number  |   |  ✔  |  The AWS account number­­ associated with the AWS account to which software charges are billed  | 
|  Customer Country  |   |  ✔  |  The billin­g address country associated with the AWS account to which software charges are billed  | 
|  Customer State  |   |  ✔  |  The billing address state associated with the AWS account to which software charges are billed  | 
|  Customer City  |   |  ✔  |  The billing address city associated with the AWS account to which software charges are billed  | 
|  Customer Zip Code  |   |  ✔  |  The billing address zip code associated with the AWS account to which software charges are billed  | 
|  Customer Email Domain  |   |  ✔  |  The email domain associated with the AWS account to which software charges are billed, e\.g\. “amazon\.com”  | 
|  Start Date  |  ✔  |  ✔  |  The start date for an AWS Marketplace SaaS contract  | 
|  End Date  |  ✔  |  ✔  |  The end date for an AWS Marketplace SaaS contract  | 
|  Quantity  |  ✔  |  ✔  |  The number of units for a dimension specified in the contract  | 
|  Dimension  |  ✔  |  ✔  |  The dimension specified in the contract  | 
|  Solution Title  |  ✔  |  ✔  |  The name of the solution  | 
|  Solution ID  |  ✔  |  ✔  |  The unique identifier for the solution  | 

## Section 3: Free Trial Conversions<a name="section-3-free-trial-conversions"></a>

### Data Coverage Period<a name="data-coverage-period-2"></a>

 Includes data from the 24\-hour period of the previous day\. 


|  **Column Name**  |  **Available for all sellers**  |  **Available for sellers enrolled in the Enhanced Data Sharing Program**  |  **Description**  | 
| --- | --- | --- | --- | 
|  Product Title  |  ✔  |  ✔  |  The title of the product  | 
|  Product Code  |  ✔  |  ✔  |  A unique identifier representing the individual software product  | 
|  New Free Trials  |  ✔  |  ✔  |  The count of the new free trials initiated that day  | 
|  Total Current Free Trials  |  ✔  |  ✔  |  The total count of all active free trial subscriptions  | 
|  Converted Free Trials  |  ✔  |  ✔  |  The total count of subscriptions that moved from free trial to paid usage that day  | 
|  Non\-Converted Free Trials  |  ✔  |  ✔  |  The total count of the total subscriptions that ended the free trial and did not convert to paid usage  | 
|  Solution Title  |  ✔  |  ✔  |  The name of the solution  | 
|  Solution ID  |  ✔  |  ✔  |  The unique identifier for the solution  | 

## Section 4: New Instances<a name="section-4-new-instances"></a>

### Data Coverage Period<a name="data-coverage-period-3"></a>

 Includes data from the 24\-hour period of the previous day\. 


|  **Column Name**  |  **Available for all sellers**  |  **Available for sellers enrolled in the Enhanced Data Sharing Program**  |  **Description**  | 
| --- | --- | --- | --- | 
|  Customer Reference ID  |  ✔  |  ✔  |  A unique ID \(not AWS Account Number\) associated with the AWS account subscribed to the product to help track usage, revenue and subscriptions by customers  | 
|  User’s State  |  ✔  |  ✔  |  The billing address state associated with the AWS account subscribed to the product  | 
|  User’s Country  |  ✔  |  ✔  |  The billing address country associated with the AWS account subscribed to the product  | 
|  Product Title  |  ✔  |  ✔  |  The title of the product  | 
|  Product Code  |  ✔  |  ✔  |  A unique identifier representing the individual software product  | 
|  Type  |  ✔  |  ✔  |  The AWS EC2 instance type  | 
|  Count  |  ✔  |  ✔  |  The count of AWS EC2 instances  | 
|  Customer AWS Account Number  |   |  ✔  |  The AWS account number­­ associated with the AWS account to which software charges are billed  | 
|  Customer Country  |   |  ✔  |  The billin­g address country associated with the AWS account to which software charges are billed  | 
|  Customer State  |   |  ✔  |  The billing address state associated with the AWS account to which software charges are billed  | 
|  Customer City  |   |  ✔  |  The billing address city associated with the AWS account to which software charges are billed  | 
|  Customer Zip Code  |   |  ✔  |  The billing address zip code associated with the AWS account to which software charges are billed  | 
|  Customer Email Domain  |   |  ✔  |  The email domain associated with the AWS account to which software charges are billed, e\.g\. “amazon\.com”  | 
|  Solution Title  |  ✔  |  ✔  |  The name of the solution  | 
|  Solution ID  |  ✔  |  ✔  |  The unique identifier for the solution  | 

## Section 5: New Product Subscribers<a name="section-5-new-product-subscribers"></a>

### Data Coverage Period<a name="data-coverage-period-4"></a>

 Includes data from the 24\-hour period of the previous day\. 


|  **Column Name**  |  **Available for all sellers**  |  **Available for sellers enrolled in the Enhanced Data Sharing Program**  |  **Description**  | 
| --- | --- | --- | --- | 
|  Customer Reference ID  |  ✔  |  ✔  |  A unique ID \(not AWS Account Number\) associated with the AWS account subscribed to the product to help track usage, revenue and subscriptions by customers  | 
|  User’s State  |  ✔  |  ✔  |  The billing address state associated with the AWS account subscribed to the product  | 
|  User’s Country  |  ✔  |  ✔  |  The billing address country associated with the AWS account subscribed to the product  | 
|  Product Title  |  ✔  |  ✔  |  The title of the product  | 
|  Product Code  |  ✔  |  ✔  |  A unique identifier representing the individual software product  | 
|  Offer ID  |  ✔  |  ✔  |  The identifier for the offer the subscriber signed  | 
|  Offer Visibility  |  ✔  |  ✔  |  Indicates the offer to be a public, private, or enterprise contract offer  | 
|  Customer Country  |   |  ✔  |  The billing address country associated with the AWS account to which software charges are billed  | 
|  Customer State  |   |  ✔  |  The billing address state associated with the AWS account to which software charges are billed  | 
|  Customer City  |   |  ✔  |  The billing address city associated with the AWS account to which software charges are billed  | 
|  Customer Zip Code  |   |  ✔  |  The billing address zip code associated with the AWS account to which software charges are billed  | 
|  Customer Email Domain  |   |  ✔  |  The email domain associated with the AWS account to which software charges are billed, e\.g\. “amazon\.com”  | 
|  Solution Title  |  ✔  |  ✔  |  The name of the solution  | 
|  Solution ID  |  ✔  |  ✔  |  The unique identifier for the solution  | 

## Section 6: Canceled Product Subscribers<a name="section-6-canceled-product-subscribers"></a>

### Data Coverage Period<a name="data-coverage-period-5"></a>

 Includes data from the 24\-hour period of the previous day\. 


|  **Column Name**  |  **Available for all sellers**  |  **Available for sellers enrolled in the Enhanced Data Sharing Program**  |  **Description**  | 
| --- | --- | --- | --- | 
|  Customer Reference ID  |  ✔  |  ✔  |  A unique ID \(not AWS Account Number\) associated with the AWS account subscribed to the product to help track usage, revenue and subscriptions by customers  | 
|  User’s State  |  ✔  |  ✔  |  The billing address state associated with the AWS account subscribed to the product  | 
|  User’s Country  |  ✔  |  ✔  |  The billing address country associated with the AWS account subscribed to the product  | 
|  Product Title  |  ✔  |  ✔  |  The title of the product  | 
|  Product Code  |  ✔  |  ✔  |  A unique identifier representing the individual software product  | 
|  Subscribed Date  |  ✔  |  ✔  |  The date when the subscription started  | 
|  Offer ID  |  ✔  |  ✔  |  The identifier for the offer the subscriber signed  | 
|  Offer Visibility  |  ✔  |  ✔  |  Indicates the offer to be a public, private, or enterprise contract offer  | 
|  Customer AWS Account Number  |   |  ✔  |  The AWS account number­­ associated with the AWS account to which software charges are billed  | 
|  Customer Country  |   |  ✔  |  The billin­g address country associated with the AWS account to which software charges are billed  | 
|  Customer State  |   |  ✔  |  The billing address state associated with the AWS account to which software charges are billed  | 
|  Customer City  |   |  ✔  |  The billing address city associated with the AWS account to which software charges are billed  | 
|  Customer Zip Code  |   |  ✔  |  The billing address zip code associated with the AWS account to which software charges are billed  | 
|  Customer Email Domain  |   |  ✔  |  The email domain associated with the AWS account to which software charges are billed, e\.g\. “amazon\.com”  | 
|  Solution Title  |  ✔  |  ✔  |  The name of the solution  | 
|  Solution ID  |  ✔  |  ✔  |  The unique identifier for the solution  | 