# Machine learning product pricing<a name="machine-learning-pricing"></a>

You can choose from several available pricing models for your Amazon SageMaker products\. Buyers who subscribe to your product run it in SageMaker within their own AWS account\. The price for your buyers is a combination of the infrastructure costs for the resources running in their AWS account and the product pricing that you set\.

## Infrastructure pricing<a name="ml-infrastructure-pricing"></a>

Buyers are responsible for all the infrastructure costs of SageMaker while using your product\. These costs are set by AWS and are available on the [Amazon SageMaker pricing](https://aws.amazon.com/sagemaker/pricing/) page\.

## Software pricing<a name="ml-software-pricing"></a>

You determine the software prices that AWS Marketplace charges the buyer for using your product\. You set the pricing and terms when you are adding your machine learning product to AWS Marketplace\.

All infrastructure and software prices per instance type are presented to the buyer on the product listing pages in AWS Marketplace before the buyer subscribes\.

### Free pricing<a name="ml-pricing-free"></a>

You can choose to offer your product for free\. In this case, the buyer only pays for infrastructure costs\.

### Hourly pricing<a name="ml-pricing-hourly"></a>

You can offer your product with a price per hour per instance of your software running in SageMaker\. You can charge a different hourly price for each instance type that your software runs on\. While a buyer runs your software, AWS Marketplace tracks usage and then bills the buyer accordingly\. Usage is prorated to the minute\.

For *model package* products, buyer can run your software in two different ways\. They can host an endpoint continuously to perform real\-time inference or run a batch transform job on a dataset\. You can set different pricing for both of the ways a buyer can run your software\.

For *algorithm* products, in addition to determining the prices for performing inference, as mentioned earlier, you also determine an hourly price for training jobs\. You can charge a different hourly price for each instance type that your training image supports\.

### Inference pricing<a name="ml-pricing-inference"></a>

When the buyer runs your software by hosting an endpoint to continuously perform real\-time inference, you can choose to set a price per inference\.

**Note**  
Batch transform processes always use hourly pricing\. Training jobs for algorithm products also always use hourly pricing\. You can set these prices independently of the inference pricing, and of each other\.

By default, with inference pricing, AWS Marketplace charges your buyer for each invocation of your endpoint\. However, in some cases, your software processes a batch of inferences in a single invocation \(also known as a *mini\-batch*\)\. For an endpoint deployment, you can indicate a custom number of inferences that AWS Marketplace should charge the buyer for that single invocation\. To do this, include a custom metering header in the HTTP response headers of your invocation, as in the following example\.

```
X-Amzn-Inference-Metering: {"Dimension": "inference.count", "ConsumedUnits": 3}
```

This example shows an invocation that charges the buyer for three inferences\.

**Note**  
For inference pricing, AWS Marketplace only charges buyer for requests where the HTTP response code is `2XX`\.

### Free trial<a name="ml-pricing-free-trial"></a>

Optionally, you can create a free trial for your product and define the number of days of the free trial\. Free trials can be 5–120 days\. During the free trial, buyers can run your software as much as they want and aren't charged for your software\. Buyers are charged for the infrastructure costs during the free trial\. After the trial ends, they are charged your normal software price, along with the infrastructure costs\.

**Note**  
You can only create a free trial for offers that are charged hourly\. You can't create a free trial for a product with inference pricing\.

When buyers subscribe to a product with a free trial, they receive a welcome email message\. The message includes the term of the free trial, a calculated expiration date, and details on unsubscribing\. A reminder email message is sent three days before the expiration date\.

If you offer a free trial for your product in AWS Marketplace, you agree to the specific [ refund policy](https://docs.aws.amazon.com/marketplace/latest/userguide/refunds.html#refund-policy) for free trials\.

### Private offers<a name="ml-pricing-private"></a>

You can create private offers for your machine learning products\. A private offer gives specific buyers a different price than your publicly displayed price\.

Private offers work in one of two ways:
+ **Hourly** – Private offers can be an hourly rate that is different from the publicly displayed hourly rate\.
+ **Contract** – Private offers can be a contract with a fixed upfront fee for a specified number of days\. The buyer is allowed to use an unlimited number of instances for the entire duration of the contract\. At the end of the contract, any instances that continue to run are billed at the hourly rate that you set in the private offer\. For example, you can create a contract with a fixed upfront fee for 365 days of unlimited use\. You also set an hourly rate for the private offer\. When the buyer accepts this private offer, they pay that upfront fee\. When the contract ends, any instances still running are billed at that hourly rate\.

The set of terms and agreement between you and the buyer in private offers can differ from the one in the public offer or other private offers\.

You can create and extend multiple private offers to a single buyer\. Buyers that you extend the private offers to have the option to choose between the private offers and the public offer\. Buyers can only be subscribed to one offer at any given time\. They can't be subscribed to both a private offer and the public offer at the same time\.

To create a private offer for a specific buyer for SageMaker products, contact [ AWS Marketplace Seller Operations](https://aws.amazon.com/marketplace/management/contact-us/)\.

**Note**  
For more details about limitations of private offers, see [Notes about private offers](private-offers-overview.md#private-offer-limitations)\.