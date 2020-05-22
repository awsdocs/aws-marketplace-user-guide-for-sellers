# Integrating AWS Marketplace with procurement systems<a name="procurement-system-integration"></a>

You can configure the integration of AWS Marketplace and your Coupa or SAP Ariba \(beta\) procurement software\. After you complete the configuration, users in your organization can use your procurement software to search and request a subscription to AWS Marketplace products\. After the subscription request is approved, the transaction is completed, and the user is notified that the software subscription is available\. When the user signs in to AWS Marketplace, the software product is listed as a purchased subscription and is available for use\.

**Important**  
If you'd like to participate in our beta to integrate with SAP Ariba, contact us at awsmp\-eprocurement@amazon\.com and we'll help you configure a level 1 punchout\.

## How Coupa integration works<a name="procurement-system-integration-how-it-works"></a>

You can configure Coupa procurement software to integrate with AWS Marketplace following the commerce extensible markup language \(cXML\) protocol\. This integration creates an access point into a third party's catalog, or a *punchout*\. Open Buy is a feature of Coupa that allows users to search AWS Marketplace, directly from Coupa\. Coupa displays search results, and when the user chooses a result, they're redirected to AWS Marketplace\. After an administrator configures the punchout integration, users of Coupa's procurement software can discover the AWS Marketplace catalog in the **Shop Online** section of their home page\. They can also use the Coupa Open Buy feature and search the AWS Marketplace catalog directly from Coupa's search function\. 

 If the user wants to see more detail about a product, they choose the product and are automatically redirected to AWS Marketplace\. When the user wants to purchase a subscription, they complete the subscription request on AWS Marketplace\. On the product's subscription page, instead of a button that completes the purchase, the user has a button to request approval\. The request is sent back to a shopping cart in the Coupa system to complete the approval process\. The following image shows the process for an Open Buy subscription request\.

 ![\[Flow chart for Open Buy subscription request\]](http://docs.aws.amazon.com/marketplace/latest/buyerguide/images/coupa-flow-01.png) 

 When the Coupa procurement system receives the request from AWS Marketplace, the procurement system starts a workflow to complete the approval process\. After the request is approved, the procurement system's purchase order system automatically completes the transaction on AWS Marketplace and notifies the user that their subscription is ready to deploy\. AWS Marketplace sends an email to the AWS account used to access AWS Marketplace that the subscription succeeded and the software is available through AWS Marketplace\. The following image shows the approval process for an Open Buy subscription request\.

 ![\[Flowchart for Open Buy subscription approval\]](http://docs.aws.amazon.com/marketplace/latest/buyerguide/images/coupa-flow-02.png) 