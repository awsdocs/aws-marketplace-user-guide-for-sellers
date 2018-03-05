# Controlling Access to AWS Marketplace Subscriptions<a name="ControllingAccessToAWSMarketplaceSubscriptions"></a>

As explained in [Controlling Access to AWS Marketplace](what-is-marketplace.md#controlling-access-to-marketplace), the best way to let others in your organization manage subscriptions is to use AWS Identity and Access Management \(IAM\) to create users and groups\. For example, if user John should only be allowed to view your subscriptions, you can create an IAM user for him and add his IAM user to the read\-only group\. If John's role in your organization changes or he leaves the company, you can change the group that his IAM user belongs to, or you can change his user's settings in IAM\. 

**Important**  
All of your users work on the same AWS Marketplace account\. Any change that a user makes to manage a software subscription is global and applies to all your users for that subscription\. 

## Creating Users<a name="CreatingIAMUsersForAWSMarketplace"></a>

To let people in your company manage subscriptions, you have to create a user for each person\. 

**To create IAM users**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the left navigation pane, choose **Users**, and then choose **Create New Users**\.

1. In the numbered text boxes, type a name for each user that you want to create\.

1. Clear the **Generate an access key for each user** check box, and then choose **Create**\.

**To assign a password to each user you just created**

1. In the list of users, choose the name of a new user\.

1. Choose the **Security Credentials** tab, and then choose **Manage Password**\.

1. Choose an option for either an auto\-generated password or a custom password\. Optionally, to require the user to choose a new password at the next sign\-in, select the box for **Require user to create a new password at next sign\-in**\. Choose **Apply**\.

1. Choose **Download Credentials** to save the user name, password, and account\-specific sign\-in URL to a comma\-separated values \(CSV\) file on your computer\. Then choose **Close**\.

**Note**  
To sign in with the IAM user name and password you just created, users must navigate to your account\-specific sign\-in URL\. This URL is in the credentials file that you just downloaded, and is also available in the IAM console\. For more information, see [How IAM Users Sign In to Your AWS Account](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_sign-in.html) in the *IAM User Guide*\.

**Tip**  
Create a user name and password for yourself as well, even though you are the AWS account owner\. It is a recommended best practice for everyone to work in the AWS Marketplace as an IAM user, even the account owner\. To learn how to create an IAM user for yourself that has administrative permissions, go to [Creating an Administrators Group](http://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html) in the *IAM User Guide*\.

## Creating Groups for AWS Marketplace Access and Adding Users to the Groups<a name="CreatingGroupsForAWSMarketplaceAccess"></a>

After creating users, you need to create groups with custom permissions\.

**To create groups for assigning AWS Marketplace permissions**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the left navigation pane, choose **Groups**, and then choose **Create New Group**\. 

1. For **Group Name:**, type a name for the group such as **MarketplaceReadOnly** or **MarketplaceFullAccess**\. Then choose **Next Step**\.

1. On the **Attach Policy** page, select the box next to one of the following policies: 

   + To allow permissions only to view subscriptions \(but not change them\), choose **AWS MarketplaceRead\-only**\.

   + To allow permissions to subscribe and unsubscribe, choose **AWS MarketplaceManageSubscriptions**\.

   + To allow complete control of your subscriptions, choose **AWS MarketplaceFullAccess**\.

1. Choose **Next Step**, and then choose **Create Group**\.

**To add users to the groups you just created**

1. In the list of groups, choose the name of the group\. 

1. Under **Users**, choose **Add Users to Group**\. 

1. Select the users to add to the group and then choose **Add Users**\.

Repeat the preceding steps to create more groups with different permissions and assign users to those groups\.

You are not limited to the permissions in the AWS managed policies that are described here\. You can use AWS Identity and Access Management \(IAM\) to create policies with custom permissions, and then add those policies to IAM groups\. For more information, go to [Creating Customer Managed Policies](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-using.html#create-managed-policy-console) and [Attaching a Policy to an IAM Group](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups_manage_attach-policy.html) in the *IAM User Guide*\. 

**Note**  
To see details about the AWS managed policies described in the preceding sections, go to [Permissions Details for Managing AWS Marketplace Subscriptions](#SummaryOfAWSMarketplaceSubscriptionsPermissions)\.

## Signing in as an IAM User<a name="LoggingInUsingAUserNameThatYouCreated"></a>

After you've created users in IAM, users can sign in with their own user names and passwords\. To do so, they need to use a unique URL that is associated with your AWS account\.

**To get your account's unique sign\-in URL**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the left navigation pane, choose **Dashboard**\.

1. Near the top of the content pane, look for **IAM users sign\-in link:** and take note of the sign\-in link, which will have a format like this:

   ```
    https://AWS_account_ID.signin.aws.amazon.com/console/
   ```
**Note**  
If you want the URL for your sign\-in page to contain your company name \(or other friendly identifier\) instead of your AWS account ID, you can create an alias for your AWS account by choosing **Customize**\. For more information, go to [Your AWS Account ID and Its Alias](http://docs.aws.amazon.com/IAM/latest/UserGuide/console_account-alias.html) in the *IAM User Guide*\. 

1. Distribute this URL to the people at your company who can work with AWS Marketplace, along with the user name and password that you created for each\. Instruct them to use your account's unique sign\-in URL to sign in before they access the AWS Marketplace\. 

As users work in AWS Marketplace, AWS enforces the appropriate permissions\. For example, user John might belong to a group that has only read\-only permissions to work with your subscriptions\. When he signs in to AWS Marketplace, he can choose the **Your Software** link at the top of the page: 

![\["Your Software" link on the AWS Marketplace web page.\]](http://docs.aws.amazon.com/marketplace/latest/controlling-access/images/AWS-Marketplace-YourSoftwareLink-2.png)

When user John does this, a message tells him that he does not have permissions to manage software:

![\[Message in AWS Marketplace showing that the current user does not have permissions to carry out an operation.\]](http://docs.aws.amazon.com/marketplace/latest/controlling-access/images/AWS-Marketplace-SubscribeError.png)![\[Message in AWS Marketplace showing that the current user does not have permissions to carry out an operation.\]](http://docs.aws.amazon.com/marketplace/latest/controlling-access/)![\[Message in AWS Marketplace showing that the current user does not have permissions to carry out an operation.\]](http://docs.aws.amazon.com/marketplace/latest/controlling-access/)

## Finding the Account Number for Customer Support<a name="GettingSupport"></a>

If you or your users need to contact customer service, you need your AWS account number\.

**To get your AWS account number**

1. Sign in to the [AWS Management Console](https://console.aws.amazon.com/console/home) with your IAM user name\. 

1. In the top navigation bar, choose **Support**, and then choose **Support Center**\.

Your AWS account ID \(account number\) is shown below the top navigation bar\.

## Permissions Details for Managing AWS Marketplace Subscriptions<a name="SummaryOfAWSMarketplaceSubscriptionsPermissions"></a>

You may need in\-depth information about the permissions that control AWS Marketplace subscriptions for several reasons:

+ You are curious about the details of the IAM permissions in the AWS managed policies\.

+ You want to create a custom policy with permissions that differ from the AWS managed policies\. For more information about creating custom policies, go to [Creating Customer Managed Policies](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-using.html#create-managed-policy-console) in the *IAM User Guide*\.

+ You are making API requests to AWS Marketplace, and you need to see what the policy language looks like for setting permissions\.

The following actions are available for managing AWS Marketplace subscriptions; that is, the actions are available in the `aws-marketplace` namespace\. \(For more information about namespaces, see [AWS Service Namespaces](http://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html#genref-aws-service-namespaces) in the *Amazon Web Services General Reference*\.\) This section also includes the policy documents for the AWS managed policies that provide access to AWS Marketplace, which illustrate how to use these actions to grant permissions in a policy statement\. Some of the permissions in these policies pertain to Amazon EC2, because managing subscriptions includes managing the EC2 instances that run your subscribed software\. 

**`aws-marketplace:ViewSubscriptions`**  
Allows users to see subscribed software\. Without this permission, no other permissions will work\.

**`aws-marketplace:Subscribe`**  
Allows users to add new software subscriptions on the **Your Software** page\.   
Some software subscriptions incur charges as soon as they are subscribed, even if no instances are launched\. Granting this permission could result in charges to your account\.
Allowing this action does not allow a user to start, stop, or otherwise manipulate instances\. The user must have Amazon EC2 permissions in order to manipulate instances from AWS Marketplace\. See the example policies that follow\. 

**`aws-marketplace:Unsubscribe`**  
Allows users to remove software subscriptions from the **Your Software** page\. However, unsubscribing might fail if there are running instances of the software\.  
Allowing this action does not allow a user to start, stop, or otherwise manipulate instances\. The user must have Amazon EC2 permissions in order to manipulate instances from AWS Marketplace\. See the example policies that follow\.

## AWS MarketplaceRead\-only<a name="AWSMarketplaceReadOnlyPolicy"></a>

The following policy defines read\-only permissions that let users view subscriptions without being able to make any changes:

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": [
        "aws-marketplace:ViewSubscriptions",
        "ec2:DescribeAccountAttributes",
        "ec2:DescribeAddresses",
        "ec2:DescribeImages",
        "ec2:DescribeInstances",
        "ec2:DescribeKeyPairs",
        "ec2:DescribeSecurityGroups",
        "ec2:DescribeSubnets",
        "ec2:DescribeVpcs"
      ],
      "Effect": "Allow",
      "Resource": "*"
    }
  ]
}
```

## AWS MarketplaceManageSubscriptions<a name="AWSMarketplaceSubscribeAndUnsubscribePolicy"></a>

The following policy defines permissions that let the user subscribe and unsubscribe from AWS Marketplace software:

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Action": [
        "aws-marketplace:ViewSubscriptions",
        "aws-marketplace:Subscribe",
        "aws-marketplace:Unsubscribe"
      ],
      "Effect": "Allow",
      "Resource": "*"
    }
  ]
}
```

## AWS MarketplaceFullAccess<a name="AWSMarketplaceFullPermissionsPolicy"></a>

The following policy defines permissions that let users perform all tasks associated with subscriptions: subscribe and unsubscribe from AWS Marketplace software; and view, start, and stop EC2 instances:

```
{
    "Version": "2012-10-17",
    "Statement": [
      {
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
          "ec2:DescribeAccountAttributes",
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
        "Effect": "Allow",
        "Resource": "*"
      }
    ]
}
```

## Additional Resources<a name="AWSMarketplacePermissionsForMoreInformation"></a>

For more information about managing IAM users and groups, go to [Identities \(Users, Groups, and Roles\)](http://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) in the *IAM User Guide*\. 

For more information about managing IAM permissions and policies, go to [Overview of AWS IAM Permissions](http://docs.aws.amazon.com/IAM/latest/UserGuide/access_permissions.html) in the *IAM User Guide*\. 