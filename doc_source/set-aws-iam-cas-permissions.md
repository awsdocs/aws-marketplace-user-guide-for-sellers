# AWS Marketplace Commerce Analytics Service account permissions<a name="set-aws-iam-cas-permissions"></a>

Use the following IAM permission policy to enroll in the AWS Marketplace Commerce Analytics Service\. 

Follow the [onboarding guide](https://docs.aws.amazon.com/marketplace/latest/userguide/commerce-analytics-service.html#on-boarding-guide) for instructions on how to enroll\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "iam:ListRoles",
                "iam:CreateRole",
                "iam:CreatePolicy",
                "iam:AttachRolePolicy",
                "aws-marketplace-management:viewReports"
            ],
            "Resource": "*"
        }
    ]
}
```

Use the following IAM permission policy to allow an IAM user to make requests to the AWS Marketplace Commerce Analytics Service\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "marketplacecommerceanalytics:GenerateDataSet",
            "Resource": "*"
        }
    ]
}
```

For more information about this feature, see [AWS MarketplaceCommerce Analytics Service](commerce-analytics-service.md)\.