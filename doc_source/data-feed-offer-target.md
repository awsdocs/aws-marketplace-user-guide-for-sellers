# Offer target data feed<a name="data-feed-offer-target"></a>

This data feed lists targets of an offer's revision for all offers you've created as the seller of record\. If a single offer has multiple revisions, all revisions are included in the data feed\.

When you make an offer revision and the data in an exposed field changes, a new record is created in the data feed for the same primary key \(`offer_id` plus `offer_revision`\), but with a different value for `valid_from` field\. 

The offer target data feed is refreshed every 24 hours, so new data is available daily\.

The following table explains the names and descriptions of the data feed's columns\.


| Column name  | Description  | 
| --- | --- | 
| offer\_target\_id | The primary key of the feed\. | 
| offer\_id\+offer\_revision | The identifier and revision of the offer\. These two columns reference the offer that this target relates to\. | 
| target\_type | Indicates whether the offer recipient is BuyerAccounts, which indicates a private offer, or ParticipatingPrograms\. | 
| polarity | Indicates whether the offer is intended to be made to the `target_type`\. Acceptable values are as follows: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/data-feed-offer-target.html)  | 
| value | A string that represents the target: either an AWS account ID or a program that can be used with an offer\. For example, [Standard Contract for AWS Marketplace \(SCMP\)](standardized-license-terms.md#standard-contracts), [Enterprise Contract for AWS Marketplace \(ECMP\)](standardized-license-terms.md#enterprise-contracts), or [AWS Marketplace Field Demonstration Program \(FDP\)](field-demonstration-program.md)\. | 

## Example of offer target data feed<a name="data-feed-offer-target-sample-data"></a>

The following shows an example of the offer target data feed\. For readability, the data history columns aren't shown\. For information about data history fields, see [Historization of the data](data-feed.md#data-feed-historization)\. 


| offer\_target\_id  | offer\_id  | offer\_revision | target\_type | polarity | value | 
| --- | --- | --- | --- | --- | --- | 
| 925ddc73f6a373b7d5544ea3210610803b600 | offer\-dacpxznflfwin | 1 | ParticipatingPrograms | PositiveTargeting | EnterpriseContract | 
| 471ff22ae3165278f1fb960d3e14517bcd601 | offer\-gszhmle5npzip | 1 | ParticipatingPrograms | PositiveTargeting | FieldDemonstration | 
| 511ff22adfj65278f1fb960d3e14517bcd6e602 | offer\-gszhmle5npzip | 1 | ParticipatingPrograms  | PositiveTargeting | EnterpriseContract | 