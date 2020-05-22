# Creating a private marketplace IT administrator<a name="it-administrator"></a>

You can create an IT administrators group to manage your company’s private marketplace settings\. Administrators for the private marketplace can control the appearance of the private marketplace user interface \(UI\) and can control what products users can buy\. You can also enable access to the private marketplace as part of an organization created in [AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/)\. Examples of tasks you can perform as an administrator of a private marketplace include the following: 
+ Enabling and disabling a private marketplace for your company\.
+ Adding products to your company's private marketplace\.
+ Removing products from your company's private marketplace\.
+ Configuring the user interface of your company's private marketplace\.

You grant IAM permissions to administer your private marketplace by attaching the **AWSPrivateMarketplaceAdminFullAccess** policy to an IAM user, group, or role\. We recommend using a group or role\. For more information about recommended practices for using IAM, see [IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)\.

For your reference, the **AWSPrivateMarketplaceAdminFullAccess** policy is shown following:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "aws-marketplace:CreatePrivateMarketplace",
                "aws-marketplace:CreatePrivateMarketplaceProfile",
                "aws-marketplace:UpdatePrivateMarketplaceProfile",
                "aws-marketplace:StartPrivateMarketplace",
                "aws-marketplace:StopPrivateMarketplace",
                "aws-marketplace:AssociateProductsWithPrivateMarketplace",
                "aws-marketplace:DisassociateProductsFromPrivateMarketplace",
                "aws-marketplace:DescribePrivateMarketplaceProfile",
                "aws-marketplace:DescribePrivateMarketplaceStatus",
                "aws-marketplace:ListPrivateMarketplaceProducts",
                "aws-marketplace:DescribePrivateMarketplaceProducts"
            ],
            "Resource": [
                "*"
            ]
        }
    ]
 }
```