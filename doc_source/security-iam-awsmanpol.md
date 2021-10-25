# AWS managed policies for AWS Marketplace sellers<a name="security-iam-awsmanpol"></a>

To add permissions to users, groups, and roles, it is easier to use AWS managed policies than to write policies yourself\. It takes time and expertise to [create IAM customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) that provide your team with only the permissions they need\. To get started quickly, you can use our AWS managed policies\. These policies cover common use cases and are available in your AWS account\. For more information about AWS managed policies, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

AWS services maintain and update AWS managed policies\. You can't change the permissions in AWS managed policies\. Services occasionally add additional permissions to an AWS managed policy to support new features\. This type of update affects all identities \(users, groups, and roles\) where the policy is attached\. Services are most likely to update an AWS managed policy when a new feature is launched or when new operations become available\. Services do not remove permissions from an AWS managed policy, so policy updates won't break your existing permissions\.

Additionally, AWS supports managed policies for job functions that span multiple services\. For example, the **ViewOnlyAccess** AWS managed policy provides read\-only access to many AWS services and resources\. When a service launches a new feature, AWS adds read\-only permissions for new operations and resources\. For a list and descriptions of job function policies, see [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.

This section lists each of the policies used to manage seller access to AWS Marketplace\. For information about buyer policies, see [AWS managed policies for AWS Marketplace buyers](https://docs.aws.amazon.com/marketplace/latest/buyerguide/buyer-security-iam-awsmanpol.html) in the *AWS Marketplace Buyer Guide*\.

**Topics**
+ [AWS managed policy: AWSMarketplaceAmiIngestion](#security-iam-awsmanpol-awsmarketplaceamiingestion)
+ [AWS managed policy: AWSMarketplaceFullAccess](#security-iam-awsmanpol-awsmarketplacefullaccess)
+ [AWS managed policy: AWSMarketplaceGetEntitlements](#security-iam-awsmanpol-awsmarketplacegetentitlements)
+ [AWS managed policy: AWSMarketplaceMeteringFullAccess](#security-iam-awsmanpol-awsmarketplacemeteringfullaccess)
+ [AWS managed policy: AWSMarketplaceMeteringRegisterUsage](#security-iam-awsmanpol-awsmarketplacemeteringregisterusage)
+ [AWS managed policy: AWSMarketplaceSellerFullAccess](#security-iam-awsmanpol-awsmarketplacesellerfullaccess)
+ [AWS managed policy: AWSMarketplaceSellerProductsFullAccess](#security-iam-awsmanpol-awsmarketplacesellerproductsfullaccess)
+ [AWS managed policy: AWSMarketplaceSellerProductsReadOnly](#security-iam-awsmanpol-awsmarketplacesellerproductsreadonly)
+ [AWS Marketplace updates to AWS managed policies](#security-iam-awsmanpol-updates)

## AWS managed policy: AWSMarketplaceAmiIngestion<a name="security-iam-awsmanpol-awsmarketplaceamiingestion"></a>

You can create a service role with this policy that can then be used by AWS Marketplace to perform actions on your behalf\. For more information about using AWSMarketplaceAmiIngestion, see [Giving AWS Marketplace access to your AMI](ami-single-ami-products.md#single-ami-marketplace-ami-access)\.

This policy is used to grant contributor permissions that allow AWS Marketplace to copy your Amazon Machine Images \(AMIs\) in order to list them on AWS Marketplace\.



**Permissions details**

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "ec2:ModifySnapshotAttribute"
            ],
            "Effect": "Allow",
            "Resource": "arn:aws:ec2:us-east-1::snapshot/snap-*"
        },
        {
            "Action": [
                "ec2:DescribeImageAttribute",
                "ec2:DescribeImages",
                "ec2:DescribeSnapshotAttribute",
                "ec2:ModifyImageAttribute"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```

## AWS managed policy: AWSMarketplaceFullAccess<a name="security-iam-awsmanpol-awsmarketplacefullaccess"></a>

You can attach the `AWSMarketplaceFullAccess` policy to your IAM identities\.

This policy grants administrative permissions that allow full access to AWS Marketplace and related services, both as a seller and a buyer\. These permissions include the ability to subscribe and unsubscribe to AWS Marketplace software, manage AWS Marketplace software instances from the AWS Marketplace, creating and managing private marketplace in your account, as well as access to Amazon EC2, AWS CloudFormation, and Amazon EC2 Systems Manager\.



**Permissions details**

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "aws-marketplace:*",
                "cloudformation:CreateStack",
                "cloudformation:DescribeStackResource",
                "cloudformation:DescribeStackResources",
                "cloudformation:DescribeStacks",
                "cloudformation:List*",
                "ec2:AuthorizeSecurityGroupEgress",
                "ec2:AuthorizeSecurityGroupIngress",
                "ec2:CreateSecurityGroup",
                "ec2:CreateTags",
                "ec2:DescribeAccountAttributes",
                "ec2:DescribeAddresses",
                "ec2:DeleteSecurityGroup",
                "ec2:DescribeImages",
                "ec2:DescribeInstances",
                "ec2:DescribeKeyPairs",
                "ec2:DescribeSecurityGroups",
                "ec2:DescribeSubnets",
                "ec2:DescribeTags",
                "ec2:DescribeVpcs",
                "ec2:RunInstances",
                "ec2:StartInstances",
                "ec2:StopInstances",
                "ec2:TerminateInstances"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "ec2:CopyImage",
                "ec2:DeregisterImage",
                "ec2:DescribeSnapshots",
                "ec2:DeleteSnapshot",
                "ec2:CreateImage",
                "ec2:DescribeInstanceStatus",
                "ssm:GetAutomationExecution",
                "ssm:UpdateDocumentDefaultVersion",
                "ssm:CreateDocument",
                "ssm:StartAutomationExecution",
                "ssm:ListDocuments",
                "ssm:UpdateDocument",
                "ssm:DescribeDocument",
                "sns:ListTopics",
                "sns:GetTopicAttributes",
                "sns:CreateTopic",
                "iam:GetRole",
                "iam:GetInstanceProfile",
                "iam:ListRoles",
                "iam:ListInstanceProfiles"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::*image-build*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "sns:Publish",
                "sns:setTopicAttributes"
            ],
            "Resource": "arn:aws:sns:*:*:*image-build*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "iam:PassRole"
            ],
            "Resource": [
                "*"
            ],
            "Condition": {
                "StringLike": {
                    "iam:PassedToService": [
                        "ec2.amazonaws.com",
                        "ssm.amazonaws.com"
                    ]
                }
            }
        }
    ]
}
```

## AWS managed policy: AWSMarketplaceGetEntitlements<a name="security-iam-awsmanpol-awsmarketplacegetentitlements"></a>

You can attach the `AWSMarketplaceGetEntitlements` policy to your IAM identities\.

This policy grants read\-only permissions that allow Software\-as\-a\-Service \(SaaS\)product sellers to check whether a customer has subscribed to their AWS Marketplace SaaS product\.

**Permissions details**

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "aws-marketplace:GetEntitlements"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```

## AWS managed policy: AWSMarketplaceMeteringFullAccess<a name="security-iam-awsmanpol-awsmarketplacemeteringfullaccess"></a>

You can attach the `AWSMarketplaceMeteringFullAccess` policy to your IAM identities\.

This policy grants contributor permissions that allow reporting metered usage that corresponds to AMI and container products with flexible consumption pricing on AWS Marketplace\.

**Permissions details**

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "aws-marketplace:MeterUsage"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```

## AWS managed policy: AWSMarketplaceMeteringRegisterUsage<a name="security-iam-awsmanpol-awsmarketplacemeteringregisterusage"></a>

You can attach the `AWSMarketplaceMeteringRegisterUsage` policy to your IAM identities\.

This policy grants contributor permissions that allow reporting metered usage that corresponds to container products with hourly pricing on AWS Marketplace\.

**Permissions details**

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

## AWS managed policy: AWSMarketplaceSellerFullAccess<a name="security-iam-awsmanpol-awsmarketplacesellerfullaccess"></a>

You can attach the `AWSMarketplaceSellerFullAccess` policy to your IAM identities\.

This policy grants administrative permissions that allow full access to all seller operations on AWS Marketplace, including AWS Marketplace Management Portal, as well as managing the Amazon EC2 Amazon Machine Images \(AMI\) used in AMI\-based products\.



**Permissions details**

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "aws-marketplace-management:uploadFiles",
                "aws-marketplace-management:viewMarketing",
                "aws-marketplace-management:viewReports",
                "aws-marketplace-management:viewSupport",
                "aws-marketplace-management:viewSettings",
                "aws-marketplace:ListChangeSets",
                "aws-marketplace:DescribeChangeSet",
                "aws-marketplace:StartChangeSet",
                "aws-marketplace:CancelChangeSet",
                "aws-marketplace:ListEntities",
                "aws-marketplace:DescribeEntity",
                "aws-marketplace:ListTasks",
                "aws-marketplace:DescribeTask",
                "aws-marketplace:UpdateTask",
                "aws-marketplace:CompleteTask",
                "ec2:DescribeImages",
                "ec2:DescribeSnapshots",
                "ec2:ModifyImageAttribute",
                "ec2:ModifySnapshotAttribute"
            ],
            "Resource": "*"
        },
        {
            "Action": [
                "aws-marketplace:SearchAgreements",
                "aws-marketplace:DescribeAgreement",
                "aws-marketplace:GetAgreementTerms"
            ],
            "Effect": "Allow",
            "Resource": "*",
            "Condition": {
                "StringEquals": {
                    "aws-marketplace:PartyType": "Proposer"
                },
                "ForAllValues:StringEquals": {
                    "aws-marketplace:AgreementType": [
                        "PurchaseAgreement"
                    ]
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "iam:GetRole",
                "iam:PassRole"
            ],
            "Resource": "arn:aws:iam::*:role/*",
            "Condition": {
                "StringEquals": {
                    "iam:PassedToService": "assets.marketplace.amazonaws.com"
                }
            }
        }
    ]
}
```

## AWS managed policy: AWSMarketplaceSellerProductsFullAccess<a name="security-iam-awsmanpol-awsmarketplacesellerproductsfullaccess"></a>

You can attach the `AWSMarketplaceSellerProductsFullAccess` policy to your IAM identities\.

This policy grants contributor permissions that allow full access to manage products and to the AWS Marketplace Management Portal, as well as managing the Amazon EC2 Amazon Machine Images \(AMI\) used in AMI\-based products\.

**Permissions details**

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "aws-marketplace:ListChangeSets",
                "aws-marketplace:DescribeChangeSet",
                "aws-marketplace:StartChangeSet",
                "aws-marketplace:CancelChangeSet",
                "aws-marketplace:ListEntities",
                "aws-marketplace:DescribeEntity",
                "aws-marketplace:ListTasks",
                "aws-marketplace:DescribeTask",
                "aws-marketplace:UpdateTask",
                "aws-marketplace:CompleteTask",
                "ec2:DescribeImages",
                "ec2:DescribeSnapshots",
                "ec2:ModifyImageAttribute",
                "ec2:ModifySnapshotAttribute"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "iam:GetRole",
                "iam:PassRole"
            ],
            "Resource": "arn:aws:iam::*:role/*",
            "Condition": {
                "StringEquals": {
                    "iam:PassedToService": "assets.marketplace.amazonaws.com"
                }
            }
        }
    ]
}
```

## AWS managed policy: AWSMarketplaceSellerProductsReadOnly<a name="security-iam-awsmanpol-awsmarketplacesellerproductsreadonly"></a>

You can attach the `AWSMarketplaceSellerProductsReadOnly` policy to your IAM identities\.

This policy grants read\-only permissions that allow access to view products on the AWS Marketplace Management Portal, as well as to view the Amazon EC2 Amazon Machine Images \(AMI\) used in AMI\-based products\.



**Permissions details**

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "aws-marketplace:ListChangeSets",
                "aws-marketplace:DescribeChangeSet",
                "aws-marketplace:ListEntities",
                "aws-marketplace:DescribeEntity",
                "aws-marketplace:ListTasks",
                "aws-marketplace:DescribeTask",
                "ec2:DescribeImages",
                "ec2:DescribeSnapshots"
            ],
            "Resource": "*"
        }
    ]
}
```



## AWS Marketplace updates to AWS managed policies<a name="security-iam-awsmanpol-updates"></a>

View details about updates to AWS managed policies for AWS Marketplace since this service began tracking these changes\. For automatic alerts about changes to this page, subscribe to the RSS feed on the AWS Marketplace [Document history](document-history.md) page\.






| Change | Description | Date | 
| --- | --- | --- | 
|  [ AWSMarketplaceFullAccess](#security-iam-awsmanpol-awsmarketplacefullaccess) – Update to an existing policy  |  AWS Marketplace removed a duplicate `ec2:DescribeAccountAttributes` permission from `AWSMarketplaceFullAccess` policy\.  | July 20, 2021 | 
|  AWS Marketplace started tracking changes  |  AWS Marketplace started tracking changes for its AWS managed policies\.  | April 20, 2021 | 