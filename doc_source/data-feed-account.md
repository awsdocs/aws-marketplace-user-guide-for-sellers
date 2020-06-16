# Account data feed<a name="data-feed-account"></a>

This data feed provides information about all the accounts you interact with: your own, any channel partners you work with, buyers, payers, and all taxed accounts\. 

Account data is immutable, and it is not associated with a version number\. Changes to fields are appended, so this data feed may have several rows with the same `account_id` and different `valid_from` values\. For information about data history fields, see [Historization of the data](data-feed.md#data-feed-historization)\.

The account data feed is refreshed every 24 hours, so new data is available daily\.

The following table explains the names and descriptions of the data feed's columns\. 


| Column name  | Description  | 
| --- | --- | 
| account\_id  | The globally unique identifier \(GUID\) of the account\.  | 
| aws\_account\_id  | The AWS account number of the seller's AWS account, which is unique by AWS partition\.  | 
| encrypted\_account\_id | The unique, encrypted ID for an individual buyer of your application\. The value for encrypted\_account\_id is used by the AWS Marketplace Metering Service, for example, as the value for CustomerIdentifier that is returned by the [https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_ResolveCustomer.html](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/API_ResolveCustomer.html) action\.  | 
| mailing\_address\_id | The mailing address reference for this account\. | 
| tax\_address\_id | The tax address reference for this account\. | 
| tax\_registration\_number | For non\-US accounts, the tax registration number for this account\.  | 
| tax\_legal\_name | For non\-US accounts, the legal company name\. This is the name used on tax invoices\. | 

## Example of account data feed<a name="data-feed-account-sample-data"></a>

The following shows an example of the account data feed\. For readability, the data history columns aren't shown\. For information about data history fields, see [Historization of the data](data-feed.md#data-feed-historization)\.


| account\_id  | aws\_account\_id  | encrypted\_account\_id | mailing\_address\_id | tax\_address\_id | tax\_registration\_number | tax\_legal\_name | 
| --- | --- | --- | --- | --- | --- | --- | 
| xk0CSmiAm6PQ4QqEog9iiaochIzuPlkMfba7a1oDlZ | 444456660000 | Zf7oMzheGWpH | 25o3k46eN6eViOfFiiqtxwX8e3kaOiPalUiofjyFa3 |  |  |  | 
| 7nyo5jwTRoPlyX81vx9ji04eEwTurO1Ff8biQi88W8 | 555567679999 | 373vuQUqmQ8v | 5oJ6vTjSzMrrF2gvh2Vj9HfqiM800MuLEHmyFY5Lr42s8 | 5oJ6vTjSzMrrF2gvh2Vj9HfqiM800MuLEHmyFY5Lr42s8 | SE823935083345 |  | 
| VIeGa2t9j3MuxioH9wc8lsndXXCgGCGUreeXriocM5 | 73739998888 | 8SPxAYmi8MwX | NLUc5UeiMlGFTrDWCoftDPhDUF1oaSd8xgl5QM8Db7 | V5NhBYBiYogwy0WMhndGU4AfMggmuoTC2j7Pm8ZKKNNyT | DE469558025 |  | 