# AMI and container product usage instructions<a name="ami-container-product-usage-instructions"></a>

When creating usage instructions for your product, you must include the following information:
+ Location of all sensitive information saved by customers
+ Explain all data encryption configuration
+ Step\-by\-step instructions for rotating programmatic system credentials and cryptographic keys\. The [AMI\-based product requirements](product-and-ami-policies.md) explain the basic requirements for listings that use credentials and cryptographic keys\.
+ Provide detailed instructions on how the user interacts with your application to decrypt necessary data if your application makes use of any encryption techniques
+ Step\-by\-step instructions for how to assess and monitor the health and proper function of the application\. For example:
  + Navigate to your [Amazon EC2 console](https://us-east-1.signin.aws.amazon.com/oauth?response_type=code&client_id=arn%3Aaws%3Aiam%3A%3A015428540659%3Auser%2Fec2&redirect_uri=https%3A%2F%2Fus-east-1.console.aws.amazon.com%2Fec2%2Fv2%2Fhome%3Fregion%3Dus-east-1%26state%3DhashArgs%2523Home%253A%26isauthcode%3Dtrue&forceMobileLayout=0&forceMobileApp=0&code_challenge=aRqwDZ0gdWGXfWQgSpY_ge8vSRw2poGnBZ_8qsU5fiA&code_challenge_method=SHA-256) and verify that you're in the correct region\.
  + Choose **Instance** and select your launched instance\.
  + Select the server to display your metadata page and choose the **Status checks** tab at the bottom of the page to review if your status checks passed or failed\.

## <a name="naming-and-describing-your-product"></a>

### Writing the release notes<a name="writing-the-release-notes"></a>

Each time you update a product, you must provide a description of the changes in the release notes\. The release notes should contain specific information to help the user decide whether to install the update\. Use clear labels for the update, such as "Critical" for a security update or "Important" or "Optional" for other types of updates\.

### Writing the usage instructions<a name="writing-the-usage-instructions"></a>

Provide usage instructions that help ensure that the buyer can successfully configure and run the software\. The usage instructions you provide are shown during the configuration process\.

To write effective usage instructions, follow these guidelines:
+ Write them with a new or moderately technical audience\.
+ Don't assume that the user has prior experience with or extensive knowledge of the product, computer operating systems, engineering, or IT operations\.
+ Take the buyer from launching to using the product, including any configuration or special steps to get the application running\.

 Example usage instructions: 

1. Launch the product via 1\-Click\.

1. Use a web browser to access the application at https://<EC2\_Instance\_Public\_DNS>/index\.html\.

1. Sign in using the following credentials:
   + Username: user
   + Password: the instance\_id of the instance

### Writing the upgrade instructions<a name="writing-upgrade-instructions"></a>

Provide details on how buyer can upgrade from an earlier version of the product\. Include information on how to preserve data and settings when creating another instance\. If there is no upgrade path, edit this field to specifically mention that\. 

Example upgrade instructions:

1. Do \*\*\*\*, and then \*\*\*\*\.

1. Check that all plugins used by your project are compatible with version \*\.\*, by doing \*\*\*\. If they aren't compatible, do \*\*\*\.

1. Make a backup of your data, by doing \*\*\*\.

## CloudFormation delivery<a name="ami-cloudformation-delivery"></a>

When using CloudFormation delivery, you must also include the following:
+ A purpose for each AWS Identity and Access Management \(IAM\) role and IAM policy created by the AWS CloudFormation template
+ A purpose and location of each key created by the AWS CloudFormation template
+ Network configuration details in deployments involving more than a single element
+ A detailed guide on how your applications are launched and how they're configured to communicate if the deployment includes multiple AWS resources
+ A pricing breakdown that includes the cost of running AWS resources added above the standard limits\. Provide prescriptive guidance on managing AWS service limits\.
+ All data encryption configuration\. For example: Amazon S3 server\-side encryption, Amazon Elastic Block Store \(Amazon EBS\) encryption, Linux Unified Key Setup \(LUKS\), etc\.\)

## Monitoring and assessing application functions<a name="ami-monitoring-applications"></a>

**To monitor and assess application functions**

1. Navigate to your [Amazon EC2 console](https://us-east-1.console.aws.amazon.com/ec2/v2/home?region=us-east-1#Home:) and verify that you're in the correct region\.

1. Choose **Instances** and select your launched instance\. 

1. Select the server to display your metadata page and choose the **Status checks** tab at the bottom of the page to review if your status checks passed or failed\.

**Note**  
If any of the data stores are proprietary, provide step\-by\-step instructions for configuration, backup, and recovery\.

## Rotating programmatic system credentials and cryptographic keys<a name="rotating-credentials"></a>

The [AMI\-based product requirements](product-and-ami-policies.md) explain the basic requirements for listings that use credentials and cryptographic keys\.

**Include the following for rotating programmatic system credentials and cryptographic keys:**
+ Prescriptive guidance on managing AWS service quotas\. For more information see the [AWS General Reference Guide](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\.
+ A pricing breakdown including the cost of running AWS resources added above the standard quota\. This can be included in your product usage instructions or linked to [documentation](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html) containing detailed information about managing and requesting increased service quotas\.