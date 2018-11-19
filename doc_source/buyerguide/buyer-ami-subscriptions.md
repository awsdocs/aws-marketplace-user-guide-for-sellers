# AMI Subscriptions<a name="buyer-ami-subscriptions"></a>

 Select AMI\-based software products offer an annual subscription pricing model, in which you make a one\-time upfront payment and then pay no hourly usage fee for the next 12 months\. You can apply one annual subscription to an AWS Marketplace software product to one Amazon EC2 instance\. You can also continue to launch and run AWS Marketplace software products using hourly pricing\. Charges for using Amazon EC2 and other services from AWS are separate and in addition to what you pay to purchase AWS Marketplace software products\.

## Frequently Asked Questions<a name="buyer-ami-subscription-frequently-asked-questions"></a>

### Why should I buy an annual subscription?<a name="why-should-i-buy-an-annual-subscription"></a>

 Annual subscriptions offer the following benefits: 
+  *Cost Savings* – Reduce software costs up to 40% when you purchase an annual subscription of select software products on AWS Marketplace\. 
+  *Predictability* – Better forecast your software expenses\. 
+  *Flexibility* – Run software bought under the annual subscription model in any AWS Region or Availability Zone\. 
+  *Easy to Use* – Change the software pricing model without restarting or re\-launching your existing instances running on AWS\. 
+  *Familiarity* – As with hourly pricing, all annual subscription charges appear on your AWS bill\. There is no need to set up a new account or share payment information with a third party\. 

### How do I buy an annual subscription?<a name="how-do-i-buy-annual-subscription"></a>

1.  On the AWS Marketplace site, search or browse for the software product you want to subscribe to\. 

1.  On the **Product Details** page, note the annual subscription price and then choose **Continue**\. 

1.  Select an annual subscription option, and then choose **Accept Terms & Launch**\. 

1.  You will see a confirmation of the purchase you just made\. 

### I run product X and pay the hourly price\. This product now offers the annual subscription option\. How can I shift from paying the hourly price to an annual subscription?<a name="i-run-product-x-and-pay-the-hourly-price.-this-product-now-offers-the-annual-subscription-option.-how-can-i-shift-from-paying-the-hourly-price-to-an-annual-subscription"></a>

 You can convert your hourly pricing to subscription pricing simply by buying a new annual subscription or subscriptions\. AWS Marketplace will automatically convert your hourly pricing to the annual subscription\. You do not need to restart or change the instance\. 

**Tip**  
 Consider buying enough annual subscriptions to cover your steady\-state workload\. On the [Your Software](file:///C:\Users\andyruth\Desktop\$%7bmodel.helpUrls%5blibrary%5d%7d) page, you can find the list of your currently running software products and instances\. Products that offer annual subscription pricing have a **Buy Annual Subscription** button\. 

### Where can I see all my purchased annual subscriptions?<a name="where-can-i-see-all-my-purchased-annual-subscriptions"></a>

 You can review all of your annual subscriptions on the [Your Software](file:///C:\Users\andyruth\Desktop\$%7bmodel.helpUrls%5blibrary%5d%7d) page\. 

### When will I be billed for my annual subscriptions?<a name="when-will-i-be-billed-for-my-annual-subscriptions"></a>

 Your purchase of an annual subscription is billed immediate to your credit card, or an invoice is immediately generated\. 

### What happens when the annual subscription period is over?<a name="what-happens-when-the-annual-subscription-period-is-over"></a>

 When your annual subscription expires, you will start getting charged at the current hourly rate for that software product and instance type\. You can buy a new annual subscription to retain its benefits\. 

### Are the annual subscriptions specific to Availability Zones or Regions? For example, if I buy one annual subscription to product X, can I run one instance in the US West \(N\. California\) Region for six months and then run one instance in the US West \(Oregon\) Region for the remaining six months of the year?<a name="are-the-annual-subscriptions-specific-to-availability-zones-or-regions-for-example-if-i-buy-one-annual-subscription-to-product-x-can-i-run-one-instance-in-the-n.-california-region-for-six-months-and-then-run-one-instance-in-the-oregon-region-for-the-remaining-six-months-of-the-year"></a>

 AWS Marketplace annual software subscriptions are independent of Availability Zones and Regions\. You can run the software on an Amazon EC2 instance in any Region, as long as the software is offered in that region\. A particular product might not be available in all regions, and Amazon EC2 instance prices vary by Region\. 

### What happens if I accidentally buy an annual subscription?<a name="what-happens-if-i-accidentally-buy-an-annual-subscription"></a>

 Contact [AWS Support](file:///C:\Users\andyruth\Desktop\$%7bmodel.helpUrls%5bcontactUsRef%5d%7d)\. 

### I bought an annual subscription for product P, and EC2 instance type Y\. The product P has another supported instance type Z\. Can I change my instance type from Y to Z? How?<a name="i-bought-an-annual-subscription-for-product-p-and-ec2-instance-type-y.-the-product-p-has-another-supported-instance-type-z.-can-i-change-my-instance-type-from-y-to-z-how"></a>

 No, you cannot simply change the instance type\. Moving between instance types is considered to be an upgrade, if you pay more or the same for the new instance, or a downgrade, if you pay less for the new instance\. Downgrading is not supported\. You can upgrade any time by following these steps to cancel your existing subscription and buy a new subscription for the new instance type\.

**Note**  
Back up your data and check the product migration instructions before you take these steps\. In some cases you may need to do more\.

1.  Buy a new annual subscription for the new instance type you want\. Your new subscription is for one year from the date of purchase\. 

1.  Stop your existing instance, change the instance type by right\-clicking in the Amazon EC2 console, and start your instance again\. For more information, see [Changing the Instance Type](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-resize.html)\. 

1.  Request cancellation of your old annual subscription by contacting the seller\. You can find their email ID or phone number on the AWS Marketplace product detail page, or by contacting AWS Support\. 

 The upgrade process resets the end date of your annual subscription to 12 months from the date of the upgrade\. 

### I purchased an annual subscription for the 32\-bit version, instead of the 64\-bit version of a product, or the inappropriate version or higher or lower bandwidth product\. How can I change my subscription?<a name="i-purchased-an-annual-subscription-for-the-32-bit-version-instead-of-the-64-bit-version-of-a-product-or-the-inappropriate-version-or-higher-or-lower-bandwidth-product.-how-can-i-change-my-subscription"></a>

 Changing from one version of a product and another product is considered an upgrade or a downgrade, depending on whether you would pay more or get a refund\. Downgrading is not supported\. You can upgrade any time\. To upgrade, follow the process described in the answer to the previous question\. The upgrade process resets the end date of your annual subscription to 12 months the date of the upgrade\. 

### I have four annual subscriptions for product X\. Can I run eight instances for 12 hours and run nothing for next 24 hours, so that my usage in a 24\-hour period is effectively the same as running four instances for 24 hours?<a name="i-have-four-annual-subscriptions-for-product-x.-can-i-run-eight-instances-for-12-hours-and-run-nothing-for-next-24-hours-so-that-my-usage-in-a-24-hour-period-is-effectively-the-same-as-running-four-instances-for-24-hours"></a>

 No\. With four annual subscriptions, you can run only four instances at any point of time\. In this scenario, you would pay the current hourly price for the four additional instances in the first 12\-hour period, and the annual subscriptions would go unused in the remaining 12\-hour period\. 

### Will stopped instances be counted against annual subscriptions?<a name="will-stopped-instances-be-counted-against-annual-subscriptions"></a>

 No\. For example, if you purchased two annual subscriptions for product X, you can have only two running instances for X at any point of time, but you can have any number of stopped instances\. This is a useful strategy for disaster recovery and is an option that is unique to AWS Marketplace\. 

### Should I buy Reserved Instances along with annual software subscription to maximize savings?<a name="should-i-buy-reserved-instances-along-with-annual-software-subscription-to-maximize-savings"></a>

 Yes\. We strongly recommend that you buy Amazon EC2 Reserved Instances with your annual software subscription purchase\. For more information, see [Amazon EC2 Reserved Instances](http://aws.amazon.com/ec2/purchasing-options/reserved-instances/)\. 