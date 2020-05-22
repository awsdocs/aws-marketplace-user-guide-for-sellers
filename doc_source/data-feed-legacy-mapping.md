# Legacy mapping data feed<a name="data-feed-legacy-mapping"></a>

This data feed lists how product IDs and offer IDs map to legacy globally unique identifiers \(GUIDs\)\. The legacy GUIDs were used in older reports, and the new IDs are used in data feeds and in AWS Marketplace APIs\.

This data feed provides information about all products you've created as the seller of record and all products you're authorized to resell\.

The legacy mapping data feed is refreshed every 24 hours, so new data is available daily\.

The following table explains the names and descriptions of the data feed's columns\. 


| Column name  | Description  | 
| --- | --- | 
| mapping\_type | Whether this is a product ID or offer ID\.  | 
| legacy\_id | The legacy ID for this product or offer\. | 
| new\_id | The friendly ID for this product or offer\. This ID is used as the primary key and with all current API actions\.  | 

## Example of legacy mapping data feed<a name="data-feed-legacy-mapping-sample-data"></a>

The following shows an example of the legacy mapping data feed\. For readability, the data history columns aren't shown\. For information about data history fields, see [Historization of the data](data-feed.md#data-feed-historization)\.


| mapping\_type | legacy\_id  | new\_id | 
| --- | --- | --- | 
| OFFER | 8a806c74\-dbd6\-403e\-9362\-bb08f417ff37 | offer\-dacpxznflfwin | 
| PRODUCT | 1368541d\-890b\-4b6c\-9bb9\-4a55306ab642 | prod\-o4grxfafcxxxy | 
| OFFER | 558d8382\-6b3a\-4c75\-8345\-a627b552f5f1 | offer\-gszhmle5npzip | 