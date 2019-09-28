# AWS Product Support Connection Account Permissions<a name="set-aws-iam-psc-permissions"></a>

 AWS Marketplace product support connection is a feature that allows AWS Marketplace customers to provide contact information in the AWS Marketplace website so you can provide them product support for your product\. AWS Marketplace shares the data the customer provides to you via an API\. Customers can choose to add contact details during or after the purchase of a product you have enrolled in AWS Marketplace product support connection\. You can retrieve the customer's contact data, along with relevant product subscription details, by calling a pull\-based API\. 

 If you're not already enrolled in the [AWS Marketplace Commerce Analytics Service](commerce-analytics-service.md), you must configure your account and AWS services to use it\. In particular, do the following: 

1.  \(Optional\) Create an [IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)\. 

1.  Create a destination [Amazon Simple Storage Service \(Amazon S3\) bucket](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucket.html#create-bucket-intro)\. 

1.  Create an [Amazon Simple Notification Service \(Amazon SNS\) topic](https://docs.aws.amazon.com/sns/latest/dg/sns-tutorial-create-topic.html) for response notifications\. 

1.  Enroll in the AWS Marketplace Commerce Analytics Service\. 

1.  \(Recommended\) Make a test call to the service using the [AWS Command Line Interface \(AWS CLI\)](https://aws.amazon.com/cli/)\. 

For detailed instructions, see [On\-boarding Guide](commerce-analytics-service.md#on-boarding-guide)\. 

**Note**  
The IAM permissions that are required for product support connection are different from those required for commerce analytics service\. Product support connection requires that the IAM user be able to invoke the `marketplacecommerceanalytics:StartSupportDataExport` action\.

 **Sample custom policy**: 

```
        {
      
        "Version": "2012-10-17",
        "Statement": [
        {
        "Effect": "Allow",
        "Action":
        "marketplacecommerceanalytics:StartSupportDataExport",
        "Resource": "*"
        }
        ]
        }
```