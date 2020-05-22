# Offer product data feed<a name="data-feed-offer-product"></a>

One offer can have several products, and one product can be included in different offers\. This data feed lists information about the relationships between offers and products\. 

This data feed provides information about all product offers you've created as the seller of record\.

When you add or remove a product from an offer, you create an offer revision\. 

The offer product data feed is refreshed every 24 hours, so new data is available daily\.

The following table explains the names and descriptions of the data feed's columns\. For information about the data feed history columns, see [Historization of the data](data-feed.md#data-feed-historization)\.


| Column name  | Description  | 
| --- | --- | 
| offer\_id | The friendly identifier of this offer\. | 
| offer\_revision | Combines with offer\_id field to form the foreign key to the offer revision\. | 
| product\_id | The friendly identifier of the product, this is the foreign key to the product that this offer exposes\.  | 

## Example of Offer product data feed<a name="data-feed-offer-product-sample-data"></a>

The following shows an example of the Offer product data feed\. 


| offer\_id  | offer\_revision | product\_id | 
| --- | --- | --- | 
| offer\-dacpxznflfwin | 10 | prod\-o4grxfafcxxxx | 
| offer\-gszhmle5npzip | 24 | prod\-o4grxfafcxxxy | 