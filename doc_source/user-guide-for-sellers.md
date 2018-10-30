# Getting Started as a Seller<a name="user-guide-for-sellers"></a>

 If you are interested in selling your software on AWS Marketplace, review the requirements, and then follow the steps to register as a seller\. There are different registration requirements based on where you reside and what type of products you want to list\. To register as a seller on AWS Marketplace, you can use an existing AWS account or create a new account\. All AWS Marketplace interactions will be tied to the AWS account you choose\. 

## Seller Requirements for Publishing Free Products on AWS Marketplace<a name="seller-requirements-for-publishing-free-products"></a>
+  Sell publicly available, full\-feature production\-ready software \(not a beta product\)\. 
+  Have a defined customer support process and support organization\. 
+  Provide a means to keep software regularly updated and free of vulnerabilities\. 
+  Follow best practices and guidelines when marketing your product on AWS Marketplace\. 
+  Be an AWS customer in good standing and meet the requirements set forth in the terms and conditions for AWS Marketplace sellers\. 

## Additional Seller Requirements for Publishing Paid or BYOL Products on AWS Marketplace<a name="additional-seller-requirements-for-paid-products"></a>
+  Be a permanent US or European Union \(EU\) resident or citizen, or a business entity organized or incorporated in the United States or member state of the EU\. 
+  Tax and bank account information are required\. For US based entities, a W\-9 and banking account from a US based bank are required\. 
+  European Union state members are required to provide a W\-8, Value Added Tax \(VAT\) number, and US bank account\. If you do not have a US bank account, you can register for a virtual U\.S\. bank account from [Hyperwallet](https://wssellers.hyperwallet.com/)\. 

 To sell into the AWS GovCloud \(US\) Region, sellers must have an [AWS GovCloud \(US\) account](https://aws.amazon.com/govcloud-us/getting-started/)\. For details on ITAR requirements, refer to the [AWS GovCloud \(US\) User Guide](http://docs.aws.amazon.com/govcloud-us/latest/UserGuide/govcloud-us-ug.pdf)\. 


 Contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team with any questions on AWS Marketplace seller requirements or the registration process\. 

## AWS Marketplace Management Portal \(AMMP\)<a name="management-portal"></a>

 The [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour) is the tool you use to register as an AWS Marketplace seller, and then to manage the products you list on AWS Marketplace\. You can: 
+  Register as an AWS Marketplace Management Portal seller\. 
+  Use the Self\-Service Listings interface to submit new, and update existing products\. 
+  Monitor the status of your requests\. 
+  Upload files needed to create and manage your new listings\. 
+  Manage your listing into incremental channel revenue by taking advantage of the go\-to\-market activities\. 
+  Measure the results of your marketing efforts within hours of launch, including the usage and revenue driven by your campaigns\. 
+  Customer service representatives can retrieve customer data in real\-time\. 
+  Access AMI Self\-Sharing to scan your AMI’s for vulnerabilities\. 


 All registered sellers can access the AMMP using their AWS credentials for the account used to list their products \(the Seller of Record\)\. If you need help determining the specific account that is the Seller of Record for your products, contact the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 

 AWS Marketplace **STRONGLY** recommends using IAM roles to sign in to the AMMP rather than using your root account credentials\. See [Create IAM Users](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_identity-management.html#intro-identity-users) for details\. 

 To allow people in your company to sign in to the AMMP, you must create an IAM user for each person you want to have access and define access permissions to the AMMP\. It is also recommended to create a *root* or account owner IAM to use for access\. An IAM user will need to following permission to have full access to the Management Portal\. 

```
        {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Stmt1452812431000",
            "Effect": "Allow",
            "Action": [
            "aws-marketplace-management:*",
            "ec2:DescribeImages",
            "ec2:DescribeSnapshots",
            "ec2:ModifyImageAttribute",
            "ec2:ModifySnapshotAttribute"
            ],
            "Resource": [
            "*"
            ]
            }
            ]
        }
```

 The AMMP is always evolving and we welcome any and all feedback on your experience using the AWS Marketplace Management Portal\. Send feedback to ammp\-feedback@amazon\.com\. 