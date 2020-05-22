# Controlling access to AWS Marketplace Management Portal<a name="marketplace-management-portal-user-access"></a>

AWS Identity and Access Management \(IAM\) is an AWS service that helps you control access to AWS resources\. If you are an IAM administrator, you control who can be *authenticated* \(signed in\) and *authorized* \(have permissions\) to use AWS Marketplace resources\. IAM is an AWS service that you can use with no additional charge\. 

The recommended way to control who can do what in AWS Marketplace Management Portal is to use IAM to create users and groups\. Then you add the users to the groups, and manage the groups\. For example, if John should be allowed to view your products, create an IAM user for him and add his IAM user to a group you create for read\-only access\. You can assign a policy or permissions to the group that provide read\-only permissions\. If you have other users that need read\-only access, you can add them to the group you created rather than adding permissions to their user account\. If John's role changes and he no longer needs read\-only access, you can remove John's user account from the group\. 

A *policy* is a document that defines the permissions that apply to a user, group, or role\. In turn, the permissions determine what users can do in AWS\. A policy typically allows access to specific actions, and can optionally grant that the actions are allowed for specific resources, like Amazon EC2 instances, Amazon S3 buckets, and so on\. Policies can also explicitly deny access\. A *permission* is a statement within a policy that allows or denies access to a particular resource\. You can state any permission like this: "A has permission to do B to C\." For example, Jane \(A\) has permission to read messages \(B\) from John's Amazon Simple Queue Service queue \(C\)\. Whenever Jane sends a request to Amazon SQS to use John's queue, the service checks to see if she has permission\. It further checks to see if the request satisfies the conditions John specified in the permission\. 

**Important**  
All of the IAM users that you create authenticate by using their credentials\. However, they use the same AWS account\. Any change that a user makes can impact the whole account\. 

 AWS Marketplace has permissions defined to control the actions that someone with those permissions can take in AWS Marketplace Management Portal\. There are also policies that AWS Marketplace created and manage that combine several permissions\. For example, the `aws-marketplace-management:ViewMarketing` permission gives a user access to the **Marketing** tab in AWS Marketplace Management Portal\. The `AWSMarketplaceSellerProductsFullAccess` policy gives the user full access to products in the AWS Marketplace Management Portal\. 

 The following resources provide more information about getting started and using IAM\. 
+  [Creating Your First IAM Admin User and Group](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html) 
+  [IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) 
+  [Managing IAM Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-using.html#create-managed-policy-console) 
+  [Attaching a Policy to an IAM Group](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups_manage_attach-policy.html) 
+  [Identities \(Users, Groups, and Roles\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) 
+  [Controlling Access Using Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_permissions.html) 

 The following provides some high\-level guidance for creating users and groups, and logging in as an IAM user\. 

## Creating users<a name="creating-iam-users"></a>

To allow people in your company to sign in to the AWS Marketplace Management Portal, create an IAM user for each person who needs access\.

**To create IAM users**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Users** and then choose **Create New Users**\.

1. In the numbered text boxes, enter a name for each user that you want to create\.

1. Clear the **Generate an access key for each user** check box and then choose **Create**\.

**To assign a password to each user that you just created**

1. In the list of users, choose the name of a new user\.

1. Choose the **Security Credentials** tab and then choose **Manage Password**\.

1. Choose an option for either an auto\-generated password or a custom password\. Optionally, to require the user to choose a new password at the next sign\-in, select the box for **Require user to create a new password at next sign\-in**\. Choose **Apply**\.

1. Choose **Download Credentials** to save the user name, password, and account\-specific sign\-in URL to a comma\-separated values \(CSV\) file on your computer\. Then choose **Close**\.

**Note**  
To sign in with the IAM user name and password that you just created, users must navigate to your account\-specific sign\-in URL\. This URL is in the credentials file that you just downloaded and is also available on the IAM console\. For more information, see [How IAM Users Sign In to Your AWS Account](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_users_sign-in.html) in the *IAM User Guide*\.

**Tip**  
Create a user name and password for yourself as well, even though you're the AWS account owner\. It's a recommended best practice for everyone to work in the AWS Marketplace Management Portal as an IAM user, even the account owner\. To learn how to create an IAM user for yourself that has administrative permissions, go to [Creating an Administrators Group](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html) in the *IAM User Guide*\.

## Creating or using groups<a name="creating-iam-groups"></a>

 After you create users, create groups, create permissions to access the pages in the AWS Marketplace Management Portal, add those permissions to the groups, and then add users to the groups\. 

 When you assign permissions to a group, you allow any member of that group to perform specific actions\. When you add a new user to the group, that user automatically gains the permissions that are assigned to the group\. A group can have permissions for more than one action\. We recommend using a managed policy rather than creating your own policy\. 

**To assign a managed policy for AWS Marketplace to a group**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Groups**, and then choose the group you want to attach a policy to\.

1. On the summary page for the group, under the **Permissions** tab, choose **Attach Policy**\. 

1. On the **Attach Policy** page, next to **Filter:** enter awsmarketplace\. 

1. Choose the policy or policies you want to attach, and then choose **Attach Policy**\.

**To create a policy with AWS Marketplace Management Portal permissions**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Policies** and then choose **Create Policy**\.

1. Next to **Policy Generator**, choose **Select**\. 

1. On the **Edit Permissions** page, do the following:

   1. For **Effect**, choose **Allow**\.

   1. For **AWS Service**, choose **AWS Marketplace Management Portal**\.

   1. For **Actions**, select the permission or permissions to allow\.

   1. Choose **Add Statement**\. 

   1. Choose **Next Step**\. 

1. On the **Review Policy** page, do the following:

   1. For **Policy Name**, enter a name for this policy\. Take note of the policy name because you need it for a later step\.

   1. \(Optional\) For **Description**, enter a description for this policy\. 

   1. Choose **Create Policy**\. 

**To create an IAM group with appropriate permissions and add users to the group**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Groups** and then choose **Create New Group**\. 

1. For **Group Name:**, type a name for the group\. Then choose **Next Step**\.

1. On the **Attach Policy** page, do the following:

   1. For **Filter:**, choose **Customer Managed Policies**\.

   1. Select the check box next to the name of the policy that you want to attach to this group\. This is typically the policy that you just created\. 

   1. Choose **Next Step**\. 

1. Choose **Create Group**\. 

1. Find your new group in the **Groups** list and then select the check box next to it\. Choose **Group Actions** and then **Add Users to Group**\.

1. Select the check box next to each user to add to the group and then choose **Add Users**\.

## Signing in as an IAM user<a name="signing-in-using-iam-user"></a>

After you have created users in IAM, users can sign in with their own user names and passwords\. To do so, they need to use the unique URL that is associated with your AWS account\. You can get and distribute the sign\-in URL to your users\.

**To get your account's unique sign\-in URL**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Dashboard**\.

1. Near the top of the content pane, find **IAM users sign\-in link:** and take note of the sign\-in link, which has a format like this:

   ```
    https://AWS_account_ID.signin.aws.amazon.com/console/
   ```
**Note**  
If you want the URL for your sign\-in page to contain your company name \(or other friendly identifier\) instead of your AWS account ID, you can create an alias for your account by choosing **Customize**\. For more information, see [Your AWS Account ID and Its Alias](https://docs.aws.amazon.com/IAM/latest/UserGuide/console_account-alias.html) in the *IAM User Guide*\. 

1. Distribute this URL to the people at your company who can work with the AWS Marketplace Management Portal, along with the user name and password that you created for each\. Instruct them to use your account's unique sign\-in URL to sign in before they access the AWS Marketplace Management Portal\. 