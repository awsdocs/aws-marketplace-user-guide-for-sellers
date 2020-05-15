# AWS Marketplace metering and entitlement API permissions<a name="iam-user-policy-for-aws-marketplace-actions"></a>

Software as a service \(SaaS\) products, AMI products, and container products can use the AWS Marketplace Metering and Entitlement Service API\. Each type requires different IAM permissions\. For your product or products, you meter for all usage, and customers are billed by AWS based on the metering records that you provide\. To enable the integration required to provide AWS Marketplace your metering records, the service account that the integration is running under needs a constrained IAM policy to enable access\. Attach the policy for the product type you are sending metering information for to the IAM user or role that you're using for the integration\. 

## IAM policy for SaaS products<a name="iam-user-policy-for-saas-products"></a>

```
{
    "Version": "2012-10-17",
    "Statement": [
         {
         "Action": [
                 "aws-marketplace:ResolveCustomer",
                 "aws-marketplace:BatchMeterUsage",
                 "aws-marketplace:GetEntitlements"
         ],
         "Effect": "Allow",
         "Resource": "*"
         }
    ]
}
```

**Note**  
 The ﬁrst permission is required for all SaaS integrations\. The second and third permissions are needed for the AWS Marketplace metering service API and the AWS Marketplace entitlement service API, respectively\. 

## IAM policy for AMI products<a name="iam-user-policy-for-ami-products"></a>

```
{
    "Version": "2012-10-17",
    "Statement": [
         {
         "Action": [
                 aws-marketplace:MeterUsage
         ],
         "Effect": "Allow",
         "Resource": "*"
         }
     ]
}
```

## IAM policy for container products<a name="iam-user-policy-for-container-products"></a>

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "aws-marketplace:RegisterUsage"
                ],
                "Effect": "Allow",
                "Resource": "*"
        }
    ]
}
```

 For more information about creating IAM users, see [Creating an IAM User in Your AWS Account](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_create.html) in the *IAM User Guide*\. For more information about creating and assigning policies, see [Changing Permissions for an IAM User](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_change-permissions.html)\. 

 This policy grants access to the APIs for the IAM role or user that you attach the policy to\. For more information on how to enable role assumption by another account for these API calls, see [How to Best Architect Your AWS Marketplace SaaS Subscription Across Multiple AWS Accounts](http://aws.amazon.com/blogs/apn/how-to-best-architect-your-aws-marketplace-saas-subscription-across-multiple-aws-accounts/) at the AWS Partner Network \(APN\) Blog\. 