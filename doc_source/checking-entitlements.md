# Checking Entitlements<a name="checking-entitlements"></a>

 If your product is a SaaS contracts product, your product calls the AWS Marketplace Entitlement Service to retrieve the customer’s entitlement\. Your product should verify subsequent usage on that account against the AWS Marketplace Entitlement Service\. For example, if the customer provisions 10 users on the account, your product should check the AWS Marketplace Entitlement Service for entitlement to that capacity\. 

To verify a customer's entitlement to your product, use the `GetEntitlements` operation in the AWS Marketplace Entitlement Service\. The AWS Marketplace Entitlement Service is available only in the US East \(N\. Virginia\) Region, accessible through entitlement\.marketplace\.us\-east\-1\.amazonaws\.com\. 

 `GetEntitlements` accepts a customer identifier and dimension as filters\. `ProductCode` is a required parameter\. The operation returns a paginated list of entitlements\. The result has an `ExpirationDate` field that shows the minimum period of time that the entitlement is valid for\. If the customer has set up automatic renewal, the date in the ExpirationDate field is the renewal date\.

The following is an example of a `GetEntitlements` request\. 

```
{ 
"ProductCode": "72m8mmj6t2dgb8dfscnpsbfmn", 
"Filter": { 
"CUSTOMER_IDENTIFIER": "gY2P1GGigmq" 
} 
}
```

 The following is an example of the response from a `GetEntitlements` request\. 

 ![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/saas-getentitlements-response.png) 

## Retrieving Entitlement on User Actions<a name="retrieving-entitlement-on-user-actions"></a>

 The following examples can help you better understand the process for retrieving entitlement on user actions\. 

### Example: User\-based Product<a name="example-user-based-application"></a>

 You offer a product that allows a number of accounts to exist for a given customer\. The customer can visit a dashboard to provision new users \(for example, to assign credentials\)\. When your website displays this dashboard, your website calls `GetEntitlements` for the customer identifier to show the customer how much capacity is available\. When the customer provisions a new user, your product calls `GetEntitlements` to verify that the capacity exists\. If it does not, you can call the AWS Marketplace Metering Service to bill for additional users\. 

### Example: Data Storage Product<a name="example-data-storage-application"></a>

 You offer a product that enables customers to store a certain amount of data in encrypted or unencrypted form\. The customer can view a dashboard that displays the amount of data existing and allocated in your product\. Your dashboard retrieves the allocation amount through `GetEntitlements`\. 

## Frequently Asked Questions<a name="api-check-entitlements-frequently-asked-questions"></a>

### How Can I Audit My Existing Entitlements?<a name="how-can-i-audit-my-existing-entitlements"></a>

 You can create a job to periodically call `GetEntitlements` for all customer identifiers in your database\. AWS throttles your call volume to 10 TPS\. 

### Should I Revoke Access on the Expiration Date Indicated in the Entitlement Document If I Don’t Receive a Notification That the Entitlement Document Has Been Updated?<a name="should-i-revoke-access-on-the-expiration-date-indicated"></a>

 No\. Your product should wait for an entitlement update or periodically check `GetEntitlements` to verify that the allocation should be revoked\. Use the expiration field only to notify customers of a possible loss in allocated resources\. Don't use the information in this field to limit functionality\. Amazon SNS notifications are delivered with best effort, so your product should check `GetEntitlements` before revoking access\. 