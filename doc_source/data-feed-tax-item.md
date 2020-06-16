# Tax item data feed<a name="data-feed-tax-item"></a>

This data feed provides information on tax calculations for a customer invoice\.

There can be multiple line items \(`line_item_id`\) for a given product \(`product_id`\) of a given customer invoice \(`invoice_id`\), one or more for each tax jurisdiction\. This happens, for example, with usage\-based bills for customers who are using different AWS region rules by different AWS entities \(say, the U\.S\. and Ireland\)\. To learn more about where AWS collects sales tax, VAT, or GST on your sales and remits such taxes to the local tax authorities, in the name of AWS, Inc\., see [Amazon Web Service Tax Help](https://aws.amazon.com/tax-help/)\.

The tax item data feed is refreshed every 24 hours, so new data is available daily\.

Tax item data is immutable\. 

The following table explains the names and descriptions of the data feed's columns\. For information about data history columns, see [Historization of the data](data-feed.md#data-feed-historization)\.


| Column name  | Description  | 
| --- | --- | 
| tax\_item\_id | A unique identifier for a tax item record\. | 
| invoice\_id | The AWS invoice ID\. You can use this value with the value of product\_id to find related tax billing events\. | 
| line\_item\_id | A unique identifier for a customer bill line item\. Refund transactions have the same line item ID as their forward tax transactions\. | 
| customer\_bill\_id | The unique identifier of the customer bill\. Buyers can share this identifier with the seller to help identify and resolve tax calculation questions\.  | 
| tax\_liable\_party | Either `AWS` or `Seller`\. If the seller is the tax liable party, taxes are collected \. If AWS is the tax liable party, sales tax is collected and remitted by AWS\. For more information, see [AWS Marketplace Sellers & Tax Collection](http://aws.amazon.com/tax-help/marketplace)\. If no taxes are collected, there is no value shown here\. The seller needs to determine whether some taxes were collected for each invoice, as the seller is liable for tax collection\.  | 
| transaction\_type\_code | The type of transaction\. Possible values are as follows: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/data-feed-tax-item.html) Refund transactions share the line item ID with their original forward transactions\. | 
| product\_id | A foreign key to the product\. | 
| product\_tax\_code | A standard code to identify the tax properties for a product\. Sellers choose the properties when creating or modifying the product\. | 
| invoice\_date | The date the invoice was created\.  | 
| taxed\_customer\_account\_id | A foreign key to the account entity who is taxed\. | 
| taxed\_customer\_country | The ISO 3166 alpha 2 country code of the address used for tax calculations\.  | 
| taxed\_customer\_state\_or\_region | The state, region, or province used for tax calculations\. | 
| taxed\_customer\_city | The city used for tax calculations\. | 
| taxed\_customer\_postal\_code | The postal code used for tax calculations\. | 
| tax\_location\_code\_taxed\_jurisdiction | The vertex geocode that is associated with the taxed location\.  | 
| tax\_type\_code | The type of tax that is applied to the transaction\. The possible values are None, Sales, and SellerUse\. | 
| jurisdiction\_level | The jurisdiction level of the address that is used for tax location\. The possible values are State, County, City, and District\. | 
| taxed\_jurisdiction | The name of the tax jurisdiction\.  | 
| display\_price\_taxability\_type | Whether the price that buyers see is inclusive or exclusive of taxes\. All AWS Marketplace offerings are exclusive of taxes\.  | 
| taxable\_amount | The amount of the transaction that is taxable, at this jurisdiction level\. | 
| nontaxable\_amount | The amount of the transaction that is nontaxable, at this jurisdiction level\. | 
| tax\_jurisdiction\_rate | The tax rate that is applied, at this jurisdiction level\. | 
| tax\_amount | The amount of tax that is charged, at this jurisdiction level\. | 
| tax\_currency | The ISO 4217 alpha 3 currency code for above amounts\. | 
| tax\_calculation\_reason\_code | Whether the transaction is taxable, not taxable, exempt, or zero\-rated, organized by the jurisdiction level\. | 
| date\_used\_for\_tax\_calculation | The date that is used for calculating tax on the transaction\. | 
| customer\_exemption\_certificate\_id | The certificate ID of the exemption certificate\. | 
| customer\_exemption\_certificate\_id\_domain | The location where the certificate is stored on Amazon systems\.  | 
| customer\_exemption\_certificate\_level | The jurisdiction level that supplied the exemption\. | 
| customer\_exemption\_code | The code that specifies the exemption; for example, RESALE\. | 
| customer\_exemption\_domain | The Amazon system that is used to capture the customer exemption information, if available\. | 
| transaction\_reference\_id | An identifier that allows you to cross\-reference data from the following reports: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/data-feed-tax-item.html)  | 

## Example of tax item data feed<a name="data-feed-tax-item-sample-data"></a>

The following shows an example of the tax item data feed\. In the data feed, this information is presented in a single table\. For readability, the data is shown in multiple tables here, and all columns aren't shown\. 


| tax\_item\_id | invoice\_id | line\_item\_id | customer\_bill\_id | 
| --- | --- | --- | --- | 
| 6p2ni6tu041xagvhbyanbgxl3xameha16txjoav\_0001 | 781216640 | 71000000000000000000 | 2210000000000000000 | 
| 6p2ni6tu041xagvhbyanbgxl3xameha16txjoav\_0002 | 781216640 | 53000000000000000000 | 2210000000000000000 | 
| flr4jobxjzww8czdsrq4noue2uxd56j39wxw0k7\_0001 | 250816266 | 76400000000000000000 | 5720000000000000000 | 
| gfkjjobxjzw56jgkrsrqgjtk52uxd56j39wgj567d\_0002 | 280336288 | 76400000000000000000 | 5724390000000000000 | 
| wwk1qpvb8ran3geiw8e3mp6dgs2qj7wpkuwhgk1\_0001 | 451431024 | 99300000000000000000 | 1230000000000000000 | 
| wwk1qpvb8ran3geiw8e3mp6dgs2qj7wpkuwhgk1\_0002 | 451431024 | 99300000000000000000 | 3120000000000000000 | 
| fnohdid8kwgqq9lvii2k30spn3ftgwihbe8h75x\_0001 | 229987654 | 92100000000000000000 | 6390000000000000000 | 


| tax\_liable\_party | transaction\_type\_code | product\_id | product\_tax\_code | invoice\_date | 
| --- | --- | --- | --- | --- | 
| Seller | AWS | prod\-o4grxfafcxxxx | AWSMP\_SOFTWARE\_RA | 2018\-12\-31T00:00:00Z | 
| Seller | AWS | prod\-o4grxfafcxxxx | AWSMP\_SOFTWARE\_RA | 2018\-12\-31T00:00:00Z | 
| Seller | AWS | prod\-t3grxfafcxxxy | AWS\_REMOTE\_ACCESS\_SOFTWARE | 2018\-08\-31T00:00:00Z | 
| Seller | REFUND | prod\-t3grxfafcxxxy | AWS\_REMOTE\_ACCESS\_SOFTWARE | 2018\-08\-31T00:00:00Z | 
| Seller | AWS | prod\-x8faxxfafcxxy | AWS\_REMOTE\_ACCESS\_SOFTWARE | 2018\-08\-31T00:00:00Z | 
| Seller | TAXONLYREFUND | prod\-x8faxxfafcxxy | AWS\_REMOTE\_ACCESS\_SOFTWARE | 2018\-05\-31T00:00:00Z | 
| AWS | AWS | prod\-wghj8xfafrhgj | AWS\_REMOTE\_ACCESS\_SOFTWARE | 2019\-07\-31T00:00:00Z | 


| taxed\_customer\_account\_id | taxed\_customer\_country | taxed\_customer\_state\_or\_region | taxed\_customer\_city | taxed\_customer\_postal\_code | 
| --- | --- | --- | --- | --- | 
| VIeGa2t9j3MuxioH9wc8lsndXXCgGCGUreeXriocM5 | US | GA | MILTON | 48573\-4839 | 
| VIeGa2t9j3MuxioH9wc8lsndXXCgGCGUreeXriocM5 | US | GA | MILTON | 48573\-4839 | 
| 7nyo5jwTRoPlyX81vx9ji04eEwTurO1Ff8biQi88W8 | US | NC | DURHAM | 27517\-4834 | 
| 7nyo5jwTRoPlyX81vx9ji04eEwTurO1Ff8biQi88W8 | US | NC | DURHAM | 27517\-4834 | 
| 7nyo5jwTRoPlyX81vx9ji04eEwTurO1Ff8biQi88W8 | US | TX | NOT APPLICABLE | 75844\-1235 | 
| 7nyo5jwTRoPlyX81vx9ji04eEwTurO1Ff8biQi88W8 | US | TX | HOUSTON | 75844\-1235 | 
| 192a0421313e41f069b52962ed7babf716291b688 | US | CT | NEW HAVEN | 06002\-2948 | 


| tax\_location\_code\_taxed\_jurisdiction | tax\_type\_code | jurisdiction\_level | taxed\_jurisdiction | display\_price\_taxability\_type | taxable\_amount | nontaxable\_amount | 
| --- | --- | --- | --- | --- | --- | --- | 
| 460473664 | Sales | State | GA | Exclusive | 100 | 0 | 
| 66301164 | Sales | County | FULTON | Exclusive | 0 | 100 | 
| 692938178 | SellerUse | State | NC | Exclusive | 58\.1 | 523\.8 | 
| 692938178 | SellerUse | State | NC | Exclusive | \-58\.1 | 523\.8 | 
| 356794387 | Sales | State | TX | Exclusive | 1105\.14 | 0 | 
| 528887443 | Sales | City | HOUSTON | Exclusive | \-36 | 0 | 
| 171248162 | Sales | State | CT | Exclusive | 0 | 114\.55 | 


| tax\_jurisdication\_rate | tax\_amount | tax\_currency | tax\_calculation\_reason\_code | date\_used\_for\_tax\_calculation | 
| --- | --- | --- | --- | --- | 
| 0\.206 | 20\.6 | USD | Taxable | 2018\-10\-31T00:00:00Z | 
| 0 | 0 | USD | NonTaxable | 2018\-10\-31T00:00:00Z | 
| 0\.1 | 5\.8 | USD | Taxable | 2018\-07\-31T00:00:00Z | 
| 0\.1 | \-5\.8 | USD | Taxable | 2018\-07\-31T00:00:00Z | 
| 0\.06 | 66\.3 | USD | Taxable | 2018\-07\-31T00:00:00Z | 
| 0\.01 | \-0\.36 | USD | NonTaxable | 2018\-07\-31T00:00:00Z | 
| 0 | 0 | USD | Exempt | 2019\-06\-30T00:00:00Z | 