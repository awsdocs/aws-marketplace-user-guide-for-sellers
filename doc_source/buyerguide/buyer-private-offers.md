# Private Offers<a name="buyer-private-offers"></a>

 AWS Marketplace Seller Private Offer enables you to receive non\-publicly available prices on publicly listed products\. Each private offer has pricing and licensing terms unique to your AWS account\. Private offers are extended directly by the seller with a set expiration date\. At the expiration date, you are automatically moved to the product public offer\. 

## Frequently Asked Questions<a name="buyer-private-offers-frequently-asked-questions"></a>

### I’m a software buyer\. How do I begin using AWS Marketplace Seller Private Offer?<a name="im-a-software-buyer.-how-do-i-begin-using-aws-marketplace-seller-private-offer"></a>

You can view private offers by visiting the products public fulfillment page\. If you have a private offer, you see a blue banner indicating that you have a private offer\. You can also reach a private offer directly from the private offer URL\. When you’re ready to purchase, you subscribe using the same process as other AWS Marketplace product\. 

### I’m a software buyer\. How does this work with linked accounts?<a name="im-a-software-buyer.-how-does-this-work-with-linked-accounts"></a>

 You can subscribe to a private offer using the master payor account or any associated linked account\. There can only be one private offer for a product to any account\. However, there can be multiple private offers to the same product as long as they are to different accounts\. For all linked accounts, you must subscribe through the AWS Marketplace website\. 

### Can I use AWS Marketplace Seller Private Offer from the EC2 console?<a name="can-i-use-aws-marketplace-seller-private-offer-from-the-ec2-console"></a>

 No, all private offers must start on the AWS Marketplace site to review specific terms\. After subscribing to an AMI\-based product, you can deploy the product from the EC2 console using the AMI ID\. After accepting a private offer, any products initially deployed through the EC2 console will receive the new price\. 

### I'm a software buyer\. What is the step\-by\-step process to subscribe to, and then launch the private offer? What interface needs to be used, the EC2 console or the AWS Marketplace portal?<a name="im-a-software-buyer.-what-is-the-step-by-step-process-to-subscribe-to-and-then-launch-the-private-offer-what-interface-needs-to-be-used-the-ec2-console-or-the-aws-marketplace-portal"></a>

 You can access a private offer using the link the seller provides\. The link takes you to the product fulfillment page\. From there, you must log in with credentials for the AWS account the offer was made to\. Private offers must be accessed from the AWS Marketplace page\. You can find your most recent private offer by navigating to the software vendor's public product detail page and choosing **Continue** to access the product fulfillment page\. After authenticating, you will see a blue banner indicating you have a private offer\. Follow the link in the banner to access the most recently created private offer for that product\. To accept the private offer, choose **Accept Offer**\. Until the expiration date noted in the pricing box, any running instances, annual software purchases, metering records, or contract purchases, will be charged at your private offer rates\. 

### When I purchase software using Private Offer, does it change how the software can be used?<a name="when-i-purchase-software-using-private-offer-does-it-change-how-the-software-can-be-used"></a>

 No\. The software you purchase behaves the same as it would if you purchased the software without a private offer\. 

### I’m a software buyer\. How do I check my usage of products purchased through AWS Marketplace Seller Private Offer?<a name="im-a-software-buyer.-how-do-i-check-my-usage-of-products-purchased-through-aws-marketplace-seller-private-offer"></a>

 Products with a private offer show up like any other AWS Marketplace product in your monthly bill\. You can use detailed billing to view your usage for each AWS Marketplace purchased products\. Each will have a line item corresponding to each kind of usage\. The product title will be appended with “\- private offer”\.

### Does subscribing to a private offer launch an instance?<a name="does-subscribing-to-a-private-offer-launch-an-instance"></a>

 No\. Subscribing to a private offer does not require launching a new instance of the software\. Accepting the private offer will modify the price to correspond to your private offer price\. If a product offers 1\-click launch, you can deploy a new instance of the software\. If a product defaults to 1\-click launch, you can accept a private offer without launching a new instance\. To launch without deploying a new instance, choose **Manual Launch** on the fulfillment page\. You can use the EC2 console to deploy additional instances, just like you would for other AWS Marketplace products\. 

### I'm a software buyer\. How do I know which account ID the software seller used to create the private offer?<a name="im-a-software-buyer.-how-do-i-know-which-account-id-master-payer-the-software-seller-used-to-create-the-private-offer"></a>

 When the software seller extends a private offer to you, you receive confirmation on the account included in a private offer\. Private offers are linked to the specific software buyer's account listed\. The software seller creates the private offer for the account you specify\. Each private offer can be made to up to 25 accounts\. All accounts associated with an offer are listed in the AWS Marketplace Management Portal, on the **Offers** view\. 

### After subscribing to a private offer, can all linked AWS accounts utilize the offer? Do I have any control to limit which linked accounts have access?<a name="after-subscribing-to-a-private-offer-can-all-linked-aws-accounts-utilize-the-offer-do-i-have-any-control-to-limit-which-linked-accounts-have-access"></a>

 When a private offer is accepted, each linked account will receive that price when using the product\. Any user with permission to use AWS Marketplace will see \(blue private offer ribbon\) and can use the private offer when they visit the products fulfillment page\. Whatever offer is accepted by the account is the price for that product\. 

### I am running an AMI and paying hourly and have just put a private offer for annual billing in place\. How do I convert the AMI to take advantage of the private offer?<a name="i-am-running-an-ami-and-paying-hourly-and-have-just-put-a-private-offer-for-annoual-billing-in-place.-how-do-i-convert-the-ami-to-take-advantage-of-the-private-offer"></a>

 Annual subscriptions function in a manner similar to a voucher system\. The subscription completely offsets the cost of running one instance hour of an hourly product per hour\. If you purchase an annual subscription through a private offer, the offer is used for running instances, whether the instance was launched when a public or private offer was in place\. 

### I am a software buyer\. How can I tell which existing instances are hourly and which are annual?<a name="i-am-a-software-buyer.-how-can-i-tell-which-existing-instances-are-hourly-and-which-are-annual"></a>

 You can review all of your annual subscriptions in In AWS Marketplace under **Your Software**\. If an annual subscription is purchased by one account in a linked account family, it is shared across the entire linked account family\. If the purchasing account does not have any running instances, the annual subscription is counted toward the usage in another linked account running that software\. For more information about annual subscriptions, see [AMI Subscriptions](buyer-ami-subscriptions.md)\. 