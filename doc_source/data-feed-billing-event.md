# Billing event data feed<a name="data-feed-billing-event"></a>

This data feed provides information about billing events, including invoicing and disbursements\. 

For example, you can use this data feed to learn when and what a buyer is invoiced\. You can also use the [example SQL queries](#data-feeds-billing-event-query-examples) to analyze the data from this data feed\.

This data feed contains information associated with billing events for which you are the seller of record\. For agreements made via channel partners, this data feed contains information about billing events between the manufacturer and seller of record\.

The billing event data feed is refreshed every 24 hours, so new data is available daily\.

Billing event data is immutable\. 

The following table explains the names and descriptions of the data feed's columns\. 


| Column name  | Description  | 
| --- | --- | 
| billing\_event\_id | An identifier for a billing event\. This ID is unique in the seller's environment\.  | 
| from\_account\_id | The account that initiated the billing event\. If transction\_type is SELLER\_REV\_SHARE, it is the buyer's payer account\. This is a foreign key to the [account](data-feed-account.md) data feed\. | 
| to\_account\_id | The account that receives the transaction amount for the product\. This is a foreign key to the account data feed\. | 
| end\_user\_account\_id | The account that uses the product\. This account may be different from the buyer and payer accounts\. | 
| product\_id | The identifier of the product\. This is a foreign key to the [product](data-feed-product.md) data feed\. | 
| action | The type of action for this event\. Possible values are as follows: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/data-feed-billing-event.html) | 
| transaction\_type | The type of transaction\. For examples, see [Taxing scenarios](#data-feeds-billing-event-tax-examples)\. Possible values are as follows:  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/data-feed-billing-event.html)  | 
| parent\_billing\_event\_id | If the action is DISBURSEMENT or FORGIVEN and the transaction\_type is DISBURSEMENT, this is the billing\_event\_id that initiated this billing event\. If action has another value, this field is null\.  | 
| disbursement\_billing\_event\_id | The related disbursement when the `action` is `DISBURSED` AND one of the following is true:  [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/data-feed-billing-event.html) In all other cases, this value is null\. | 
| amount | The billing event amount\.  | 
| currency | The ISO 639 currency code\. | 
| balance\_impacting | Whether the amount is taken into account in calculating seller disbursements\. A value of 0 indicates the amount is shown for informational purposes and has no effect on the balance\. A value of 1 indicates that this amount takes into account in determining seller disbursements\.  | 
| invoice\_date | The date the invoice was created\. | 
| payment\_due\_date | When the action is INVOICED, the due date for the invoice\. | 
| usage\_period\_start\_date | The start date for the period in the record\. | 
| usage\_period\_end\_date | The end date for the period in the record\. | 
| invoice\_id | The AWS invoice ID\. | 
| billing\_address\_id | The payer's billing address reference in the address data feed\. | 
| transaction\_reference\_id | An identifier that allows you to cross\-reference data from the following reports: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/marketplace/latest/userguide/data-feed-billing-event.html)  | 

## Taxing scenarios<a name="data-feeds-billing-event-tax-examples"></a>

The taxation model that is in place for the country and state of the buyer and seller dictates how taxes are collected and remitted\. Following are the possible scenarios:
+ Taxes are collected and remitted by AWS\. In these cases, the `transaction_type` is `AWS_TAX_SHARE`\. 
+ Taxes are collected by AWS, disbursed to the seller, and remitted by the seller to the tax authorities\. In these cases, the `transaction_type` is `SELLER_TAX_SHARE`\.
+ Taxes are not collected by AWS\. The seller must calculate the taxes and remit them to the tax authorities\. In these cases, AWS Marketplace doesn't perform tax calculations or receive tax information\. The seller pays the taxes from the revenue share\.

## Examples of billing event data feed<a name="data-feed-billing-event-sample-scenario"></a>

This section shows examples of the billing event data period at the time of invoicing and one month later\. Note the following for all tables in this section: 
+ In data feeds, `billing_event_id` values are 40\-character alphanumeric strings\. They're shown here as two\-character strings for readability\. 
+ In the data feed, this information is presented in a single table\. For readability, the data is shown in multiple tables here, and all columns aren't shown\. 

For the examples in this section, assume the following: 
+ Arnav is the buyer\.
  + His account ID is `73739998888`\.
  + He's located in France, which is subject to marketplace facilitator laws\. For more information, see [Amazon Web Service Tax Help](https://aws.amazon.com/tax-help/)\.
  + He purchased `prod-o4grxfafcxxxx` and was invoiced $120\.60 for his monthly usage of that product\.
  + He paid the invoice within the month\.
+ Jane is the manufacturer\.
  + Her account ID is `111122223333`\.
+ Paulo is the seller of record\.
  + His account ID is `777788889999`\. 
  + He lives in Kansas, which is not subject to market facilitator laws\. 

### Billing event data feed for seller of record<a name="billing-event-example-seller-of-record"></a>

As the seller of record, Paulo invoices the buyer, Arnav\. 

The following tables show the relevant information in Paulo's data feed when he invoices Arnav\.


| billing\_event\_id  | from\_account\_id  | to\_account\_id  | end\_user\_account\_id | product\_id | action | transaction\_type | 
| --- | --- | --- | --- | --- | --- | --- | 
| I0 | 73739998888 | 777788889999 | 73739998888 | prod\-o4grxfafcxxxx | INVOICED | SELLER\_REV\_SHARE | 
| I1 | 73739998888 | AWS | 73739998888 | prod\-o4grxfafcxxxx | INVOICED | AWS\_TAX\_SHARE | 
| I2 | 777788889999 | 111122223333 | 73739998888 | prod\-o4grxfafcxxxx | INVOICED | SELLER\_REV\_SHARE | 
| I3 | 777788889999 | AWS | 73739998888 | prod\-o4grxfafcxxxx | INVOICED | AWS\_TAX\_SHARE | 


| parent\_billing\_event\_id | disbursement\_billing\_event\_id | amount | currency | invoice\_date | invoice\_id | 
| --- | --- | --- | --- | --- | --- | 
|  |  | 100 | USD | 2018\-12\-31T00:00:00Z | 781216640 | 
|  |  | 20\.6 | USD | 2018\-12\-31T00:00:00Z | 781216640 | 
|  |  | \-80 | USD | 2018\-12\-31T00:04:07Z | 788576665 | 
|  |  | \-0\.2 | USD | 2018\-12\-31T00:04:07Z | 788576665 | 

The following tables show the relevant information in Paulo's data feed at the end of the month, after Arnav pays the invoice\.


| billing\_event\_id  | from\_account\_id  | to\_account\_id  | end\_user\_account\_id | product\_id | action | transaction\_type | 
| --- | --- | --- | --- | --- | --- | --- | 
| I10 | 73739998888 | 777788889999 | 73739998888 |  | INVOICED | SELLER\_REV\_SHARE | 
| I12 | 777788889999 | 111122223333 | 73739998888 |  | INVOICED | SELLER\_REV\_SHARE | 
| I13 | 777788889999 | AWS | 73739998888 | prod\-o4grxfafcxxxx | INVOICED | AWS\_REV\_SHARE | 
| I14 | AWS | 777788889999 |  |  | DISBURSED | DISBURSEMENT | 


| parent\_billing\_event\_id | disbursement\_billing\_event\_id | amount | currency | invoice\_date | invoice\_id | 
| --- | --- | --- | --- | --- | --- | 
| I0 | I14 | \-100 | USD | 2018\-12\-31T00:00:00Z | 781216640 | 
| I2 | I14 | 80 | USD | 2018\-12\-31T00:04:07Z | 788576665 | 
| I3 | I14 | 0\.2 | USD | 2018\-12\-31T00:04:07Z | 788576665 | 
|  |  | 19\.8 | USD |  |  | 

### Billing event data feed for manufacturer<a name="billing-event-example-manufacturer"></a>

The following tables show the relevant information in the Jane's data feed when Paulo invoices Arnav\.


| billing\_event\_id  | from\_account\_id  | to\_account\_id  | end\_user\_account\_id | product\_id | action | transaction\_type | 
| --- | --- | --- | --- | --- | --- | --- | 
| I5 | 777788889999 | 111122223333 |  | prod\-o4grxfafcxxxx | INVOICED | SELLER\_REV\_SHARE | 
| I6 | 777788889999 | 111122223333 |  | prod\-o4grxfafcxxxx | INVOICED | SELLER\_TAX\_SHARE | 
| I7 | 777788889999 | AWS |  | prod\-o4grxfafcxxxx | INVOICED | AWS\_REV\_SHARE | 


| parent\_billing\_event\_id | disbursement\_billing\_event\_id | amount | currency | invoice\_date | invoice\_id | 
| --- | --- | --- | --- | --- | --- | 
|  |  | 73\.5 |  | 2018\-12\-31T00:04:07Z | 788576665 | 
|  |  | 6\.5 |  | 2018\-12\-31T00:04:07Z | 788576665 | 
|  |  | \-7\.35 |  | 2018\-12\-31T00:04:07Z | 788576665 | 

The following tables show the relevant information in Jane's data feed at the end of the month, after the invoice is paid\.


| billing\_event\_id  | from\_account\_id  | to\_account\_id  | end\_user\_account\_id | product\_id | action | transaction\_type | 
| --- | --- | --- | --- | --- | --- | --- | 
| I30 | 777788889999 | 111122223333 |  | prod\-o4grxfafcxxxx | DISBURSED | SELLER\_REV\_SHARE | 
| I31 | 777788889999 | 111122223333 |  | prod\-o4grxfafcxxxx | DISBURSED | SELLER\_TAX\_SHARE | 
| I32 | 777788889999 | AWS |  | prod\-o4grxfafcxxxx | DISBURSED | AWS\_REV\_SHARE | 
| I33 | AWS | 777788889999 |  |  | DISBURSED | DISBURSEMENT | 


| parent\_billing\_event\_id | disbursement\_billing\_event\_id | amount | currency | invoice\_date | invoice\_id | 
| --- | --- | --- | --- | --- | --- | 
| I5 | I33 | \-73\.5 | USD |  |  | 
| I6 | I33 | \-6\.5 | USD |  |  | 
| I7 | I33 | 7\.35 | USD |  |  | 
|  |  | 72\.65 | USD |  |  | 

## Example queries<a name="data-feeds-billing-event-query-examples"></a>

As described in [Using data feeds](data-feed.md#data-feed-using), you can use [ Athena](https://docs.aws.amazon.com/athena/latest/ug/what-is.html) to run queries on the data that's collected and stored as data feeds in your managed Amazon S3 bucket\. This section provides some examples of common ways you might do this\. All examples assume that a single currency is used\.

## Example 1: Amount invoiced, including taxes<a name="data-feed-example-query-tax-invoice"></a>

To find out how much buyers were invoiced, including taxes, you can run a query like the following: 

```
SELECT sum(amount) FROM billing_event 
WHERE 
  action = 'INVOICED'
  AND
  (
    (transaction_type in ('SELLER_REV_SHARE', 'SELLER_TAX_SHARE')
      -- to discard SELLER_REV_SHARE from Manufacturer to Channel Partner, aka cost of goods
      AND to_account_id='seller-account-id'
    )
  OR transaction_type= 'AWS_TAX_SHARE'
  );
```

## Example 2: Amount invoiced to buyers on seller's behalf<a name="data-feed-example-query-invoice-for-seller"></a>

To find out how much buyers were invoiced on a seller's behalf, you can run a query like the following:

```
SELECT sum(amount) FROM billing_event 
WHERE
  action = 'INVOICED'
  AND transaction_type in ('SELLER_REV_SHARE', 'SELLER_TAX_SHARE')
  AND to_account_id='seller-account-id'
;
```

## Example 3: Amount AWS can collect on seller's behalf<a name="data-feed-example-query-aws-collect"></a>

To find out how much AWS can collect on a seller's behalf, minus any refunds, credits, and forgiven accounts, you can run a query like the following:

```
SELECT sum(amount) FROM billing_event 
WHERE
  transaction_type like 'SELLER_%' -- what is invoiced on behalf of SELLER, incl. refunds/ credits and cost of goods
  and action in ('INVOICED','FORGIVEN') -- FORGIVEN action records will "negate" related INVOICED
;
```

## Example 4: Amount seller can collect<a name="data-feed-example-query-seller-collect"></a>

To find out how much sellers can collect, you can run a query like the following\. This example removes listing fees and taxes that AWS collects, and adds any exceptional balance adjustments\. 

```
SELECT sum(amount) FROM billing_event
WHERE
  (transaction_type like 'SELLER_%' -- what is invoiced on behalf of SELLER
  or transaction_type like 'AWS_REV_%' -- what is owed to AWS
  or transaction_type = 'BALANCE_ADJUSTMENT' -- exceptionnal case
  )
  and action in ('INVOICED','FORGIVEN')
;
```

You can also use the following query to collect the same information:

```
SELECT sum(amount) FROM billing_event
WHERE
  balance_impacting = 1
  and action in ('INVOICED','FORGIVEN')
;
```

The following example shows the same information, but is restricted to 2018 transactions and assumes all buyers paid their invoices: 

```
SELECT sum(amount) FROM billing_event
WHERE
  invoice_date between '2018-01-01' and '2018-12-31'
  and balance_impacting = 1
  and action in ('INVOICED','FORGIVEN')
;
```

## Example 5: Amount of disbursements<a name="data-feed-example-query-disbursements"></a>

To find out the amount that's been disbursed, you can run a query like the following:

```
select sum(amount) FROM billing_event
WHERE
  action ='DISBURSED'
  and transaction_type like 'DISBURSEMENT%'
;
```

## Example 6: Amount pending disbursement<a name="data-feed-example-query-pending-dibursement"></a>

To find out the amount that's pending disbursement, you can run a query like the following\. This query removes amounts that have already been disbursed\. 

```
SELECT sum(amount) FROM billing_event targeted 
WHERE
   (transaction_type like 'SELLER_%'  -- what is invoiced on behalf of SELLER
    or transaction_type like 'AWS_REV_%'  -- what is owed to AWS
    or transaction_type = 'BALANCE_ADJUSTMENT' -- exceptionnal case
   ) 
  -- DISBURSEMENT action records will "negate" 'INVOICED'
  -- but do not take into account failed disbursements
   AND 
    (not exists
      (select 1 
        from billing_event disbursement
          join billing_event failed_disbursement
           on disbursement.billing_event_id=failed_disbursement.parent_billing_event_id
        where
         disbursement.transaction_type='DISBURSEMENT'
         and failed_disbursement.transaction_type='DISBURSEMENT_FAILURE'
         and targeted.disbursement_billing_event_id=disbursement.billing_event_id
      )
    ) 
;
```

Another way to get the same information is to run a query like the following to get the seller's balance:

```
SELECT sum(amount) FROM billing_event
WHERE
 balance_impacting = 1
;
```

The following query extends our example\. It restricts the results to 2018 transactions and returns more details about the transactions\.

```
select sum(residual_amount_per_transaction)
from
 (SELECT
    max(billed_invoices.amount) invoiced_amount,
    sum(nvl(disbursed_invoices.amount,0)) disbursed_amount,
    -- Exercise left to the reader:
    -- use transaction_type to distinguish listing fee vs seller-owed money
    -- still pending collection
    max(transaction_type) transaction_type,
    max(billed_invoices.amount) 
      + sum(nvl(disbursed_invoices.amount,0)) residual_amount_per_transaction
  FROM billing_event billed_invoices
    -- find related disbursements
    left join billing_event disbursed_invoices
      on disbursed_invoices.action='DISBURSED'
      and disbursed_invoices.parent_billing_event_id=billed_invoices.billing_event_id
  WHERE
    billed_invoices.invoice_date between '2018-01-01' and '2018-12-31'
    and billed_invoices.transaction_type like 'SELLER_%' -- invoiced on behalf of SELLER
    and billed_invoices.action in ('INVOICED','FORGIVEN')
    -- do not take into account failed disbursements
    AND not exists
      (select 1 from billing_event failed_disbursement
       where disbursed_invoices.disbursement_billing_event_id =  failed_disbursement.parent_billing_event_id
      )
   GROUP BY billed_invoices.billing_event_id
);
```

## Example 7: Balance of set of invoices<a name="data-feed-example-query-balance-invoice-set"></a>

To learn the sum of a set of invoices, you can run a query like the following:

```
SELECT invoice_id, sum(amount) FROM billing_event targeted
WHERE
  --invoice_id is only not null for invoiced records AND disbursed records linking them to related disbursement -> no need to filter more precisely
  invoice_id in ('XXX','YYY') 
  -- filter out failed disbursements 
  AND not exists
      (select 1 
        from billing_event disbursement
          join billing_event failed_disbursement
           on disbursement.billing_event_id=failed_disbursement.parent_billing_event_id
        where
         disbursement.transaction_type='DISBURSEMENT'
         and failed_disbursement.transaction_type='DISBURSEMENT_FAILURE'
         and targeted.disbursement_billing_event_id=disbursement.billing_event_id
      ) 
  group by invoice_id;
```