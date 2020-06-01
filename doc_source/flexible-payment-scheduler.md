# Flexible payment scheduler<a name="flexible-payment-scheduler"></a>

Flexible payment scheduler enables you to extend private offers with a custom payment schedule\. The schedule can be spread over up to three years, and the customer makes payments in regular installments\. After they are subscribed, your customers can see all the payments on the schedule and on their AWS invoice, helping them track their spending\. Flexible payment scheduler is available for private offers on AMI multi\-year and SaaS contracts products\.

Any customer on invoice terms, for example net\-30 or net\-60 terms, can subscribe to a private offer with a flexible payment schedule\. Customers who pay their AWS bill using a credit card can't\. If you try to create a private offer with a custom payment schedule for a customer who isn't on invoice terms, you receive an error\. 

## Creating a payment schedule<a name="creating-a-payment-schedule"></a>

The process for creating a custom payment schedule using flexible payment scheduler is part of the process for creating a private offer\. While creating the private offer, as you are adding product and buyer account information, choose **Allow Buyers to pay for this product in installments**\. This enables you to create an offer with a flexible payment schedule\. When you choose **Next** to continue, the flexible payment scheduler feature validates that any AWS account that you added is an account on invoice terms\. If you have provided an account that isn't on invoice terms, you receive an error message\. 

**Note**  
If the account is in an AWS Organizations billing family, the targeted account can be any account that is on net payment terms with AWS\. For more information, see [Consolidated Billing for AWS Organizations](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/consolidated-billing.html) in the *AWS Billing and Cost Management User Guide*\. 

After the AWS account or accounts are confirmed, customize your offer details on the next page\. Choose the contract duration for this offer and specify the offer details accordingly\.

**Note**  
 For private offers with flexible payment scheduler, for multi\-year and custom duration Amazon Machine Image \(AMI\) products, set the number of instances for each instance type included in the offer and the hourly pricing for any additional launched instances\. After the customer launches the specified number of instances, any additional instances launched are charged at the hourly rate specified in the private offer\. 

Under **Payment Schedule**, add the invoice dates and invoice amounts for all of the installments that the customer will make\. You can add up to 36 installments\. Each time you add an installment, **Total amount due from buyer** is updated\. 

**Note**  
The invoice date for the first installment is the first time that the customer is invoiced for your private offer\. You receive the payment for that first invoice after AWS Marketplace receives the payment from the customer\. 

The flexible payment scheduler feature validates that the invoice dates fall within the contract duration\. If your last invoice date is after the duration of the contract, you receive an error message\. 

After you have added all invoice dates and amounts, confirm that **Total amount due from buyer** matches the total price that you want your customer to pay over the course of the private offer\. To finish creating the private offer, upload the end user license agreement \(EULA\) for the customer and set the offer acceptance date\. 

**Note**  
Only one invoice date can occur before the offer acceptance date that you're extending to your customer\. 

Your customer is invoiced based on the schedule that you defined, and invoices start after they accept the offer\. If the first invoice date is scheduled before the offer is accepted, this invoice is processed immediately after the offer is accepted\. 

**Note**  
You can't modify the payment schedule on a private offer that has been extended to and subscribed by a buyer\. To make changes, you must create a new offer\. 

## Reporting for flexible payment scheduler<a name="fps-reporting"></a>

Reporting for private offers with flexible payment schedules is in the [Section 4: Contracts with flexible payment schedule](monthly-billed-revenue-report.md#section-4-contracts-with-flexible-payments), of the monthly billed revenue report\. 