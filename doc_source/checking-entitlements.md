# Checking entitlements<a name="checking-entitlements"></a>

 If your product is a SaaS contracts product, your product calls the AWS Marketplace Entitlement Service to retrieve the customer’s entitlement using the [GetEntitlements](https://docs.aws.amazon.com/marketplaceentitlement/latest/APIReference/API_GetEntitlements.html)\. Your product should verify subsequent usage on that account against the AWS Marketplace Entitlement Service\. For example, if the customer provisions 10 users on the account, your product should check the AWS Marketplace Entitlement Service for entitlement to that capacity\. 

To verify a customer's entitlement to your product, use the `GetEntitlements` operation in the AWS Marketplace Entitlement Service\. The AWS Marketplace Entitlement Service is available only in the US East \(N\. Virginia\) Region, accessible through `entitlement.marketplace.us-east-1.amazonaws.com`\. 

 `GetEntitlements` accepts a customer identifier and dimension as filters\. `ProductCode` is a required parameter\. The operation returns a paginated list of entitlements\. The result has an `ExpirationDate` field that shows the minimum period of time that the entitlement is valid for\. If the customer has set up automatic renewal, the date in the ExpirationDate field is the renewal date\.

For code samples, see [Code examples](saas-code-examples.md)\.

## Retrieving entitlement on user actions<a name="retrieving-entitlement-on-user-actions"></a>

 The following examples can help you better understand the process for retrieving entitlement on user actions\. 

### Example: User\-based product<a name="example-user-based-application"></a>

 You offer a product that allows a number of accounts to exist for a given customer\. The customer can visit a dashboard to provision new users \(for example, to assign credentials\)\. When the customer provisions a new user, your product calls `GetEntitlements` to verify that the capacity exists\. If it does not, you can call the AWS Marketplace Metering Service to bill for additional users\. 

### Example: Data storage product<a name="example-data-storage-application"></a>

 You offer a product that enables customers to store a certain amount of data in encrypted or unencrypted form\. The customer can view a dashboard that displays the amount of data existing and allocated in your product\. Your dashboard retrieves the allocation amount through `GetEntitlements`\. 