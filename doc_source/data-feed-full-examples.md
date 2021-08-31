# Data feed query examples<a name="data-feed-full-examples"></a>

This section gives examples of complex queries using the data feeds provided by AWS Marketplace\. These examples are similar to the [Seller reports](Reporting.md) that you get from the AWS Marketplace Management Portal\. You can customize these queries to create other reports that you need\.

## Example 1: Disbursements by product<a name="data-feed-example-disbursement-by-product"></a>

To find out the amount that's been disbursed by product, you can run a query like the following\. This example is comparable to the [Disbursement report](monthly-disbursement-report.md) that you can get as a seller report\. However, you can use this sample to build your own queries and customize it to get exactly the report that you need\.

This set of sample queries build upon each other to create the final list of product details with disbursements\. It also shows how to get the product information at a specific point in time\. The comments in the queries explain what the queries are doing, as well as how you can modify them to get different views of the data\.

**Note**  
When running this query, we are assuming that the data ingested is using two time axes \(the valid\_from column and the update column\)\. For more details, see [Storage and structure of data feeds](data-feed.md#data-feed-details)\.

```
    -- Get all the products and keep the latest product_id, valid_from tuple
    with products_with_uni_temporal_data as (
      select
       *
      from
      (
        select
         *,
         ROW_NUMBER() OVER (PARTITION BY product_id, valid_from 
             ORDER BY from_iso8601_timestamp(update_date) desc) 
             as row_num
        from
         productfeed_v1
      )
      where
        -- A product_id can appear multiple times with the same 
        -- valid_from date but with a different update_date column,
        -- making it effectively bi-temporal. By only taking the most
        -- recent tuple, we are converting to a uni-temporal model.
        row_num = 1
    ),

    -- Gets the latest revision of a product
    -- A product can have multiple revisions where some of the 
    -- columns, like the title, can change.
    -- For the purpose of the disbursement report, we want 
    -- to get the latest revision of a product
    products_with_latest_version as (
     select
      *
     from
     (
      select
       *,
       ROW_NUMBER() OVER (PARTITION BY product_id 
           ORDER BY from_iso8601_timestamp(valid_from) desc) 
           as row_num_latest_version
      from
       products_with_uni_temporal_data
     )
     where
      row_num_latest_version = 1
   ),

    -- Get all the accounts and keep the latest account_id, valid_from tuple
    accounts_with_uni_temporal_data as (
      select
       *
      from
      (
        select
         *,
         ROW_NUMBER() OVER (PARTITION BY account_id, valid_from ORDER BY from_iso8601_timestamp(update_date) desc) as row_num
        from
         accountfeed_v1
      )
      where
        -- An account_id can appear multiple times with the same 
        -- valid_from date but with a different update_date column,
        -- making it effectively bi-temporal. By only taking the most
        -- recent tuple, we are converting to a uni-temporal model.
        row_num = 1
    ),

    -- Gets the latest revision of an account
    -- An account can have multiple revisions where some of the 
    -- columns, like the mailing_address_id, can change.
    -- For the purpose of the disbursement report, we want 
    -- to get the latest revision of a product
    accounts_with_latest_version as (
     select
      *
     from
     (
      select
       *,
       ROW_NUMBER() OVER (PARTITION BY account_id 
           ORDER BY from_iso8601_timestamp(valid_from) desc) 
           as row_num_latest_version
      from
       accounts_with_uni_temporal_data
     )
     where
      row_num_latest_version = 1
   ),

    -- Get all the billing events and keep the 
    -- latest billing_event_id, valid_from tuple:
    billing_events_with_uni_temporal_data as (
      select
       *
      from (
        select
          billing_event_id,
          from_iso8601_timestamp(valid_from) as valid_from,
          from_iso8601_timestamp(update_date) as update_date,
          from_iso8601_timestamp(invoice_date) as invoice_date,
          transaction_type,
          transaction_reference_id,
          product_id,
          disbursement_billing_event_id,
          action,
          from_account_id,
          to_account_id,
          end_user_account_id,
          CAST(amount as decimal(20, 10)) invoice_amount,
          bank_trace_id,
          ROW_NUMBER() OVER (PARTITION BY billing_event_id, valid_from 
              ORDER BY from_iso8601_timestamp(update_date) desc) 
              as row_num
        from
          billingeventfeed_v1
        )
      where row_num = 1
    ),

    -- Get all the disbursements
    -- The billing events data is immutable.
    -- It is not required to use time windows based on the 
    -- valid_from column to get the most recent billing event
    disbursement_events as (
      select
        billing_events_raw.billing_event_id as disbursement_id,
        billing_events_raw.invoice_date as disbursement_date,
        billing_events_raw.bank_trace_id
      from
        billing_events_with_uni_temporal_data billing_events_raw
      where
        -- Only interested in disbursements, so filter out
        -- non-disbursements by selecting transaction type 
        -- to be DISBURSEMENT:
        billing_events_raw.transaction_type = 'DISBURSEMENT'
        -- Select a time period, you can adjust the dates 
        -- below if need be. For billing events use the 
        -- invoice date as the point in time of the 
        -- disbursement being initiated:
        and billing_events_raw.invoice_date >= 
            from_iso8601_timestamp('2020-10-01T00:00:00Z')
        and billing_events_raw.invoice_date < 
            from_iso8601_timestamp('2020-11-01T00:00:00Z')
    ),

    -- Get the invoices along with the line items that 
    -- are part of the above filtered disbursements
    disbursed_line_items as (
      select
        line_items.transaction_reference_id,
        line_items.product_id,
        line_items.transaction_type,
        (case
           -- Get the payer of the invoice from any 
           -- transaction type that is not AWS and 
           -- not BALANCE_ADJUSTMENT.
           -- For AWS and BALANCE_ADJUSTMENT, the billing 
           -- event feed will show the "AWS Marketplace" 
           -- account as the receiver of the funds and the 
           -- seller as the payer. Filter those out.
           when line_items.transaction_type 
               not like '%AWS%' and transaction_type 
               not like 'BALANCE_ADJUSTMENT' 
               then line_items.from_account_id
        end) as payer_account_id,
        line_items.end_user_account_id,
        invoice_amount,
        disbursements.disbursement_date,
        disbursements.disbursement_id,
        disbursements.bank_trace_id
      from
        billing_events_with_uni_temporal_data line_items
        -- Each disbursed line item is linked to the parent 
        -- disbursement via the disbursement_billing_event_id
        join disbursement_events disbursements 
          on disbursements.disbursement_id 
          = line_items.disbursement_billing_event_id
      where
        -- we are interested only in the invoice line 
        -- items that are DISBURSED
        line_items.action = 'DISBURSED'
    ),

  -- An invoice can contain multiple line items
  -- Create a pivot table to calculate the different 
  -- amounts that are part of an invoice.
  -- The new row is aggregated at 
  -- transaction_reference_id - end_user_account_id level
  invoice_amounts_aggregated as (
    select
      transaction_reference_id,
      product_id,
      -- a given disbursement id should have the 
      -- same disbursement_date
      max(disbursement_date) as disbursement_date,
      -- Build a pivot table in order to provide all the
      -- data related to a transaction in a single row.
      -- Note that the amounts are negated. This is because 
      -- when an invoice is generated, we give you the 
      -- positive amounts and the disbursement event 
      -- negates the amounts
      sum(case when transaction_type = 'SELLER_REV_SHARE' 
          then -invoice_amount else 0 end) as seller_rev_share,
      sum(case when transaction_type = 'AWS_REV_SHARE'  
          then -invoice_amount else 0 end) as aws_rev_share,
      sum(case when transaction_type = 'SELLER_REV_SHARE_REFUND'  
          then -invoice_amount else 0 end) as seller_rev_refund,
      sum(case when transaction_type = 'AWS_REV_SHARE_REFUND'  
          then -invoice_amount else 0 end) as aws_rev_refund,
      sum(case when transaction_type = 'SELLER_REV_SHARE_CREDIT'  
          then -invoice_amount else 0 end) as seller_rev_credit,
      sum(case when transaction_type = 'AWS_REV_SHARE_CREDIT'  
          then -invoice_amount else 0 end) as aws_rev_credit,
      sum(case when transaction_type = 'SELLER_TAX_SHARE'  
          then -invoice_amount else 0 end) as seller_tax_share,
      sum(case when transaction_type = 'SELLER_TAX_SHARE_REFUND'  
          then -invoice_amount else 0 end) as seller_tax_refund,
      -- This is the account that pays the invoice:
      max(payer_account_id) as payer_account_id,
      -- This is the account that subscribed to the product:
      end_user_account_id as customer_account_id,
      bank_trace_id
    from
      disbursed_line_items
    group by
      transaction_reference_id,
      product_id,
      disbursement_id,
      -- There might be a different end-user for the same 
      -- transaction reference id. Distributed licenses 
      -- is an example
      end_user_account_id,
      bank_trace_id
),

disbursed_amount_by_product as (
  select
    products.title as ProductTitle,
    products.product_code as ProductCode,
    -- We are rounding the sums using 2 decimal precision
    -- Note that the rounding method might differ 
    -- between SQL implementations.
    -- The disbursement seller report is using 
    -- RoundingMode.HALF_UP. This might create 
    -- discrepancies between this SQL output
    -- and the disbursement seller report
    round(invoice_amounts.seller_rev_share, 2) as SellerRev,
    round(invoice_amounts.aws_rev_share, 2) as AWSRefFee,
    round(invoice_amounts.seller_rev_refund, 2) as SellerRevRefund,
    round(invoice_amounts.aws_rev_refund, 2) as AWSRefFeeRefund,
    round(invoice_amounts.seller_rev_credit, 2) as SellerRevCredit,
    round(invoice_amounts.aws_rev_credit, 2) as AWSRefFeeCredit,
    (
        round(invoice_amounts.seller_rev_share, 2) +
        round(invoice_amounts.aws_rev_share, 2) +
        round(invoice_amounts.seller_rev_refund, 2) +
        round(invoice_amounts.aws_rev_refund, 2) +
        round(invoice_amounts.seller_rev_credit, 2) +
        round(invoice_amounts.aws_rev_credit, 2)
    ) as NetAmount,
    invoice_amounts.transaction_reference_id  
          as TransactionReferenceID,
    round(invoice_amounts.seller_tax_share, 2)  
          as SellerSalesTax,
    round(invoice_amounts.seller_tax_refund, 2)  
          as SellerSalesTaxRefund,
    payer_info.aws_account_id  
          as PayerAwsAccountId,
    customer_info.aws_account_id  
          as EndCustomerAwsAccountId,
    invoice_amounts.disbursement_date  
          as DisbursementDate,
    invoice_amounts.bank_trace_id  
          as BankTraceId
  from
    invoice_amounts_aggregated invoice_amounts
    join products_with_latest_version products  
      on products.product_id = invoice_amounts.product_id
    left join accounts_with_latest_version payer_info  
      on payer_info.account_id = invoice_amounts.payer_account_id
    left join accounts_with_latest_version customer_info  
      on customer_info.account_id = invoice_amounts.customer_account_id
)

select * from disbursed_amount_by_product;
```

## Example 2: Sales compensation report<a name="data-feed-example-sales-compensation"></a>

To find the billed revenue by customer, you can run a query like the following\. This example is comparable to the [Sales compensation report](sales-compensation-report.md) that you can get as a seller report\. However, you can use this sample to build your own queries and customize it to get exactly the report that you need\.

This is a set of sample queries that build upon each other to create the final list of customer details with the total amount billed to each customer for usage of your software\. The comments in the queries explain what the queries are doing, as well as how you can modify them to get different views of the data\.

**Note**  
When running this query, we are assuming that the data ingested is using two time axes \(the valid\_from column and the update column\)\. For more details, see [Storage and structure of data feeds](data-feed.md#data-feed-details)\.

```
    -- Gets all the products and keeps the latest product_id, 
    -- valid_from tuple.
    with products_with_uni_temporal_data as (
      select
       *
      from
      (
        select
         *,
         ROW_NUMBER() OVER (PARTITION BY product_id, valid_from 
                  ORDER BY from_iso8601_timestamp(update_date) desc) 
                  as row_num
        from
         productfeed_v1
      )
      where
        -- A product_id can appear multiple times with the same 
        -- valid_from date but with a different update_date column,
        -- making it effectively bi-temporal. By only taking the most
        -- recent tuple, we are converting to a uni-temporal model.
        row_num = 1
    ),

    -- Gets the latest revision of a product
    -- A product can have multiple revisions where some of the 
    -- columns, like the title, can change.
    -- For the purpose of the sales compensation report, we want 
    -- to get the latest revision of a product
    products_with_latest_revision as (
     select
      *
     from
     (
      select
       *,
       ROW_NUMBER() OVER (PARTITION BY product_id ORDER BY from_iso8601_timestamp(valid_from) desc) as row_num_latest_revision
      from
       products_with_uni_temporal_data
     )
     where
      row_num_latest_revision = 1
   ),

     -- Gets all the addresses and keeps the latest address_id, 
     -- aws_account_id, and valid_from combination.
     -- We're transitioning from a bi-temporal data model to an 
     -- uni-temporal data_model
     piifeed_with_uni_temporal_data as (
       select
        *
       from
       (
         select
          *,
          ROW_NUMBER() OVER (
             PARTITION BY address_id, aws_account_id, valid_from 
             ORDER BY from_iso8601_timestamp(update_date) desc) 
             as row_num
         from
          piifeed
       )
       where
         -- An address_id can appear multiple times with the same
         -- valid_from date but with a different update_date column.
         -- We are only interested in the most recent.
         row_num = 1
     ),

    -- Gets the latest revision of an address.
    -- An address_id can have multiple revisions where some of 
    -- the columns can change.
    -- For the purpose of the sales compensation report, we want to
    -- get the latest revision of an address + account_id pair.
    pii_with_latest_revision as (
      select
       *
      from
      (
       select
        *,
        ROW_NUMBER() OVER (PARTITION BY address_id, aws_account_id 
              ORDER BY from_iso8601_timestamp(valid_from) desc) 
              as row_num_latest_revision
       from
        piifeed_with_uni_temporal_data
      )
      where
       row_num_latest_revision = 1
    ),

    -- Gets all the accounts and keeps the latest 
    -- account_id, valid_from tuple.
    -- We're transitioning from a bi-temporal data 
    -- model to an uni-temporal data_model.
    accounts_with_uni_temporal_data as (
      select
       *
      from
      (
        select
         *,
         ROW_NUMBER() OVER (PARTITION BY account_id, valid_from 
             ORDER BY from_iso8601_timestamp(update_date) desc) 
             as row_num
        from
         accountfeed_v1
      )
      where
        -- An account_id can appear multiple times with the same 
        -- valid_from date but with a different update_date column.
        -- We are only interested in the most recent tuple.
        row_num = 1
    ),

    -- Gets all the historical dates for an account
    -- An account can have multiple revisions where some of the 
    -- columns like the mailing_address_id can change.
    accounts_with_history as (
     select
      *,
      -- This interval's begin_date
      case
        when
        -- First record for a given account_id
          lag(valid_from, 1) over (partition by account_id 
             order by from_iso8601_timestamp(valid_from) asc) is null
        then
          -- 'force' begin_date a bit earlier because of different 
          -- data propagation times. We'll subtract one day as one
          -- hour is not sufficient
          from_iso8601_timestamp(valid_from) - INTERVAL '1' DAY
        else
          -- not the first line -> return the real date
          from_iso8601_timestamp(valid_from)
      end as begin_date,
      -- This interval's end date.
      COALESCE(
           LEAD(from_iso8601_timestamp(valid_from), 1) 
                OVER (partition by account_id 
                ORDER BY from_iso8601_timestamp(valid_from)),
           from_iso8601_timestamp('9999-01-01T00:00:00Z')
      ) as end_date
     from
       accounts_with_uni_temporal_data
   ),

    -- Gets all the billing events and keeps the latest 
    -- billing_event_id, valid_from tuple.
    -- We're transitioning from a bi-temporal data 
    -- model to an uni-temporal data_model.
    billing_events_with_uni_temporal_data as (
      select
       *
      from (
        select
          billing_event_id,
          from_iso8601_timestamp(valid_from) as valid_from,
          from_iso8601_timestamp(update_date) as update_date,
          from_iso8601_timestamp(invoice_date) as invoice_date,
          transaction_type,
          transaction_reference_id,
          product_id,
          disbursement_billing_event_id,
          action,
          currency,
          from_account_id,
          to_account_id,
          end_user_account_id,
          -- convert an empty billing address to null. This will 
          -- later be used in a COALESCE call
          case
           when billing_address_id <> '' then billing_address_id else null
          end as billing_address_id,
          CAST(amount as decimal(20, 10)) invoice_amount,
          ROW_NUMBER() OVER (PARTITION BY billing_event_id, valid_from 
              ORDER BY from_iso8601_timestamp(update_date) desc) 
              as row_num
        from
          billingeventfeed_v1
        where
          -- The Sales Compensation Report does not contain BALANCE 
          -- ADJUSTMENTS, so we filter them out here
          transaction_type <> 'BALANCE_ADJUSTMENT'
          -- Keep only the transactions that will affect any 
          -- future disbursed amounts.
          and balance_impacting = '1'
        )
      where row_num = 1
    ),

    -- Gets the billing address for all DISBURSED invoices. This 
    -- will be the address of the payer when the invoice was paid.
    -- NOTE: For legal reasons, for CPPO transactions, the 
    -- manufacturer will not see the payer's billing address id
    billing_addresses_for_disbursed_invoices as (
      select
        billing_events_raw.transaction_reference_id,
        billing_events_raw.billing_address_id,
        billing_events_raw.from_account_id
      from
        billing_events_with_uni_temporal_data billing_events_raw
      where
        -- the disbursed items will contain the billing address id
        billing_events_raw.action = 'DISBURSED'
        -- we only want to get the billing address id for the 
        -- transaction line items where the seller is the receiver
        -- of the amount
        and billing_events_raw.transaction_type like 'SELLER_%'
      group by
        billing_events_raw.transaction_reference_id,
        billing_events_raw.billing_address_id,
        billing_events_raw.from_account_id
    ),

  -- An invoice can contain multiple line items.
  -- We create a pivot table to calculate the different amounts 
  -- that are part of an invoice.
  -- The new row is aggregated at 
  -- transaction_reference_id - end_user_account_id level
  invoiced_and_forgiven_transactions as (
    select
      transaction_reference_id,
      product_id,
      -- A transaction will have the same invoice date for all 
      -- of its line items (transaction types)
      max(invoice_date) as invoice_date,
      -- A transaction will have the same billing_address_id 
      -- for all of its line items. Remember that the billing event
      -- is uni temporal and we retrieved only the latest valid_from item
      max(billing_address_id) as billing_address_id,
      --  A transaction will have the same currency for all 
      -- of its line items
      max(currency) as currency,
      -- We're building a pivot table in order to provide all the 
      -- data related to a transaction in a single row
      sum(case when transaction_type = 'SELLER_REV_SHARE' 
            then invoice_amount else 0 end) as seller_rev_share,
      sum(case when transaction_type = 'AWS_REV_SHARE' 
            then invoice_amount else 0 end) as aws_rev_share,
      sum(case when transaction_type = 'SELLER_REV_SHARE_REFUND' 
            then invoice_amount else 0 end) as seller_rev_refund,
      sum(case when transaction_type = 'AWS_REV_SHARE_REFUND' 
            then invoice_amount else 0 end) as aws_rev_refund,
      sum(case when transaction_type = 'SELLER_REV_SHARE_CREDIT' 
            then invoice_amount else 0 end) as seller_rev_credit,
      sum(case when transaction_type = 'AWS_REV_SHARE_CREDIT' 
            then invoice_amount else 0 end) as aws_rev_credit,
      sum(case when transaction_type = 'SELLER_TAX_SHARE' 
            then invoice_amount else 0 end) as seller_tax_share,
      sum(case when transaction_type = 'SELLER_TAX_SHARE_REFUND' 
            then invoice_amount else 0 end) as seller_tax_refund,
      -- this is the account that pays the invoice.
      max(case
        -- Get the payer of the invoice from any transaction type 
        -- that is not AWS and not BALANCE_ADJUSTMENT.
        -- For AWS and BALANCE_ADJUSTMENT, the billing event feed 
        -- will show the "AWS Marketplace" account as the
        -- receiver of the funds and the seller as the payer. We 
        -- are not interested in this information here.
        when
         transaction_type not like '%AWS%' 
           and transaction_type not like 'BALANCE_ADJUSTMENT' 
         then from_account_id
       end) as payer_account_id,
      -- this is the account that subscribed to your product
      end_user_account_id as customer_account_id
    from
      billing_events_with_uni_temporal_data
    where
      -- Get invoiced or forgiven items. Disbursements are 
      -- not part of the sales compensation report
      action in ('INVOICED', 'FORGIVEN')
    group by
      transaction_reference_id,
      product_id,
      -- There might be a different end-user for the same 
      -- transaction reference id. Distributed licenses 
      -- is an example.
      end_user_account_id
),

invoiced_items_with_product_and_billing_address as (
  select
    invoice_amounts.*,
    products.product_code,
    products.title,
    payer_info.aws_account_id as payer_aws_account_id,
    payer_info.account_id as payer_reference_id,
    customer_info.aws_account_id as end_user_aws_account_id,
    (
        invoice_amounts.seller_rev_share +
        invoice_amounts.aws_rev_share +
        invoice_amounts.seller_rev_refund +
        invoice_amounts.aws_rev_refund +
        invoice_amounts.seller_rev_credit +
        invoice_amounts.aws_rev_credit +
        invoice_amounts.seller_tax_share +
        invoice_amounts.seller_tax_refund
    ) as seller_net_revenue,
    -- Try to get the billing address from the DISBURSED event 
    -- (if any). If there is no DISBURSEMENT, get the billing 
    -- address from the INVOICED item. If still no billing address, 
    -- then default to getting the mailing address of the payer.
    coalesce(billing_add.billing_address_id, 
             invoice_amounts.billing_address_id, 
             payer_info.mailing_address_id) 
          as final_billing_address_id
  from
    invoiced_and_forgiven_transactions invoice_amounts
    join products_with_latest_revision products 
        on products.product_id = invoice_amounts.product_id
    left join accounts_with_history payer_info 
        on payer_info.account_id = invoice_amounts.payer_account_id
          -- Get the Payer Information at the time of invoice creation
          and payer_info.begin_date <= invoice_amounts.invoice_date 
          and invoice_amounts.invoice_date < payer_info.end_date
    left join accounts_with_history customer_info 
        on customer_info.account_id = invoice_amounts.customer_account_id
          -- Get the End User Information at the time of invoice creation
          and customer_info.begin_date <= invoice_amounts.invoice_date 
          and invoice_amounts.invoice_date < customer_info.end_date
    left join billing_addresses_for_disbursed_invoices billing_add 
        on billing_add.transaction_reference_id = 
           invoice_amounts.transaction_reference_id
        and billing_add.from_account_id = 
            invoice_amounts.payer_account_id
),

invoices_with_full_address as (
  select
    payer_aws_account_id as "Customer AWS Account Number",
    pii_data.country as "Country",
    pii_data.state_or_region as "State",
    pii_data.city as "City",
    pii_data.postal_code as "Zip Code",
    pii_data.email_domain as "Email Domain",
    product_code as "Product Code",
    title as "Product Title",
    seller_rev_share as "Gross Revenue",
    aws_rev_share as "AWS Revenue Share",
    seller_rev_refund as "Gross Refunds",
    aws_rev_refund as "AWS Refunds Share",
    seller_net_revenue as "Net Revenue",
    currency as "Currency",
    date_format(invoice_date, '%Y-%m')as "AR Period",
    transaction_reference_id as "Transaction Reference ID",
    payer_reference_id as "Payer Reference ID",
    end_user_aws_account_id as "End Customer AWS Account ID"
  from
    invoiced_items_with_product_and_billing_address invoice_amounts
    left join pii_with_latest_revision pii_data 
        on pii_data.aws_account_id = invoice_amounts.payer_aws_account_id
        and pii_data.address_id = invoice_amounts.final_billing_address_id
    -- Filter out FORGIVEN and Field Demonstration Pricing transactions
    where seller_net_revenue <> 0
)

select * from invoices_with_full_address;
```