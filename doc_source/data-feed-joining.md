# Data feed tables overview<a name="data-feed-joining"></a>

The AWS Marketplace provided data feeds are a set of tables that you can join together to provide more context for your queries\.

There are three general domains, or categories of interest, in your data feeds:
+ **Catalog** – Includes information about the products and offers in your account\.
+ **Accounts** – Includes information about the accounts that provide or purchase products on AWS Marketplace \(your own accounts or accounts of parties that you work with such as channel partners or buyers\)\.
+ **Revenue** – Includes information about billing, disbursements, and taxes\.

The following diagram shows the tables in each domain, and how they are related to each other\. This diagram shows the Catalog, Accounts, and Revenue domains, including the tables within them\.

![\[Entity relationship diagram showing how data feeds relate to each other.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/datafeeds-overview.png) 

The following sections provide *entity relationship* \(ER\) diagrams for each domain\. Each ER diagram shows the tables and the fields within each table, as well as the fields that you can use to join the tables\.

**Note**  
The ER diagrams in this section do not include the common fields for all data feeds\. For more information about the common fields, see [Storage and structure of data feeds](data-feed.md#data-feed-details)\.

The following table describes the symbols that are used in the ER diagrams\.


| Symbol | Description | 
| --- | --- | 
|  ![\[An image of the letters "PK" as a symbol.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/datafeeds-primary-key.png)  |  **Primary key** – A primary key for the table\. When used with the `valid_from` and `update_date` fields, it is unique\. For more details about using these fields together, see [Historization of the data](data-feed.md#data-feed-historization)\. If more than one field is marked as primary key, then the fields together form the primary key\.  | 
|  ![\[An image of the letters "FK" as a symbol.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/datafeeds-foreign-key.png)  |   **Foreign key** – A field that represents a primary key in a different table\. Not necessarily unique in the table\.   In some cases, the foreign key can be blank if the record in the current table does not have a corresponding record in the foreign table\.   | 
|  ![\[An image of the letters "AK" as a symbol.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/datafeeds-alternate-key.png)  |   **Alternate key** – A key that can be used as a key in the table\. Follows the same uniqueness rules as the primary key\.  | 
|  ![\[An image of a line with a cross at one end and circle and fork at the other.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/datafeeds-one-to-many.png)  |   **Connector** – Lines between fields represent a connection, which is two fields that can be used to join tables\. The ends of the line represent the type of connection\. This example represents a one\-to\-many connection\.  | 

**Connector types**

The following table shows the types of ends that each connector can have\.


| Connector type | Description | 
| --- | --- | 
|  ![\[An image of a line with a cross at one end.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/datafeeds-one-to-n.png)  |   **One to n** – A connector with this end represents a join that has exactly one value on this side of the join\.  | 
|  ![\[An image of a line with a cross and circle at one end.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/datafeeds-zero-or-one-to-n.png)  |   **Zero or one to n** – A connector with this end represents a join that has zero or one values on this side of the join\.  | 
|  ![\[An image of a line with a circle and fork at one end.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/datafeeds-optional-many-to-n.png)  |   **Zero or more to n** – A connector with this end represents a join that has zero, one, or many values on this side of the join\.  | 
|  ![\[An image of a line with a cross and fork at one end.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/datafeeds-one-or-more-to-n.png)  |   **One or more to n** – A connector with this end represents a join that has one or many values on this side of the join\.  | 

## Catalog\-related tables<a name="data-feed-catalog-domain"></a>

The following diagram shows the relationships between tables in the Catalog domain, as well as the fields within the tables\. 

![\[Relationships between the Product, Offer_Product, Offer, Offer_Target, and Legacy_id_mapping tables in the Catalog domain.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/datafeeds-catalog-details.png)

The `Product`, `Offer_Product`, `Offer`, `Offer_Target`, and `Legacy_id_mapping`\_tables are in the Catalog domain\.

The `Offer_Target` table includes a value field for the `account_id` of the target, but only when the `target_type` value is `account`\.

The `Legacy_id_mapping` table is not used for current data\.

**Note**  
For more information about these tables, including a description of each field in the table and the joins that can be created, see the following topics:  
[Product data feed](data-feed-product.md)
[Offer product data feed](data-feed-offer-product.md)
[Offer data feed](data-feed-offer.md)
[Offer target data feed](data-feed-offer-target.md)
[Legacy mapping data feed](data-feed-legacy-mapping.md)

## Accounts\-related tables<a name="data-feed-accounts-domain"></a>

The following diagram shows the relationships between the `Account` and `Address` tables in the Accounts domain, as well as the fields within the tables\.

![\[Relationship between the Account and Address tables in the Accounts domain, and fields within each table.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/datafeeds-accounts-details.png)

**Note**  
For more information about these tables, including a description of each field in the table and the joins that can be created, see the following topics:  
[Account data feed](data-feed-account.md)
[Address data feed](data-feed-address.md)

## Revenue\-related tables<a name="data-feed-revenue-domain"></a>

The following diagram shows the relationships between the `Billing_Event` and `Tax_Item` tables in the Revenue domain, as well as the fields within the tables\. The `Billing_Event` table includes information about disbursements, as well as billing events\.

![\[Relationships between the Billing_Event and Tax_Item tables in the Revenue domain, and the fields within each table.\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/datafeeds-revenue-details.png)

**Note**  
For more information about these tables, including a description of each field in the table and the joins that can be created, see the following topics:  
[Billing event data feed](data-feed-billing-event.md)
[Tax item data feed](data-feed-tax-item.md)