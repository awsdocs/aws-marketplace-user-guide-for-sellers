# AWS Marketplace Product Support Connection account permissions<a name="set-aws-iam-psc-permissions"></a>

 The AWS Marketplace product support connection feature makes it possible for customers to provide contact information in the AWS Marketplace website so that you can offer them support for your products\. AWS Marketplace shares the data that the customer provides to you through an API\. Customers can choose to add contact details during or after they purchase a product that you enrolled in AWS Marketplace product support connection\. You use the API to retrieve the customer's contact data, along with relevant product subscription details\.

 If haven't enrolled in the [AWS Marketplace Commerce Analytics Service](commerce-analytics-service.md), you must configure your account and AWS services to use it\. Do the following: 

1.  \(Optional\) Create an [IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html)\. 

1.  Create a destination [Amazon Simple Storage Service \(Amazon S3\) bucket](https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingBucket.html#create-bucket-intro)\. 

1.  Create an [Amazon Simple Notification Service \(Amazon SNS\) topic](https://docs.aws.amazon.com/sns/latest/dg/sns-tutorial-create-topic.html) for response notifications\. 

1.  Enroll in the AWS Marketplace Commerce Analytics Service\. 

1.  \(Recommended\) Make a test call to the service using the [AWS Command Line Interface \(AWS CLI\)](https://aws.amazon.com/cli/)\. 

For instructions, see the [Onboarding guide](commerce-analytics-service.md#on-boarding-guide)\. 

**Note**  
The IAM permissions required for product support connection are different from those required for commerce analytics service\. Product support connection requires that the IAM user can call the `marketplacecommerceanalytics:StartSupportDataExport` action\.

You can allow an IAM user to call the `StartSupportDataExport` action by using an IAM permission policy\.

**Example**  

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "marketplacecommerceanalytics:StartSupportDataExport",
            "Resource": "*"
        }
    ]
}
```

For more information about this feature, see [Product Support Connection](product-support-connection.md)\.