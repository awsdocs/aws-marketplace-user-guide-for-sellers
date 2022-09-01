# Onboarding with AWS Marketplace Vendor Insights<a name="vendor-insights-onboarding"></a>

The following list provides you with an overview of the required process for setting up AWS Marketplace Vendor Insights\. Use these steps to help make sure that your AWS accounts are set up and work with your AWS Marketplace Vendor Insights dashboard\. 

**Note**  
You must configure the baseline resources and infrastructure in your AWS accounts so that AWS Marketplace Vendor Insights can gather information and generate security and compliance profiles for your software\-as\-a\-service \(SaaS\) products on AWS Marketplace\.



1. Identify an owner or owners for the tasks described in step 3 \(deploy the AWS CloudFormation template\), step 4 \(upload artifacts\), and step 5 \(complete self\-assessment\)\.

1. Deploy the onboarding CloudFormation stack set template on your AWS accounts\. 

   This step does the following:
   + Initiates the AWS services and resources that are required for gathering automated evidence from your software as a service \(SaaS\) hosting environment\.
   + Sets up an assessment in AWS Audit Manager to complete your self\-assessment\.

   For instructions on using the CloudFormation stack set template, see [[Deploy AWS CloudFormation StackSets](#deploy-onboarding-aws-cloudformation-stacksets.title)](#deploy-onboarding-aws-cloudformation-stacksets)\.

1. Share the compliance artifacts, such as audit reports and certifications, with AWS Marketplace\. To do this, upload the artifacts to the Amazon S3 bucket that was created by the CloudFormation stack set template on your AWS account\. For instructions on how to upload artifacts to your profile, refer to [Upload artifacts](#upload-artifacts)\.

1. Contact the [AWS Marketplace Vendor Insights support team](http://aws.amazon.com/marketplace/management/contact-us/?category=listing&details=Hello%20AWS%20Marketplace%20Operations%20Team%2C%0A%0AI%20want%20to%20add%20security%20profile%20for%20product%20id%3A%20%3CProductId%3E%0A%0AThanks&marketplace=commercial&subCategory=update)\. Enter your contact information, then choose **Submit**\. Our support team will contact you\.

1. Complete the self\-assessment in AWS Audit Manager\. For instructions on completing the self\-assessment, see [Complete the self\-assessment](#complete-self-assessment)\.

## Deploy AWS CloudFormationStackSets<a name="deploy-onboarding-aws-cloudformation-stacksets"></a>

To simplify AWS Marketplace Vendor Insights setup, we use AWS CloudFormation StackSets\. By using CloudFormation, you can model, provision, and manage AWS and third\-party resources by treating infrastructure as code\. A CloudFormation template describes all the AWS resources, such as an Amazon Elastic Compute Cloud \(Amazon EC2\) instance and an Amazon Relational Database Service \(Amazon RDS\) database instance\. CloudFormation takes care of provisioning and configuring those resources for you\.

A collection of AWS resources that are managed as a single unit is known as a *stack*\. AWS CloudFormation StackSets extends a stack for deploying and managing resources across multiple AWS accounts and AWS Regions as a single operation\. For more information about CloudFormation StackSets, see [Working with AWS CloudFormation StackSets](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/what-is-cfnstacksets.html) in the *AWS CloudFormation User Guide*\.

AWS Marketplace Vendor Insights setup requires that you use the following CloudFormation templates: 
+ **VendorInsightsPrerequisiteCFT** – Sets up the necessary administrator role and permissions to run CloudFormation StackSets in your account\.
+ **VendorInsightsOnboardingCFT ** – Sets up the required AWS services and configures the appropriate AWS Identity and Access Management \(IAM\) permissions\. These permissions allow AWS Marketplace Vendor Insights to gather data for the SaaS product running in your AWS accounts and display the data on your AWS Marketplace Vendor Insights profile\.

### Create the VendorInsightsPrerequisiteCFT stack<a name="create-vendor-insights-pre-cft-stack"></a>

By running this CloudFormation stack, you set up IAM permissions to start onboarding stack sets\. Before creating this stack, provide your AWS account ID to the AWS Marketplace team so we can grant permission for the account to access the CloudFormation template file from this Amazon S3 location\. To begin the setup, follow the steps in [Selecting a stack template](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-using-console-create-stack-template.html)\.

**To create the VendorInsightsPrerequisiteCFT stack**

1. Sign in to the AWS Management Console and open the [AWS Marketplace console](https://console.aws.amazon.com/marketplace/)\. 

1. Contact the [AWS Marketplace Vendor Insights support team](http://aws.amazon.com/marketplace/management/contact-us/?category=listing&details=Hello%20AWS%20Marketplace%20Operations%20Team%2C%0A%0AI%20want%20to%20add%20security%20profile%20for%20product%20id%3A%20%3CProductId%3E%0A%0AThanks&marketplace=commercial&subCategory=update)\. Enter your contact information, then choose **Submit**\. Our support team will contact you, upon contact provide your AWS account IDs\.

### Create the VendorInsightsOnboardingCFT stack set<a name="create-vendor-insights-onboarding-cft-stackset"></a>

By running this CloudFormation stack set, you set up the [required AWS services](#vendor-insights-onboarding-services) and configure the appropriate IAM permissions\. This allows AWS Marketplace Vendor Insights to gather data for the SaaS product running in your AWS account and display it in your AWS Marketplace Vendor Insights profile\. 

Before creating this stack set, provide your AWS account ID to the AWS Marketplace team, so we can grant permission for the account to access the CloudFormation file from this Amazon S3 location\. 

To begin the setup, follow the instructions to [create a stack set with self\-managed permissions](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-getting-started-create.html#stacksets-getting-started-create-self-managed)\. To create the VendorInsightsPrerequisiteCFT stack, contact [AWS Marketplace Vendor Insights support team](https://aws.amazon.com/marketplace/management/contact-us/?category=listing&details=Hello%20AWS%20Marketplace%20Operations%20Team%2C%0A%0AI%20want%20to%20add%20security%20profile%20for%20product%20id%3A%20%3CProductId%3E%0A%0AThanks&marketplace=commercial&subCategory=update)\. Enter your contact information, then choose **Submit**\. Our support team will contact you\.

**To create the VendorInsightsOnboardingCFT stack set**
+ Once you have the template file downloaded, enter a name for the stack set\. The value of the stack set parameters changes based on the use case\. The stack set takes the following parameters: 
  + `CreateVendorInsightsAutomatedAssessment` – This parameter sets up the AWS Audit Manager automated assessment in your AWS account\. 
  + `CreateVendorInsightsBucket` – This parameter sets up an Amazon S3 bucket to facilitate the exchange of artifacts, such as certificates between AWS Marketplace Vendor Insights and you\.
  + `CreateVendorInsightsIAMRoles` – This parameter provisions an IAM role that allows AWS Marketplace Vendor Insights to read the assessment and artifact data in your AWS account\.
  + `CreateVendorInsightsSelfAssessment` – This parameter sets up the Audit Manager self\-assessment in your AWS account\.
  + `MarketplaceManagementAccountId` – This parameter sets up an IAM trust relationship between your AWS Marketplace management account and your other AWS accounts\. This trust relationship allows resource information from the other AWS accounts to pass to AWS Marketplace Vendor Insights from the management account during the setup process\.
  + `PrimaryRegion` – This parameter sets the primary AWS Region for your SaaS deployment\. This is the Region where the S3 bucket and self\-assessment are created in your AWS account\. If your SaaS product is deployed to only one Region, that Region is the primary Region\.
  + `ProductName` – This parameter specifies the name that is added as a suffix to the AWS Audit Manager self\-assessment to help you distinguish between multiple self\-assessments that you might set up for your products\.
**Important**  
The first Region in this list must be the Region that is set in the `PrimaryRegion` parameter specified earlier in step 5\.  
You must leave the **Region Concurrency** option to the default setting of **Sequential**\. The stack set takes about five minutes per Region to complete the implementation\.

### Required AWS services and resources<a name="vendor-insights-onboarding-services"></a>

AWS Marketplace Vendor Insights requires that you set up the following AWS services and resources\. The CloudFormation VendorInsightsOnboardingCFT stack set automatically deploys to the AWS Regions that you specify in the AWS account you run the stack set in\. This process occurs automatically and you don't need to run a process to deploy to the AWS Regions you specified in your AWS account\. 
+ **AWS Audit Manager** – The stack set creates two assessments in AWS Audit Manager: 
  + A self\-assessment that contains over 140 control categories\. For each control in the self\-assessment, you provide an answer that is visible to buyers\.
  + An automated assessment that contains 30 controls and is automatically populated using AWS Config\.

  For more information about AWS Audit Manager, see the [AWS Audit Manager User Guide](https://docs.aws.amazon.com/audit-manager/latest/userguide/what-is.html)\.
+ **AWS Config** – The stack set deploys an AWS Config Conformance Pack to set up the necessary AWS Config rules\. These rules allow the Audit Manager automated assessment to gather live evidence for other AWS services deployed in that AWS account\. For more information about AWS Config features, see [AWS Config](http://aws.amazon.com/https://docs.aws.amazon.com/config/latest/developerguide/WhatIsConfig.html)\.
+ **Amazon S3** – The stack set creates the following three Amazon S3 buckets: 
  + **vendor\-insights\-stack\-set\-output\-bucket\-\{account number\}** – This bucket contains outputs from the stack set run that the AWS Marketplace Vendor Insights team uses to complete your setup and generate your AWS Marketplace Vendor Insights profile\.
  + **vendor\-insights\-audit\-reports\-bucket\-\{account number\}** – This bucket serves as a common link between your AWS account and the AWS Marketplace Vendor Insights service\. It contains artifacts such as ISO\-27001 and SOC2 certificates and reports that AWS Marketplace Vendor Insights uses as data sources\.
  + **vendor\-insights\-assessment\-reports\-bucket\-\{account number\}** – AWS Audit Manager publishes assessment reports to this Amazon S3 bucket\. For more information about publishing assessment reports, see [Assessment reports](https://docs.aws.amazon.com/audit-manager/latest/userguide/assessment-reports.html) in the *AWS Audit Manager User Guide*\.

    For more information about Amazon S3 features, see the [Amazon S3 User Guide](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)\.
+ **IAM** – The stack set provisions the following IAM roles in your account: 
  + When the `VendorInsightsPrerequisiteCFT.yaml` template is deployed, it creates the admin role **AWSVendorInsightsOnboardingStackSetsAdmin** and the run role **AWSVendorInsightsOnboardingStackSetsExecution**\. The stack set uses the admin role to deploy the required stacks into multiple AWS Regions simultaneously\. The admin role assumes the execution role to deploy the necessary parent and nested stacks as part of the AWS Marketplace Vendor Insights setup process\. For more information about self\-managed permissions, see [Grant self\-managed permissions](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-prereqs-self-managed.html) in the *AWS CloudFormation User Guide*\.
  + The **AWSVendorInsightsRole** role provides AWS Marketplace Vendor Insights with principal access in order to read information from AWS Audit Manager resources\. Then AWS Marketplace Vendor Insights displays the resources' information on your AWS Marketplace Vendor Insights profile\. For more information about principals, see [Principal](https://docs.aws.amazon.com/IAM/latest/UserGuide/intro-structure.html#intro-structure-principal) in the *AWS Identity and Access Management User Guide\. *
  + The **AWSVendorInsightsOnboardingDelegationRole** provides AWS Marketplace Vendor Insights with principal access in order to list and read objects in the **vendor\-insights\-audit\-reports\-bucket** and **vendor\-insights\-stack\-set\-output\-bucket** buckets\. This capability is necessary to complete the setup actions and generate your AWS Marketplace Vendor Insights profile\. 
  + The **AWSAuditManagerAdministratorAccess** role provides administrative access to enable or disable AWS Audit Manager, update settings, and manage assessments, controls, and frameworks\. You or your team can assume this role to complete the self\-assessment in AWS Audit Manager\.
**Note**  
Although CloudFormation StackSets support cross\-account deployments, we recommend running these stack sets individually on each AWS account that your AWS Marketplace SaaS product is running\. If your SaaS product is deployed to multiple AWS Regions within the account, all Regions should be provided to the stack set when prompted\. This helps to ensure that AWS Config and AWS Audit Manager are correctly enabled for gathering data from all Regions\. For more information about CloudFormation StackSets, see [Working with AWS CloudFormation StackSets](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/what-is-cfnstacksets.html)\.

## Upload artifacts<a name="upload-artifacts"></a>

Share compliance artifacts, such as audit reports and certifications, with AWS Marketplace\.

**To upload artifacts**

1. Sign in to the AWS Management Console and open the [AWS Marketplace console](https://console.aws.amazon.com/marketplace/)\.

1. The **VendorInsightsOnboardingCFT** stack set template sets an Amazon S3 bucket in the primary AWS Region of your AWS account with the name **vendor\-insights\-audit\-reports\-bucket\-\{account number\}**\. 

1. Upload the certification artifacts, such as ISO\-27001 and SOC2 reports, to this Amazon S3 bucket\.

AWS Marketplace Vendor Insights downloads the reports from this Amazon S3 bucket, extracts information from the reports, and presents it in the dashboard\.

**Important**  
After you upload an artifact, contact the [AWS Marketplace Vendor Insights support team](https://aws.amazon.com/marketplace/management/contact-us/?category=listing&details=Hello%20AWS%20Marketplace%20Operations%20Team%2C%0A%0AI%20want%20to%20add%20security%20profile%20for%20product%20id%3A%20%3CProductId%3E%0A%0AThanks&marketplace=commercial&subCategory=update)\. We will initiate the data extraction from the reports\.

## Complete the self\-assessment<a name="complete-self-assessment"></a>

The **VendorInsightsOnboardingCFT** stack set template sets an AWS Audit Manager assessment in the primary Region of your AWS account with the name **AWSVendorInsightsSelfAssessment**\.

This assessment contains 140 controls in total\. If you enable automated evidence gathering and share your ISO and SOC2 report, you are only required to answer 29 of the 140 controls\. You can identify these 29 controls by the control name which contains "Requires manual attestation"\.

The **VendorInsightsOnboardingCFT** stack set template provisions two IAM roles: `AWSAuditManagerAdminRole` and `AWSVendorInsightsRole`\. Then, the CloudFormation stack set template adds the roles as audit owners for the automated assessment and the self\-assessment in AWS Audit Manager\. AWS Marketplace Vendor Insights uses `AWSVendorInsightsRole` to pull the data from the assessment\. You can use `AWSAuditManagerAdminRole` to view and add responses to controls\.

**To complete the self\-assessment**

1. Sign in to the AWS Management Console and open the [AWS Marketplace console](https://console.aws.amazon.com/marketplace/)\.

1. From the drop\-down menu on the top right, choose **Switch** role\.

1. On the **Role switch** page, enter your IAM account ID and select **AWSAuditManagerAdminRole** as the role\. Choose **Switch Role**\.
**Note**  
If you encounter a permissions issue when switching to this role, add the IAM permission for your IAM user account to assume this role\.  
In **Control status summary**, for **Total controls**, the value should be **140**\.  
In **Control status summary**, a value of **0** for **Total controls** indicates that only audit owners are allowed to view and add responses to controls\. 

1. To record your response for a control, do the following: 

   1. Select the control, then navigate to the **Comments** tab on the **Control** page\.

   1. Enter your response to the **Comments** field\. Choose **Submit comments**\.

   1. When you enter a response in the comments field, begin with a **Yes** or **No** response before you add additional details\. By using this exact response approach, our system can parse your response correctly and display the correct compliance status in the dashboard\.