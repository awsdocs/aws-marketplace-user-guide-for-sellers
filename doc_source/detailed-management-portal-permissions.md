# Policies and permissions for AWS Marketplace sellers<a name="detailed-management-portal-permissions"></a>

 AWS Marketplace has three managed policies you can use with the AWS Marketplace Management Portal\. In addition, you can use individual permissions to create your own AWS Identity and Access Management \(IAM\) policy\. 

**Note**  
To learn about policies and permissions on AWS Data Exchange for data products, see [Identity and Access Management in AWS Data Exchange](https://docs.aws.amazon.com/data-exchange/latest/userguide/auth-access.html) in the *AWS Data Exchange User Guide*\.

## Policies for AWS Marketplace sellers<a name="seller-managed-policies"></a>

You can use the following managed policies to provide IAM users with controlled access to the AWS Marketplace Management Portal:

**`AWSMarketplaceSellerFullAccess`**  
Allows full access to all of the pages in the AWS Marketplace Management Portal and other AWS services, such as Amazon Machine Image \(AMI\) management\.

**`AWSMarketplaceSellerProductsFullAccess`**  
Allows full access to the [Products](https://aws.amazon.com/marketplace/management/products/) pages in the AWS Marketplace Management Portal\.

**`AWSMarketplaceSellerProductsReadOnly`**  
Allows read\-only access to the [Products](https://aws.amazon.com/marketplace/management/products/) pages in the AWS Marketplace Management Portal\.

**Important**  
AWS Marketplace buyers can use managed policies to manage the subscriptions they purchase\. The managed policies you use with AWS Marketplace Management Portal start with `AWSMarketplaceSeller`\. When you search for policies in IAM, make sure to search for policies that start with `AWSMarketplaceSeller`\. 

AWS Marketplace also provides specialized managed policies for specific scenarios\. For a full list of AWS managed policies for AWS Marketplace sellers, as well as descriptions of what permissions they provide, see [AWS managed policies for AWS Marketplace sellers](security-iam-awsmanpol.md)\.

## Permissions for AWS Marketplace sellers<a name="seller-ammp-permissions"></a>

You can use the following permissions in IAM policies for the AWS Marketplace Management Portal:

**`aws-marketplace-management:viewMarketing`**  
Allows access to the [Marketing](https://aws.amazon.com/marketplace/management/marketing/) page in the AWS Marketplace Management Portal\.

**`aws-marketplace-management:viewSupport`**  
Allows access to the [Customer Support Eligibility](https://aws.amazon.com/marketplace/management/support/) page in the AWS Marketplace Management Portal\.

**`aws-marketplace-management:viewReports`**  
Allows access to the [Reports](https://aws.amazon.com/marketplace/management/reports/) page in the AWS Marketplace Management Portal\.

**`aws-marketplace-management:uploadFiles`**  
Allows access to the [File Upload](https://aws.amazon.com/marketplace/management/product-load/) page in the AWS Marketplace Management Portal\.

**`aws-marketplace-management:viewSettings`**  
Allows access to the [Settings](https://aws.amazon.com/marketplace/management/seller-settings/account) page in the AWS Marketplace Management Portal\. 

**`aws-marketplace:SearchAgreements`**  
Allows viewing the high\-level list of agreements on the [**Agreements**](private-offers-upgrades-and-renewals.md) page, as well as opportunities between ISVs and consulting partners on the [**Partners**](consulting-partner-offers.md) page\.

**`aws-marketplace:DescribeAgreement`**  
Allows viewing of high\-level agreement details on the **Agreements** page, as well as opportunities between ISVs and consulting partners on the **Partners** page\.

**`aws-marketplace:GetAgreementTerms`**  
Allows viewing all agreement term details on the **Agreements** page, as well as opportunities between ISVs and consulting partners on the **Partners** page\.

**Note**  
 To enable a user to access the [Manage Products](https://aws.amazon.com/marketplace/management/products/) page, you must use either the `AWSMarketplaceSellerProductsFullAccess` or `AWSMarketplaceSellerProductsReadOnly` managed permissions\. 

You can combine the preceding permissions into a single IAM policy to grant the permissions that you want\. See the following examples\.

### Example 1: Permissions to access the Marketing and File Upload pages\.<a name="seller-ammp-permissions-example1"></a>

To grant permissions to both the **Marketing** page and the **File Upload** page, use a policy similar to the following example\. 

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": [
      "aws-marketplace-management:viewMarketing",
      "aws-marketplace-management:uploadFiles"
    ],
    "Resource": ["*"]
  }]
}
```

### Example 2: Permissions to create upgrades and renewals for private offers<a name="seller-ammp-permissions-example2"></a>

To grant permissions to view and use the **Agreements** page to create upgrades and renewals for private offers, use a policy similar to the following example\.

```
{
    "Version": "2012-10-17",
    "Statement": [
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
        }
    ]
}
```

### Using IAM groups<a name="seller-ammp-permissions-iam-groups"></a>

Alternatively, you can create separate IAM groups for granting access to each individual page in the AWS Marketplace Management Portal\. Users can belong to more than one group\. So, if a user needs access to more than one page, you can add the user to all of the appropriate groups\. For example, create one IAM group and grant that group permission to access the **Marketing** page, create another group and grant that group permission to access the **File Upload** page, and so on\. If a user needs permission to access both the **Marketing** page and the **File Upload** page, add the user to both groups\.

For more information about IAM users and groups, see [Identities \(Users, Groups, and Roles\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) in the *IAM User Guide*\. 