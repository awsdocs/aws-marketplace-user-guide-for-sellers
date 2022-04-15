# Offer data feed<a name="data-feed-offer"></a>

The offer data feed provides information about all offers that you've created as the seller of record\. If a single offer has multiple revisions, all revisions are included in the data feed\.

When you make an offer revision and the data in an exposed field changes, a new record is created in the data feed for the same primary key \(`offer_id` plus `offer_revision`\)\. However, the `valid_from` field has a different value\. For more information about the data feed history columns, see [Historization of the data](data-feed.md#data-feed-historization)\.

The offer data feed is refreshed every 24 hours, so new data is available daily\.

The following table provides the names and descriptions of the data feed's columns\. 


| Column name  | Description  | 
| --- | --- | 
| offer\_id | The friendly identifier for the offer\.Can be used to join to the `offer_id` field of the `Offer_Product` data feed\. | 
| offer\_revision | The offer revision\. This field and the offer\_id field combine to form the primary key\.With `offer_id`, can be used to join to the `offer_id` and `offer_revision` fields of the `Target_Offer` data feed\. | 
| name | The seller\-defined name of the offer\.  | 
| expiration\_date | The date and time that the offer expires\. | 
| opportunity\_name | Any opportunity data linked to this offer\. If the offer is bound to an AWS opportunity, this field is populated\. | 
| opportunity\_description | Any descriptive information linked to this offer\. If the offer is bound to an AWS opportunity, this field is populated\. | 
| seller\_account\_id | The globally unique identifier \(GUID\) of the seller’s account\. Can be used to join with the account\_id field in the account data feed\. | 
| opportunity\_id | An identifier for the opportunity is only populated if a reseller is selling your product\. All offers created by different channel partners \(or sellers\) have the same opportunity\_id if the product is the same\.  | 

## Example of offer data feed<a name="data-feed-offer-sample-data"></a>

The following shows an example of the offer data feed\. For readability, the data history columns aren't shown\. For information about data history fields, see [Historization of the data](data-feed.md#data-feed-historization)\.


| offer\_id  | offer\_revision | name | expiration\_date | opportunity\_name | opportunity\_description | seller\_account\_id | opportunity\_id | 
| --- | --- | --- | --- | --- | --- | --- | --- | 
| offer\-dacpxznflfwin | 1 | Enterprise Contract Program Offer | 9999\-01\-01T00:00:00Z |  |  |  |  | 
| offer\-gszhmle5npzip | 1 | Private offer created by seller | 2020\-10\-31T00:00:00Z |  |  |  |  | 
| offer\-hmzhyle8nphlp | 1 | Enterprise Contract Program Offer | 9999\-01\-01T00:00:00Z |  |  |  |  | 