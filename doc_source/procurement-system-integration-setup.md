# Setting up Coupa integration<a name="procurement-system-integration-setup"></a>

To configure the integration between AWS Marketplace and Coupa, you start the process in AWS Marketplace and complete it in Coupa\. You use the information generated in AWS Marketplace to configure the Coupa punchout\. To complete the configuration, the accounts that you use must meet the following requirements:
+  The account used to complete the AWS Marketplace configuration must be the payer account and have the IAM permissions defined in the `AWSMarketplaceProcurementSystemAdminFullAccess` managed policy\.
+  The account used to complete the Coupa configuration must have Coupa administration access to set up a contract, supplier, and punchout\.

## Configuring IAM permissions<a name="procurement-system-integration-setup-iam-permissions"></a>

 The following AWS Identity and Access Management \(IAM\) permissions are in the `AWSMarketplaceProcurementSystemAdminFullAccess` managed policy and are required to configure the integration between AWS Marketplace and Coupa\. 

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "aws-marketplace:PutProcurementSystemConfiguration", 
        "aws-marketplace:DescribeProcurementSystemConfiguration",
        "organizations:Describe*",
        "organizations:List*"
      ],
      "Resource": [
        "*"
      ]
    }
  ]
}
```

 We recommend that you use IAM managed permissions rather than manually configuring permissions\. Using this approach is less prone to human error, and if the permissions change, the managed policy is updated\. For more information about configuring and using IAM, see the following topics:
+  For more information about managing IAM users and groups, see [Identities \(Users, Groups, and Roles\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) in the *IAM User Guide*
+  For more information about managing IAM permissions and policies, see [Controlling Access Using Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_permissions.html) in the *IAM User Guide*
+  For a description of AWS Marketplace managed policies, see [AWS managed policies for AWS Marketplace ](buyer-iam-users-groups-policies.md#buyer-iam-builtin-policies)
+  For more information about signing in as an IAM user, see [Signing in as an IAM user](buyer-iam-user-login.md)\.

## Configuring AWS Marketplace<a name="procurement-system-integration-setup-awsmp-configuration"></a>

 To configure AWS Marketplace to integrate with Coupa, navigate to **Manage procurement**\. In the **Manage procurement systems** pane, enter a name and description for the punchout, and can also configure integrated invoicing\. You can also switch the integration to test mode so that users can't make valid subscriptions until you're ready\. To configure the AWS Marketplace portion of the integration, complete the following procedure\. 

**To configure AWS Marketplace for integrating with Coupa**

1.  From [AWS Marketplace Manage Procurement Systems](https://aws.amazon.com/marketplace/eprocurement/overview), under **Procurement systems**, choose **Set up Coupa integration**\. 

1.  On the **Manage Coupa integration** page, under **Account information**, enter the name and description of your integration\. 

You use the information generated on this page to configure the punchout in your Coupa system\. The configuration defaults to test mode being enabled\. This helps you complete the configuration and enable the punchout in a planned manner\.

 You can also enable electronic invoicing from AWS Marketplace by entering a URL that you want the invoices delivered to\. This is likely a URL for the Coupa system\. 

## Configuring Coupa<a name="procurement-system-integration-setup-coupa-configuration"></a>

 To configure the integration with AWS Marketplace in your Coupa system, copy the information from the **Purchase information** pane of the **Manage Coupa integration** page in AWS Marketplace\. Use this information to complete the steps in the following links and guide you through configuring your Coupa procurement system\. 
+  [Punchout Setup](https://success.coupa.com/Suppliers/For_Customers/Toolkit/Manage_Catalogs/Punchout_Catalogs/Punchout_Setup) 
+  [Configuring a Supplier for cXML Purchase Orders](https://success.coupa.com/Suppliers/For_Customers/Toolkit/Document_Exchange/cXML/Configuring_a_Supplier_for_cXML_Purchase_Orders) 

 AWS Marketplace includes the following United Nations standard products and services code \(UNSPSC\) codes for the software listings sent back to Coupa's cart:
+  Software\-as\-a\-service \(SaaS\) products: 81162000 
+  Application server products: 43232701 
+  Other software, such as containers, AWS WAF rules, and machine learning \(ML\) algorithms: 43230000 