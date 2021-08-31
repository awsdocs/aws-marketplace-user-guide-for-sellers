# Best practices for building AMIs<a name="best-practices-for-building-your-amis"></a>

This topic provides some best practices and references to help you build Amazon Machine Images \(AMIs\) for use with AWS Marketplace\. AMIs built and submitted to AWS Marketplace must adhere to all AWS Marketplace product policies\.

## Verifying your AMI<a name="self-service-scanning"></a>

To help verify your AMI before submitting it as a new product or version, you can use self\-service scanning\.

From the AWS Marketplace Management Portal, choose **Amazon Machine Image** from the **Assets** menu\. Click **Add AMI** to start the scanning process\. You can see the scan status of AMIs by returning to this page\.

**Note**  
To learn about giving AWS Marketplace access to your AMI, see [Giving AWS Marketplace access to your AMI](ami-single-ami-products.md#single-ami-marketplace-ami-access)\.

## Securing resell rights<a name="rights"></a>

You are responsible for securing resell rights for non\-free Linux distributions, with the exception of AWS\-provided Amazon Linux, RHEL, SUSE, and Windows AMIs\.

## Building an AMI<a name="building-an-ami"></a>

Use the following guidelines for building AMIs:
+ Ensure that your AMI meets all AWS Marketplace policies, including disabling root login\. 
+ Create your AMI in the US East \(N\. Virginia\) Region\. 
+ Create products from existing, well\-maintained AMIs backed by Amazon Elastic Block Store \(Amazon EBS\) with a clearly defined lifecycle provided by trusted, reputable sources such as AWS Marketplace\. 
+ Build AMIs using the most up\-to\-date operating systems, packages, and software\. 
+ Ensure that all AMIs must start with a public AMI that uses hardware virtual machine \(HVM\) virtualization and 64\-bit architecture\. 
+ Develop a repeatable process for building, updating, and republishing AMIs\. 
+ Use a consistent operating system \(OS\) user name across all versions and products\. We recommend **ec2\-user**\.
+ Configure a running instance from your final AMI to the end\-user experience you want, and test all installation methods, features, and performance *before* submission to AWS Marketplace\. 
+ Check port settings as follows:
  + Linux\-based AMIs – Ensure that a valid SSH port is open\. The default SSH port is 22\.
  + Windows\-based AMIs – Ensure that an RDP port is open\. The default RDP port is 3389\. Also, the WinRM port \(5985 by default\) must be open to 10\.0\.0\.0/16\. 

For more information about creating an AMI, see the following resources:

 [Creating Your Own AMI](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html#creating-an-ami) in the *Amazon EC2 User Guide for Linux Instances*

 [Creating a Custom Windows AMI](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/Creating_EBSbacked_WinAMI.html) in the *Amazon EC2 User Guide for Windows Instances* 

 [How do I create an Amazon Machine Image \(AMI\) from an EBS\-backed Windows instance?](https://aws.amazon.com/premiumsupport/knowledge-center/create-ami-ebs-backed-windows/) 

 [Amazon Linux AMI](https://aws.amazon.com/amazon-linux-ami/) 

 [Amazon EC2 Instance Types](http://aws.amazon.com/ec2/instance-types/) and [Instance Types](http://docs.amazonwebservices.com/AWSEC2/latest/UserGuide/instance-types.html?r=2153) 

## Verifying your software is running on your AWS Marketplace AMI<a name="verifying-ami-runtime"></a>

You may wish to have your software verify at runtime that it is running on an Amazon EC2 instance created from your AMI product\.

To verify the Amazon EC2 instance is created from your AMI product, use the instance metadata service built into Amazon EC2\. The following steps take you through this validation\. For more information about using the metadata service, see [Instance metadata and user data](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html) in the *Amazon Elastic Compute Cloud User Guide*\.

1. *Obtain the instance identity document*

   Each running instance has an identity document accessible from the instance that provides data about the instance itself\. The following example shows using curl from the instance to retrieve the instance identity document\.

   ```
   curl http://169.254.169.254/latest/dynamic/instance-identity/document
   {
      "accountId" : "0123456789",
      "architecture" : "x86_64",
      "availabilityZone" : "us-east-1e",
      "billingProducts" : null,
      "devpayProductCodes" : null,
      "marketplaceProductCodes" : [ "0vg0000000000000000000000" ],
      "imageId" : "ami-0123456789abcdef1",
      "instanceId" : "i-0123456789abcdef0",
      "instanceType" : "t2.medium",
      "kernelId" : null,
      "pendingTime" : "2020-02-25T20:23:14Z",
      "privateIp" : "10.0.0.2",
      "ramdiskId" : null,
      "region" : "us-east-1",
      "version" : "2017-09-30"
   }
   ```

1. *Verify the instance identity document*

   You can verify that the instance identity is correct using the signature\. For details about this process, see [ Instance identity documents](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-identity-documents.html) in the *Amazon Elastic Compute Cloud User guide*\.

1. *Verify the product code*

   When you initially submit your AMI product for publishing, your product is assigned a [product code](https://docs.aws.amazon.com/marketplace/latest/userguide/ami-getting-started.html#ami-product-codes) by AWS Marketplace\. You can verify the product code by checking the `marketplaceProductCodes` field in the instance identity document, or you can get it directly from the metadata service:

   ```
   curl http://169.254.169.254/latest/meta-data/product-codes
   0vg0000000000000000000000
   ```

   If the product code matches the one for your AMI product, then the instance was created from your product\.

You may also wish to verify other information from the instance identity document, such as the `instanceId` and the instance `privateIp`\.

## Securing an AMI<a name="securing-an-ami"></a>

We recommend the following guidelines for creating secure AMIs:
+ Architect your AMI to deploy as a minimum installation to reduce the attack surface\. Disable or remove unnecessary services and programs\. 
+ Whenever possible, use end\-to\-end encryption for network traffic\. For example, use Secure Sockets Layer \(SSL\) to secure HTTP sessions between you and your buyers\. Ensure that your service uses only valid and up\-to\-date certificates\. 
+ When adding a new version to your AMI product, configure security groups to control inbound traffic access to your instance\. Ensure that your security groups are configured to allow access only to the minimum set of ports required to provide necessary functionality for your services\. Allow administrative access only to the minimum set of ports and source IP address ranges necessary\. For more information about how to add a new version to your AMI product, see [Adding a new version](ami-single-ami-products.md#single-ami-adding-version)\.
+ Consider performing a penetration test against your AWS computing environment at regular intervals, or consider employing a third party to conduct such tests on your behalf\. For more information, including a penetration testing request form, see [AWS Penetration Testing](http://aws.amazon.com/security/penetration-testing/)\. 
+ Be aware of the top 10 vulnerabilities for web applications, and build your applications accordingly\. To learn more, see [Open Web Application Security Project \(OWASP\) \- Top 10 Web Application Security Risks](https://owasp.org/www-project-top-ten/)\. When new internet vulnerabilities are discovered, promptly update any web applications that ship in your AMI\. Examples of resources that include this information are [SecurityFocus](http://www.securityfocus.com/vulnerabilities) and the [NIST National Vulnerability Database](http://nvd.nist.gov/)\.

For more information related to security, see the following resources:
+ [Guidelines for Shared Linux AMIs](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/building-shared-amis.html) in the *Amazon EC2 User Guide for Linux Instances*
+  [AWS Cloud Security](http://aws.amazon.com/security/) 
+  [The Center for Internet Security \(CIS\): Security Benchmarks](http://benchmarks.cisecurity.org/downloads/benchmarks/) 
+  [The Open Web Application Security Project \(OWASP\): Secure Coding Practices \- Quick Reference Guide](https://www.owasp.org/www-project-secure-coding-practices-quick-reference-guide/migrated_content) 
+  [OWASP Top 10 Web Application Security Risks](https://owasp.org/www-project-top-ten/) 
+  [SANS \(SysAdmin, Audit, Networking, and Security\) Common Weakness Enumeration \(CWE\) Top 25 Most Dangerous Software Errors](http://www.sans.org/top25-software-errors/) 
+  [Security Focus](http://www.securityfocus.com/vulnerabilities) 
+  [NIST National Vulnerability Database](http://nvd.nist.gov/) 