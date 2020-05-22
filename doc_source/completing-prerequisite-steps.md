# Completing prerequisite steps<a name="completing-prerequisite-steps"></a>

 The prerequisite steps described here require administrative\-level permissions that configure IAM so that you can grant the ability to build private images to other users\. Once the IAM policies and roles are created you can attach them to group \(or user\) accounts so the associated users can build private images\. 

 IAM is a web service that helps you securely control access to AWS resources\. You use IAM to control who is authenticated \(signed in\) and authorized \(has permissions\) to use resources\. You create [identities](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html#id_iam-users) \(users, groups, and roles\) and add the users to the groups so you can then manage groups instead of individual users\. An IAM role is similar to a user in that it's an identity with permission policies that determine what the identity can and can't do in AWS\. However, a role doesn't have any credentials \(password or access keys\) associated with it\. Instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it\. An IAM user can assume a role to temporarily take on different permissions for a specific task\. 

 The [access management](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_access-management.html) portion of IAM helps you to define what a user or other entity is allowed to do in an account, often referred to as *authorization*\. Permissions are granted through policies\. A policy is an entity in AWS that, when attached to an identity or resource, defines their permissions\. AWS evaluates these policies when a principal, such as a user, makes a request\. Permissions in the policies determine whether the request is allowed or denied\. Policies are stored in AWS as JSON documents attached to principals as *identity\-based policies* or to resources as *resource\-based policies*\.You give permissions by defining [permission policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_access-management.html) and assigning the policy to a group\. 

 [Identity\-based policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_access-management.html#intro-access-resource-based-policies) are permission policies that you can attach to a principal \(or identity\), such as an IAM user, role, or group\. Resource\-based policies are JSON policy documents that you attach to a resource such as an Amazon Simple Storage Service \(Amazon S3\) bucket\. Identity\-based policies control what actions that identity can perform, on which resources, and under what conditions\. Identity\-based policies can be categorized into *AWS managed policies*, *customer managed policies*, and *inline policies*\. 

 Resource\-based policies control what actions a specified principal can perform on that resource and under what conditions\. Resource\-based policies are inline policies, and there are no managed resource\-based policies\. Although IAM identities are technically AWS resources, you can't attach a resource\-based policy to an IAM identity\. You must use identity\-based policies in IAM\. *Trust policies* are resource\-based policies that are attached to a role that define which principals can assume the role\. When you create a role in IAM, the role must have two things: a trust policy that indicates who can assume the role and a permission policy that indicates what they can do with that role\. Remember that adding an account to the trust policy of a role is only half of establishing the trust relationship\. By default, no users in the trusted accounts can assume the role until the administrator for that account grants the users the permission to assume the role\. 

 The AWS Marketplace Image Building Service uses two IAM roles, and each role has a permissions policy and a trust policy\. If you have IAM users access the AWS Marketplace website to build private images, those users also need IAM permissions to list and assign the roles needed to create and view the private images they build\. 

 As an administrator, you create the two roles that are required and their associated policies\. The first role is an [instance profile](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2_instance-profiles.html#instance-profiles-manage-console) that is attached to the instance created during the image build process\. An instance profile is a container for an IAM role that you can use to pass role information to an Amazon EC2 instance when the instance starts\. The second is an IAM role that provides access to [AWS Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/auth-and-access-control.html) and Amazon EC2\. To configure the instance profile, attach a permissions policy that provides the required permissions\. Then edit the trust policy for the role to grant permission for Amazon EC2 and AWS Systems Manager to assume the role\. 

## Creating an instance profile role<a name="creating-an-instance-profile-role"></a>

 To create the instance profile role through the IAM console: 

1.  Sign in to the AWS Management Console and open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\. 

1.  In the navigation pane of the IAM console, choose **Roles** and then choose **Create role**\. 

1.  For **Select type of trusted entity**, choose **AWS service**\. 

1.  For **Choose the service that will use this role**, choose **EC2** and then choose **Next: Permissions**\. 

1.  For **Create policy**, choose **Next: Review**\. 

1.  For **Role name**, type a role name or role name suffix to help you identify the purpose of this role, for example *MyInstanceRole*\. Role names must be unique in your AWS account\. 

1.  Review the role and then choose **Create role**\. 

1.  On the **Roles** page, choose the role that you created\. 

1.  For **Permissions**, choose **Add inline policy**\. 

1.  Choose the **JSON** tab and replace all of the text with the following InstanceRolePermissionsPolicy text\. 

    InstanceRolePermissionsPolicy: 

   ```
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Action": [
                   "ssm:DescribeAssociation",
                   "ssm:GetDocument",
                   "ssm:GetManifest",
                   "ssm:GetParameters",
                   "ssm:ListAssociations",
                   "ssm:ListInstanceAssociations",
                   "ssm:PutConfigurePackageResult",
                   "ssm:UpdateAssociationStatus",
                   "ssm:UpdateInstanceAssociationStatus",
                   "ssm:UpdateInstanceInformation"
               ],
               "Resource": "*",
               "Effect": "Allow"
           },
           {
               "Action": [
                   "ec2messages:AcknowledgeMessage",
                   "ec2messages:DeleteMessage",
                   "ec2messages:FailMessage",
                   "ec2messages:GetEndpoint",
                   "ec2messages:GetMessages",
                   "ec2messages:SendReply"
               ],
               "Resource": "*",
               "Effect": "Allow"
           },
           {
               "Action": [
                   "ec2:DescribeInstanceStatus"
               ],
               "Resource": "*",
               "Effect": "Allow"
           },
           {
               "Action": [
                   "s3:GetObject",
                   "s3:PutObject"
               ],
               "Resource": "arn:aws:s3:::awsexamplebucket>/*",
               "Effect": "Allow"
           }
       ]
   }
   ```
**Note**  
You'll need to create the bucket, *awsexamplebucket* before you begin this process\. 

1.  Choose **Review policy**\. 

1.  For **Policy name**, type a name to help you identify the purpose of this policy, for example *MyInstanceRolePolicy*, and choose **Create policy**\. 

 **To edit the trust relationship for the role**: 

1.  On the **Roles** page, choose the role that you created\. 

1.  Choose the **Trust relationships** tab and then choose **Edit trust relationship**\. 

1.  Select all of the text in the **Policy Document** text box and replace it with the following InstanceRoleTrustPolicy text\. 

    InstanceRoleTrustPolicy: 

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Principal": {
           "Service": [
             "ssm.amazonaws.com",
             "ec2.amazonaws.com"
           ]
         },
         "Action": "sts:AssumeRole"
       }
     ]
   }
   ```

1.  Choose **Update Trust Policy**\. 

## Creating an AWS Systems Manager automation role<a name="creating-an-aws-systems-manager-automation-role"></a>

 To create the AWS Systems Automation role: 

1.  In the navigation pane of the IAM console, choose **Roles** and then choose **Create role**\. 

1.  For **Select type of trusted entity**, choose **AWS service**\. 

1.  For **Choose the service that will use this role**, choose **EC2** and then choose **Next: Permissions**\. 

1.  For **Create policy**, choose **Next: Review**\. 

1.  For **Role name**, type a role name or role name suffix to help you identify the purpose of this role, for example *MyAutomationRole*\. Role names must be unique in your AWS account\. 

1.  Review the role and then choose **Create role**\. 

1.  On the **Roles** page, choose the role that you created\. 

1.  For **Permissions**, choose **Add inline policy**\. 

1.  Choose the **JSON** tab and replace all the text with the following AutomationRolePermissionsPolicy text\. 

    AutomationRolePermissionsPolicy: 

   ```
       "Version": "2012-10-17",
       "Statement": [
           {
               "Action": [
                   "ssm:*"
               ],
               "Resource": [
                   "*"
               ],
               "Effect": "Allow"
           },
           {
               "Action": [
                   "ec2:CreateImage",
                   "ec2:DescribeImages",
                   "ec2:StartInstances",
                   "ec2:RunInstances",
                   "ec2:StopInstances",
                   "ec2:TerminateInstances",
                   "ec2:DescribeInstanceStatus",
                   "ec2:CreateTags",
                   "ec2:DescribeTags"
               ],
               "Resource": [
                   "*"
               ],
               "Effect": "Allow"
           },
           {
               "Action": [
                   "iam:PassRole"
               ],
               "Resource": [
                   "{{ Instance Profile }}"
               ],
               "Effect": "Allow"
           }
       ]
   }
   ```
**Note**  
 You must replace *\{\{ Instance Profile \}\}* with the Amazon Resource Name \(ARN\) for the instance policy role that you created earlier\. Locate the role in the IAM management console and choose it\. On the summary page for the role, the **Role ARN** is the first item listed, for example, **arn:aws:iam::123456789012:role/MyInstanceRole**\. 

 **To edit the trust relationship for the role**: 

1.  On the **Roles** page, choose the role that you created\. 

1.  Choose the **Trust relationships** tab and then choose **Edit trust relationship**\. 

1.  Replace all the text in the **Policy Document** text box with the following InstanceRoleTrustPolicy text\. 

    AutomationRoleTrustPolicy: 

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Principal": {
           "Service": [
             "ssm.amazonaws.com",
             "ec2.amazonaws.com"
           ]
         },
         "Action": "sts:AssumeRole"
       }
     ]
   }
   ```

1.  Choose **Update Trust Policy**\. 

 You have now created the two roles and associated policies that you will use during the private image build process\. 

## Using a policy to access the AWS Marketplace website<a name="using-a-policy-to-access-the-aws-marketplace-website"></a>

 Most organizations don't allow users to log in with root account credentials\. Instead, they create IAM users with limited permissions based on organizational roles or tasks that only certain people can perform\. AWS Marketplace provides two primary IAM managed policies for working with AWS Marketplace tools\. Use these two managed policies to provide the ability to perform the described tasks: 
+  **AWSMarketplaceFullAccess** \- Provides the ability to subscribe and unsubscribe to AWS Marketplace software, allows users to manage Marketplace software instances from the Marketplace 'Your Software' page, and provides administrative access to EC2\. 
+  **AWSMarketplaceRead\-only** – Provides the ability to review AWS subscriptions\. 

 You can add the managed policy named AWSMarketplaceFullAccess to an IAM user, group, or role to provide all of the permissions needed to access the AWS Marketplace website and perform the tasks associated with AWS Marketplace Private Image Build\. To add the policy to a user, group or role: 

1.  Sign in to the AWS Management Console and open the AWS IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\. 

1.  In the navigation pane of the AWS IAM console, choose **Policies**\. 

1.  Next to **Filter policies**, enter *AWSMarketplaceFullAccess*\. The policy should be listed in the results\. 

1.  In the **Results** pane, choose **AWSMarketplaceFullAccess**\. 

1.  In the **Policy actions** pulldown menu, choose **Attach**\. 

1.  Select the users, groups and roles you want to attach this policy to, and then choose **Attach Policy**\. 

 The next time that a user or member of a group or role you selected accesses the AWS Marketplace website, they can perform the tasks associated with the private image build process\. 