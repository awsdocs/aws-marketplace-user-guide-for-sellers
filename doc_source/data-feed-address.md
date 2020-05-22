# Address data feed<a name="data-feed-address"></a>

This data feed provides contact information for all the accounts you interact with: your own, any channel partners you work with, buyers, payers, and all taxed accounts\. Each time a new transaction occurs, the customer address for the transaction is scanned, and if it's not in your data feed, a new entry is added to your data feed file\.

Address data is immutable\. 

The address data feed is refreshed every 24 hours, so new data is available daily\.

The following table explains the names and descriptions of the data feed's columns\. 


| Column name  | Description  | 
| --- | --- | 
| address\_id  | The unique key of the address\.  | 
| aws\_account\_id  | The AWS account number of this address\.  | 
| email\_domain  | The domain for the email address on file for this account\.  | 
| company\_name  | The company name on file for this account\.  | 
| country  | The ISO 3166 alpha\-2 country code on file for this address\.  | 
| state\_or\_region  | The state or region on file for this address\.  | 
| city  | The city on file for this address\.  | 
| postal\_code  | The postal code on file for this address\.  | 
| address\_line\_1  | The first line of the address on file for this address\.  | 
| address\_line\_2  | The second line of the address on file for this address\.  | 
| address\_line\_3  | The third line of the address on file for this address\.  | 

## Example of address data feed<a name="data-feed-address-sample-data"></a>

The following shows an example of the address data feed\. In the data feed, this information is presented in a single table\. For readability, the data is shown in two tables here, and the data history columns aren't shown\. For information about data history fields, see [Historization of the data](data-feed.md#data-feed-historization)\. 


| address\_id  | aws\_account\_id  | email\_domain  | company\_name  | country  | state\_or\_region  | city  | postal\_code  | 
| --- | --- | --- | --- | --- | --- | --- | --- | 
| V5NhBYBiYogwy0WMhndGU4AfMggmuoTC2j7Pm8ZKKNNyT | 444456660000 | a\.com | Mateo Jackson's Company | DE |  | Hamburg | 67568 | 
| G68xdbkZQDVVHzfBGw6yf5yos0A6NiSVWHmH5ViLjf | 555567679999 | b\.com | Mary Major's Company | US | OH | Dayton | 57684 | 
| NLUc5UeiMlGFTrDWCoftDPhDUF1oaSd8xgl5QM8Db7 | 555567679999 | c\.com | Our Seller | US | NY | New York | 89475 | 


| address\_line\_1  | address\_line\_2  | address\_line\_3  | 
| --- | --- | --- | 
|   |   |  | 
|  |   |  | 
|  | 19th Floor |  | 