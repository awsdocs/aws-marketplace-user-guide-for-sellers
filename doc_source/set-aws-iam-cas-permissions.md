# AWS Marketplace Commerce Analytics Service account permissions<a name="set-aws-iam-cas-permissions"></a>

You can use the following IAM permission policy to allow an IAM user to access the AWS Marketplace Commerce Analytics Service\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "marketplacecommerceanalytics:GenerateDataSet",
            "Resource": "*"
        },
    ]
}
```

For more information about this feature, see [AWS Marketplace Commerce Analytics Service](commerce-analytics-service.md)\.