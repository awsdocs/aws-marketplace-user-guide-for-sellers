# Signing in as an IAM user<a name="buyer-iam-user-login"></a>

After you have created users in IAM, users can sign in with their own user names and passwords\. To do so, they need to use a unique URL that is associated with your AWS account\.

**To get your account's unique sign\-in URL**

1. Open the IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\.

1. In the navigation pane, choose **Dashboard**\.

1. Near the top of the content pane, find **IAM users sign\-in link:** and take note of the sign\-in link, which has a format like this:

   ```
    https://AWS_account_ID.signin.aws.amazon.com/console/
   ```
**Note**  
If you want the URL for your sign\-in page to contain your company name \(or other friendly identifier\) instead of your AWS account ID, you can create an alias for your account by choosing **Customize**\. For more information, see [Your AWS Account ID and Its Alias](https://docs.aws.amazon.com/IAM/latest/UserGuide/console_account-alias.html) in the *IAM User Guide*\. 

1. Distribute this URL to the people at your company who can work with the AWS Marketplace, along with the user name and password that you created for each\. Instruct them to use your account's unique sign\-in URL to sign in before they access the AWS Marketplace\. 

As users work in AWS Marketplace, AWS enforces the appropriate permissions\. For example, user John might belong to a group that has only read\-only permissions to work with your subscriptions\. When he signs in to AWS Marketplace, he can choose the **Your Software** link at the top of the page\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/buyerguide/images/AWS-Marketplace-YourSoftwareLink-2.png)

When John does this, a message tells him that he doesn't have permissions to manage software, as shown in the following image\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/buyerguide/images/AWS-Marketplace-SubscribeError.png)