# Controlling AWS Marketplace Management Portal Access<a name="marketplace-management-portal-user-access"></a>

The best way to let others in your organization use the AWS Marketplace Management Portal is to use AWS Identity and Access Management \(IAM\) to create users and groups\. For example, if Jane should only be allowed to view the Customer Support Eligibility page, you can create a user for her and add her to a group with only that level of access\. If Jane's role in the organization changes or she leaves the company, you can change the group that her IAM user belongs to, or you can change her user settings in IAM\.

## Creating Users<a name="creating-iam-users"></a>

To allow people in your company to sign in to the AWS Marketplace Management Portal, you must create an IAM user for each person you want to have access\.

**To create IAM users**

1. Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the left navigation pane, choose **Users** and then choose **Create New Users**\.

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
Create a user name and password for yourself as well, even though you are the AWS account owner\. It's a recommended best practice for everyone to work in AWS Marketplace Management Portal as an IAM user, even the account owner\. To learn how to create an IAM user for yourself that has administrative permissions, go to [Creating an Administrators Group](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html) in the *IAM User Guide*\.

## Creating Groups with Appropriate Permissions and Adding Users to those Groups<a name="creating-iam-groups"></a>

After you create users, you create groups, create permissions to access the pages in the AWS Marketplace Management Portal, add those permissions to the groups, and then add users to the groups\.

When you assign permissions to a group, you allow any member of that group to perform specific actions\. When you add a new user to the group, that user automatically gains the permissions that are assigned to the group\. A group can have permissions for more than one action\. 

**To create a policy with AWS Marketplace Management Portal permissions**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the left navigation pane, choose **Policies** and then choose **Create Policy**\.

1. Next to **Policy Generator**, choose **Select**\. 

1. On the **Edit Permissions** page, do the following:

   1. For **Effect**, choose **Allow**\.

   1. For **AWS Service**, choose **AWS Marketplace Management Portal**\.

   1. For **Actions**, select the permission\(s\) to allow\.

   1. Choose **Add Statement**\. 

   1. Choose **Next Step**\. 

1. On the **Review Policy** page, do the following:

   1. For **Policy Name**, type a name for this policy\. Take note of the policy name because you need it for a later step\.

   1. \(Optional\) For **Description**, type a description for this policy\. 

   1. Choose **Create Policy**\. 

**To create an IAM group with appropriate permissions and add users to the group**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the left navigation pane, choose **Groups** and then choose **Create New Group**\. 

1. For **Group Name:**, type a name for the group\. Then choose **Next Step**\.

1. On the **Attach Policy** page, do the following:

   1. For **Filter:**, choose **Customer Managed Policies**\.

   1. Select the check box next to the name of the policy that you want to attach to this group\. This is typically the policy you just created\. 

   1. Choose **Next Step**\. 

1. Choose **Create Group**\. 

1. Find your new group in the **Groups** list and then select the check box next to it\. Choose **Group Actions**, **Add Users to Group**\.

1. Select the check box next to each user to add to the group and then choose **Add Users**\.

## Signing In to the AWS Marketplace Management Portal as an IAM User<a name="signing-in-using-iam-user"></a>

After you have created users in IAM, users can sign in with their own user names and passwords\. To do so, they need to use the unique URL that is associated with your AWS account\. You can get and distribute the sign\-in URL to your users\.

**To get your account's unique sign\-in URL**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the left navigation pane, choose **Dashboard**\.

1. Near the top of the content pane, find **IAM users sign\-in link:** and take note of the sign\-in link, which has a format like this:

   ```
    https://AWS_account_ID.signin.aws.amazon.com/console/
   ```
**Note**  
If you want the URL for your sign\-in page to contain your company name \(or other friendly identifier\) instead of your AWS account ID, you can create an alias for your account by choosing **Customize**\. For more information, see [Your AWS Account ID and Its Alias](https://docs.aws.amazon.com/IAM/latest/UserGuide/console_account-alias.html) in the *IAM User Guide*\. 

1. Distribute this URL to the people at your company who can work with AWS Marketplace Management Portal, along with the user name and password that you created for each\. Instruct them to use your account's unique sign\-in URL to sign in before they access AWS Marketplace Management Portal\. 

## Permissions Details for the AWS Marketplace Management Portal<a name="detailed-management-portal-permissions"></a>

The following permissions are available to use in policies for the AWS Marketplace Management Portal:

**`aws-marketplace-management:viewMarketing`**  
Allows a user to access the Marketing page inside the AWS Marketplace Management Portal at [https://aws\.amazon\.com/marketplace/management/marketing/](https://aws.amazon.com/marketplace/management/marketing/)\.

**`aws-marketplace-management:viewSupport`**  
Allows a user to access the Customer Support Eligibility page inside the AWS Marketplace Management Portal at [https://aws\.amazon\.com/marketplace/management/support/](https://aws.amazon.com/marketplace/management/support/)\.

**`aws-marketplace-management:viewReports`**  
Allows a user to access the Reports page inside the AWS Marketplace Management Portal at [https://aws\.amazon\.com/marketplace/management/reports/](https://aws.amazon.com/marketplace/management/reports/)\.

**`aws-marketplace-management:uploadFiles`**  
Allows a user to access the File Upload page inside the AWS Marketplace Management Portal at [https://aws\.amazon\.com/marketplace/management/product\-load/](https://aws.amazon.com/marketplace/management/product-load/)\.

**`aws-marketplace-management:viewSettings`**  
Allows a user to access the Settings page inside the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/)\.

**`aws-marketplace-management:*`**  
Allows a user full access to all of the pages inside the AWS Marketplace Management Portal, including the Manage Products page at [https://aws\.amazon\.com/marketplace/management/manage\-products/](https://aws.amazon.com/marketplace/management/manage-products/)\.  
To allow a user access to the Manage Products page, you must allow full access\. The Manage Products page doesn't currently have its own permission that you can allow separately from the others\.

You can combine the preceding permissions into a single IAM policy to grant the desired permissions\. For example, to grant permissions to both the Marketing page and the File Upload page, use a policy that looks like this: 

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

An alternate approach to combining multiple permissions in a single IAM policy is to create separate IAM groups for granting access to each individual page in the AWS Marketplace Management Portal\. Users can belong to more than one group, so if a user needs access to more than one page inside the AWS Marketplace Management Portal, you can add the user to all of the appropriate groups\. For example, you create one IAM group and grant that group permission to access the Marketing page, then create another group and grant that group permission to access the File Upload page, and so on\. If a user needs permission to access both the Marketing page and the File Upload page, you place the user into both groups\.

For more information about IAM users and groups, see [What Is IAM?](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) in *IAM User Guide*\. 