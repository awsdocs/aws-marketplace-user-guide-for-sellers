# AMI\-Based Products<a name="AmiBasedProducts"></a>

 AMI is the acronym for [Amazon Machine Image](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)\. 

## Product ID and Product Codes<a name="product-id-and-product-codes"></a>

 Each product in AWS Marketplace is assigned a unique product ID which is used to track and identify the product in our catalog, and is included in seller reports\. A unique product code is assigned to all AMIs submitted to AWS Marketplace\. The unique product ID is used to distinguish your product in AWS Marketplace, provide access to users who purchase your product, as well as for the customer billing process\. 

 Sellers can obtain the Product Code while developing their software so it can be used for extra security, such as validating Product Code at product start\. API calls to an AMIs Product Code will not be possible until the product has been published into a limited state for testing\. 

 These Product Codes automatically propagate as customers work with the software\. For example, a customer subscribes and launches an AMI, configures it and produces a new AMI\. The new AMI will still contain the original Product Code so correct billing and permissions will still be in place\. More information is available at [Amazon Elastic Compute Cloud](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html) \(Amazon EC2\) instance metadata and user data\. 

## Multiple Versions<a name="multiple-versions"></a>

 AWS Marketplace product listings allow for multiple versions of the product to be available to subscribers as part of their subscription as separate AMIs\. The seller can request any number of versions to be available on a product listing\. Note that once a subscriber has access to an AMI, they will always have launch permissions on the AMI regardless of the visibility or status of that version on the listing\. 

 For example, product “Data Cleaner” might have versions “1\.0\.0”, “1\.2\.5” and “2\.0\.1”, all of which can be available to subscribers\. If you request removal of version 1\.0\.0, no new customers can subscribe to that version, but exisiting customer can still access version 1\.0\.0\. 

## Removing Products from AWS Marketplace<a name="removing-products-from-aws-marketplace"></a>

 Once your product is published, you can sunset \(remove\) the product from AWS Marketplace\. To remove a product, you identify the product, and submit a request to remove, along with a reason for removeing and a contact email for you\. You can also provide a replacement product ID if you are replacing your current product with a new one\. Once you request to remove your product, new customers will no longer be able to subscribe\. You are required to support any existing customers for a minimum of 90 days\. Requests for a product to be removed from AWS Marketplace will be processed with the following conditions: 
+  The product is removed from AWS Marketplace search, browse and other discovery tools\. Any “Subscribe” button or functionality is disabled, and messaging on the page clearly indicates the product is no longer available\. Note that the product detail page is still accessible using the URL and may be indexed in public search engines\. 
+  A reason for takedown must be specified \(i\.e\. end of support, end of product updates, replacement product\)\. The [Terms and Conditions for AWS Marketplace Sellers](https://aws.amazon.com/marketplace/management/terms?) contains the requirements for continuing support for these removed products\. 
+  Current subscribers will be messaged by AWS Marketplace informing of the product takedown, reasons, and provide seller contact information\. 
+  Current subscribed customers WILL retain access to the software until they cancel their subscription and will not be impacted in any way\. 

 To remove a product created using the Self\-Service Listing tool: 

1.  Open the AWS Marketplace management portal \(AMMP\) and choose the **Listings** tab\. 

1.  On your products listing page under current listings, locate the product you want to remove\. Under the **Actions** column for the listing, in the **Select action** menu, choose **Remove listing**\. An **Remove Product Listing** page will appear\. 

1.  On the **Remove Product Listing** page, next to **Request Reason**, type the reason you are requesting the product be removeed\. 

1.  Next to **Contact Email**, provide the email AWS Marketplace can use to contact you if there are any questions\. **Note**: You can also provide a replacement product ID, but the field is not a required field you must complete\. 

1.  Review the information for accuracy, and then choose **Submit Sunset Request**\. 

 Once you have submitted the request, you will be taken to a **What’s next** informational page\. The AWS Marketplace Seller Operations team will review and process your request\. You can check the status of your submission by viewing **Open Requests** from your **Self Service Listing** page\. If you have any questions or concerns, contact the **AWS Marketplace Seller Operations** \(aws\-marketplace\-seller\-ops@amazon\.com\) team\. 

 After your product is removed, the product will show in your **Request History** list, and in the **Current Listings** list\. In **Current Listings**, the only action available to you will be to download the spreadsheet for the listing\. You will no longer be able to edit or submit another sunset request\. 

 For listings not created with the Self\-Service Listings tool, you edit and upload the Product Load Form for the product\. Links to upload updated Product Load Forms are under the File Uploads tab\. For questions on this process, contact the **AWS Marketplace Seller Operations** \(aws\-marketplace\-seller\-ops@amazon\.com\) team\. 

## Best Practices for Building Your AMIs<a name="best-practices-for-building-your-amis"></a>

 All AMIs built and submitted to AWS Marketplace must adhere to all product policies\. To share your AMI and verify that it meets all AWS Marketplace, utilize the self\-service [AMI scanning tool](https://aws.amazon.com/marketplace/management/manage-products/#/manage-amis.unshared)\. Additionally, here are some best practices and references to help you in building your AMI\. 

## Rights<a name="rights"></a>

 You are responsible for securing resell rights for non\-free Linux distributions, with the exception of AWS\-provided Amazon Linux, RHEL, SUSE and Windows AMIs\. 

## Building an AMI<a name="building-an-ami"></a>
+  Ensure your AMI meets all AWS Marketplace policies, including disabling root login\. 
+  Create your AMI in us\-east\-1 \(N\. Virginia\)\. 
+  Products should be created from existing, well\-maintained EBS\-backed AMIs with a clearly defined life\-cycle provided by trusted, reputable sources such as AWS Marketplace\. 
+  Build AMIs using the most up\-to\-date operating systems, packages, and software\. 
+  All AMIs must start with a public AMI that uses Hardware Virtual Machine \([HVM](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/virtualization_types.html)\) virtualization and 64\-bit architecture\. 
+  Develop a repeatable process for building, updating, and republishing AMIs\. 
+  Use a consistent OS username across all versions and products\. We recommend **ec2\-user** 
+  Configure a running instance from your final AMI to the end\-user experience you want, and test all installation, features, and performance **prior** to submission to AWS Marketplace\. 
+  Ensure for **Linux** based AMIs that a valid SSH port is open \(default is 22\) and for **Windows** based AMIs that an RDP port is open \(default is 3389\)\. WINRM \(port 5985\) must be open to 10\.0\.0\.0/16\. 

 **Resources** 

 [Creating Your Own AMIs](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html#creating-an-ami) 

 [Creating your Own Windows\-based AMIs](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/Creating_EBSbacked_WinAMI.html) 

 [Using Amazon EBS\-Backed AMIs and Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/creating-an-ami-instance-store.html) 

 [Creating an AMI from an EBS\-backed Windows Instance](https://aws.amazon.com/premiumsupport/knowledge-center/create-ami-ebs-backed-windows/) 

 [Amazon Linux](https://aws.amazon.com/amazon-linux-ami/) 

 [Linux Forums](http://www.linuxforums.org/) 

 [EC2 Instance Types](http://aws.amazon.com/ec2/instance-types/) and [Instance Families and Types](http://docs.amazonwebservices.com/AWSEC2/latest/UserGuide/instance-types.html?r=2153) 

## Securing an AMI<a name="securing-an-ami"></a>
+  Architect your AMI to deploy as a minimum installation to reduce the attack surface\. You should disable or remove unnecessary services and programs\. 
+  Whenever possible, use end\-to\-end encryption for network traffic\. For example, use Secure Socket Layer \(SSL\) to secure HTTP sessions between you and your customers\. Ensure that your service uses only valid and up\-to\-date certificates\. 
+  Use security groups to control inbound traffic access to your instance\. Ensure that your security groups are configured to allow access only to the minimum set of ports required to provide necessary functionality for your services\. In addition, allow administrative access only to the minimum set of ports and source IP address ranges necessary\. 
+  Consider performing a penetration test against your AWS computing environment at regular intervals; or, consider employing a third party to conduct such tests on your behalf\. To learn more, see [AWS Penetration Testing](http://aws.amazon.com/security/penetration-testing/) \(includes a penetration testing request form\)\. 
+  Be aware of the top 10 vulnerabilities for web applications and build your applications accordingly\. To learn more, visit [Open Web Application Security Project \(OWASP\) \- Top 10 Web Application Security Risks](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project)\. When new Internet vulnerabilities are discovered, promptly update any web applications that ship in your AMI\. Examples of resources that include this information are [SecurityFocus](http://www.securityfocus.com/vulnerabilities) and the [NIST National Vulnerability Database](http://nvd.nist.gov/)\., 

 **Resources** 
+  [AWS Security Center](http://aws.amazon.com/security/) 
+  [AWS Security Best Practices](http://media.amazonwebservices.com/AWS_Security_Best_Practices.pdf) 
+  [AWS Overview of Security Processes](http://media.amazonwebservices.com/pdf/AWS_Security_Whitepaper.pdf) 
+  [The Center for Internet Security \(CIS\): Security Benchmarks](http://benchmarks.cisecurity.org/downloads/benchmarks/) 
+  [The Open Web Application Security Project \(OWASP\): Secure Coding Practices Quick Reference Guide](https://www.owasp.org/index.php/OWASP_Secure_Coding_Practices_-_Quick_Reference_Guide) 
+  [OWASP Top 10 Web Application Security Risks](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project) 
+  [SANS \(SysAdmin, Audit, Networking, and Security\) Common Weakness Enumeration \(CWE\) Top 25 Most Dangerous Software Errors](http://www.sans.org/top25-software-errors/) 
+  [Security Focus](http://www.securityfocus.com/vulnerabilities) 
+  [NIST National Vulnerability Database](http://nvd.nist.gov/) 

## Product and AMI Policies<a name="product-and-ami-policies"></a>

 These policies exist to ensure that the products and offerings on AWS Marketplace contribute to a safe, secure and trusted source for customers\. 

 **All** products and metadata will be reviewed to ensure they meet or exceed current AWS Marketplace policies\. Product policies are always being reviewed and adjusted to meet current security guidelines and it is possible for products to no longer be compliant with current policy\. With the introduction of AMI Self Service Scanning, please utilize the [self\-service AMI scanning tool](https://aws.amazon.com/marketplace/management/manage-products/#/manage-amis.unshared) which will help to ensure the AMI meets AWS Marketplace policies\. 

### Security<a name="security"></a>

1.  AMIs **MUST NOT** contain any known vulnerabilities, malware or viruses\. 

1.  AMIs **MUST NOT** contain default passwords, auth keys, key pairs, security keys or other credentials for any reason\. All instance authentication must use key pair access rather than password based auth, even if the password is generated, reset or defined by the user at launch\. 

1.  AMIs **MUST NOT** request or use access /secret keys from users to access AWS resources\. 

1.  AWS Marketplace AMIs must not allow password authentication\. Disable password authentication via your sshd\_config file by setting the PasswordAuthentication to NO\. 

### Accessibility<a name="accessibility"></a>

1.  Linux\-based AMIs **MUST** [lock/disable root login](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/building-shared-amis.html) and allow only sudo access through a user account \(not “root”\)\. Sudo allows you to control which users are allowed to perform root functions and logs the activity so that there is an audit trail\. 

1.  AMIs **MUST** allow OS\-level administration capabilities to allow for compliance requirements, vulnerability updates and log file access\. For Linux\-based AMIs this is through SSH, and for Windows\-based AMIs this is normally through RDP\. 

1.  Linux\-based AMIs **MUST NOT** have blank or null root passwords\. 

1.  AMIs **MUST NOT** contain Authorized Passwords or Authorized Keys 

1.  AMIs **MUST NOT** use default passwords for user interface access\. It is recommended to use a randomization process such as using the instance\_id from the [AWS EC2 Metadata Service](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AESDG-chapter-instancedata.html)\. 

1.  Windows\-based AMIs **MUST** 

   1.  Use the most recent version of [Ec2ConfigService](http://aws.amazon.com/developertools/5562082477397515) 

   1.  ENABLE “Ec2SetPassword”, “Ec2WindowsActivate” and “Ec2HandleUserData” 

   1.  Remove Guest Accounts or Remote Desktop Users \(none are allowed\) 

1.  The seller **MUST NOT** maintain access to the customer’s running instances\. The customer has to explicitly enable any outside access, and any accessibility built into the AMI must be off by default\. 

### Customer Information<a name="customer-information"></a>

1.  All non\-BYOL AMI products **MUST NOT** require customer registration with the seller, or require customer information to use the product \(for example email address required\)\. 

1.  Software **MUST NOT** require, collect or export customer data without the customer’s knowledge and express consent\. 

1.  AWS **WILL NOT** share private or personally identifying customer information \(name, email, contact info, etc\.\) with any seller or outside party without the consent of the customer\. 

### Product Usage<a name="product-usage"></a>

1.  Products **MUST NOT** restrict access to the product or product functionality by time or other restrictions; "Trial", "Beta", or “Evaluation” products are not supported\. 

1.  All AMIs **MUST** meet be compatible with either the AWS 1\-click fulfillment experience or the [Clusters and AWS Resources](https://aws.amazon.com/mp/clusters/) feature\. For 1\-click, the AMI cannot require customer or user data at instance creation in order to function correctly\. To learn more about multi\-instance or AWS CloudFormation launches see the additional guidelines [here](https://s3.amazonaws.com/awsmp-loadforms/awsmp-ami-delivery-using-cloudformation.pdf)\. 

1.  Each AMI **MUST** contain everything a subscriber needs to use the software, including any client applications\. 

1.  For Free or Paid products, the fulfillment process **MUST NOT** require the customer to leave the AWS Marketplace\. 

1.  AMIs **MUST NOT** require a subscription API or launches from outside the AWS Marketplace\. 

1.  Products **MUST NOT** use copyrighted material you do not have the rights to use\. 

1.  Product software and metadata **MUST NOT** contain language that redirects users to other cloud platforms, additional products or upsell services not available on AWS Marketplace\. 

### Architecture<a name="architecture"></a>

1.  Source AMIs for AWS Marketplace **MUST** be provided in the us\-east\-1 region\. 

1.  AMIs **MUST** use Hardware Virtual Machine \([HVM](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/virtualization_types.html)\) virtualization 

1.  AMIs **MUST** use 64\-bit architecture 

1.  AMIs **MUST** be EBS\-backed AMIs; we do not currently support S3\-backed AMIs\. 

1.  AMIs **MUST** use a supported file system; Ext2, Ext3, Ext4, Xfs, Vfat, Lvm, and NTFS\. Encrypted file systems are not supported\. These are necessary in order to pass AMI Self Service Scanning\. 

1.  FreeBSD products **MUST** be built from Linux\-based OS\. 

1.  AMIs **MUST** be built such that they can run in all regions and is region agnostic\. AMIs built differently for regions are not allowed\. 

### AMI File Upload<a name="amis-file-upload"></a>

 Self\-service AMI scanning is available within the AWS Marketplace Management Portal\. With this feature, you can initiate scans of your AMIs and receive scanning results quickly – typically in less than an hour – with clear feedback in a single location\. See AMI Self Service Scanning for information on this process\. 

 To upload a new product load form, click on the File Upload tab at the top of the management portal\. 

 From there you will be able to download the most recent product load template\. We STRONGLY RECCOMEND checking that the form you have is the most recent as it will be consistently updated with more instance types and regions as they become available\. This will significantly increase the ease of loading the page\. 

## AWS Marketplace Listing Checklist<a name="aws-marketplace-listing-checklist"></a>

 **Product Usage** 
+  Production\-ready 
+  Does not restrict product usage by time or any other measurements 
+  Compatible with 1\-click fulfillment experience 
+  Everything required to utilize the product is contained within the software including client applications 
+  Default user utilizes a randomized password and/or creation of initial user requires verification that the subscriber is authorized to use the instance using a value unique to the instance such as instance ID 

 **For Free or Paid products:** 
+  No additional license is required to use the product 
+ Subscriber does not have to provide personally identifiable information \(e\.g\. email address\) to use the product **AMI Preparation**
+  Utilizes hardware virtual machine \(HVM\) virtualization and 64\-bit architecture 
+  Does not contain any known vulnerabilities, malware or viruses 
+  Subscribers have OS\-level administration access to the AMI 
+  Run your AMI through AMI Self Service Scanning 

 **For Windows AMIs:** 
+  Utilizes the most recent version of Ec2ConfigService 
+  Ec2SetPassword, Ec2WindowsActiviate and Ec2HandleUserData are enabled 
+  No Guest Accounts or Remote Desktop Users are present 

 **For Linux AMIs:** 
+  Root login is locked/disabled 
+  No authorized keys, default passwords or other credentials are included 

**Load Form or Self\-service Listings Preparation**
+  All required fields are completed 
+  All values are within specified character limits 
+  All URLs load without error 
+  Product image is at least 110px wide and between a 1:1 and 2:1 ratio 
+  Pricing is specified for all enabled instance types \(for hourly, hourly\_monthly and hourly\_annual pricing models\) 
+  Monthly pricing is specified \(for hourly\_monthly and monthly pricing models\) 