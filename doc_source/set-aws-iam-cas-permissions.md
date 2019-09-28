# AWS Commerce Analytics Service Account Permissions<a name="set-aws-iam-cas-permissions"></a>

 To provide a user access to the AWS Marketplace Commerce Analytics Service, assign an IAM permission policy with the following permissions to a group or role that the user is a member of\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
            "iam:Generate*",
            "iam:Get*",
            "iam:List*",
            "iam:Simulate*"
            ],
            "Resource": "arn:aws:iam::123456789123:user/goldmine-test-seller-with-customer-support-policy"
            }
            ]
        }
```