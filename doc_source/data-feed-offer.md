# Offer data feed<a name="data-feed-offer"></a>

This data feed provides information about all offers you've created as the seller of record\. If a single offer has multiple revisions, all revisions are included in the data feed\.

When you make an offer revision and the data in an exposed field changes, a new record is created in the data feed for the same primary key \(`offer_id` plus `offer_revision`\), but with a different value for `valid_from` field\. For more information about the data feed history columns, see [Historization of the data](data-feed.md#data-feed-historization)\.

The offer data feed is refreshed every 24 hours, so new data is available daily\.

The following table explains the names and descriptions of the data feed's columns\. 


| Column name  | Description  | 
| --- | --- | 
| offer\_id | The friendly identifier for the offer\. | 
| offer\_revision | The offer revision\. This field and the offer\_id field combine to form the primary key\. | 
| name | The seller\-defined name of the offer\.  | 
| expiration\_date | The date and time that the offer expires\. | 
| opportunity\_name | Any opportunity data linked to this offer\. If the offer is bound to an AWS opportunity, this field is populated\. | 
| opportunity\_description | Any descriptive information linked to this offer\. If the offer is bound to an AWS opportunity, this field is populated\. | 

## Example of offer data feed<a name="data-feed-offer-sample-data"></a>

The following shows an example of the offer data feed\. For readability, the data history columns aren't shown\. For information about data history fields, see [Historization of the data](data-feed.md#data-feed-historization)\.


| offer\_id  | offer\_revision | name | expiration\_date | opportunity\_name | opportunity\_description | 
| --- | --- | --- | --- | --- | --- | 
| offer\-dacpxznflfwin | 1 | Enterprise Contract Program Offer | 9999\-01\-01T00:00:00Z |  |  | 
| offer\-gszhmle5npzip | 1 | Private offer created by seller | 2020\-10\-31T00:00:00Z |  |  | 
| offer\-hmzhyle8nphlp | 1 | Enterprise Contract Program Offer | 9999\-01\-01T00:00:00Z |  |  | 