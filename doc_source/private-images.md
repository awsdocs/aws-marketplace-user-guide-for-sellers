# Private images<a name="private-images"></a>

You can use private image builds to let buyers purchase your installable software products through AWS Marketplace, and then install those products on a gold image or AMI they choose from the images available to their AWS account\. A *gold image* is a buyer\-provided server image that includes a base operating system with modifications applied to help ensure the software adheres to the buyer’s IT standards\. Gold images allow buyers to better meet their internal security, compliance, and management requirements\. 

This page describes how to use the [AWS Marketplace Management Portal](https://aws.amazon.com/marketplace/management/tour/) \(AMMP\) to upload your software binaries and/or scripts and create an installable package group for each OS your software will run on\. AWS Marketplace does a test build by installing the package group on a base operating system \(OS\) you specify and scans the resulting image for certain known vulnerabilities\. After the image build and scan completes, you can use the AMMP to submit your product\. 

The following shows the private image build flow\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/marketplace/latest/userguide/images/private-image-build-image01.png) 

When a buyer wants to fulfill your software product but use their gold image, they specify build parameters and use the AWS Marketplace Private Image Build Service to install your product on an image they choose to create a new private image that is available to their AWS account only\. They can then launch the AMI from the private image configuration panes or within Amazon EC2\. 

## Package group requirements<a name="package-group-requirements"></a>

 You can submit your package group for use on either AWS Marketplace base Linux AMIs or AWS Marketplace base Windows Server AMIs\. 

 When you select the OS platform for your product, you will have the option to select multiple OSes and OS versions on which your package group will run\. Windows Server packages will not run on Linux OSes and vice versa, so if you want your product to support private images for both OS platforms, you will need to define at least two package groups\. When you define your package group, you upload the installation packages or scripts and AMMP will build and scan a test image for each OS you choose\. 

 For your package group to successfully complete the build and scan process, you must adhere to these guidelines: 
+  The package group must have one of the packages or scripts marked as the installer\. For example, the installer may be a batch file or script that orchestrates the installation of the other packages and provides the required parameters for an unattended installation\. 
+  For Windows Server\-based packages, the supported installer types have \.msi, \.ps1, \.bat, and \.exe extensions\. 
+  For Linux/UNIX \(or any POSIX\-compliant\) systems, the supported installer types have \.exe, \.rpm, \.deb, \.sh, and \.run extensions\. 
+  The entire installation process must be unattended\. It cannot require any interactive input, and all parameters or switches must be included in the installer\. 
+  The packages must install without downloading patches or configuration files \(be complete\) from another website\. 
+  The installer/installation script must be synchronous\. For example, the script must not exit until the package\(s\) are completely installed\. 
+  The installer must exit with exit status 0 when the installation is successful\. Any value other than 0 is used for unsuccessful installations\. 
+  The installer cannot require a reboot during the installation\. A reboot would kill the agent that tracks the test and scan process for packages\. If your installer reboots, the agent is killed and the test and scan will fail\. 
+  The installer must not affect the network routing on the instance in such a way that the host becomes unreachable\. 

## Submitting your package group<a name="submitting-your-package-group"></a>

**To submit a package group to AWS Marketplace for use with Private Image Build**

1.  From the [AMMP](https://aws.amazon.com/marketplace/management/tour/), choose the **Image Build** tab\. 

1.  Under **Manage packages**, choose **Start package**\. 

1. In **Enter a unique name for your package group**, type the name of your product\. **Note**: the name must be less than 100 characters, and can only contain alphanumeric characters, underscores, and dashes\. Each product name associated with the AWS account used to create and publish package groups must be unique\. After you've used a name \(even if the build is unsuccessful\), you can't use the name again\. We recommend using a naming convention with a revision number included in the file name\. For example: **\[product\_group\_name\]<product\_name><version><platform><revision\_number>**\.

1.  In **Select one or more packages**, select a package from the dropdown list or choose **Browse** to locate and select the package group you want to upload\. 

1.  Under **Select supported operating system platform**, choose either **AWS Marketplace base Linux AMIs** or **AWS Marketplace base Windows AMIs**\. 

1.  Under **Select supported operating systems**, choose all the OSes that your package group will support, and then choose **Submit**\. 

    For each package group you submit, a build process is completed for each OS version you chose\. After you submit your package group, you are redirected to the **Scan status** page, where you can check progress of the image building and scanning process for each package group\. 

## Scan status<a name="scan-status"></a>

After you submit your package group, you can check the current status on the **Scan status** tab\. Each package group you've submitted is listed\. Choose the arrow next to the package group to expand the list and show the build and scan status for each package group you selected\. 

 Each entry will show the AMI ID, date you submitted the package group, and the status of the package group \(or build\)\. During the process, you can track the state of package groups and individual builds you have submitted\. There are four states your package group submission can be in, and five states individual builds can be in\. 

### Package group state<a name="package-group-state"></a>

 The package group state updates as automated steps complete\. You can return to the **Scan status** page to check on progress, or if the page is open you can choose **Refresh status** to update the information on the page\. The package group states are: 
+  **Building** – You have submitted your package group and the corresponding image\(s\) are being built\. 
+  **Scanning** – You have submitted your package group and the corresponding images\(s\) are being scanned\. 
+  **Successful** – All builds associated with your package group were successfully scanned\. Submit your product load form\. 
+  **Issues Found** – One or more builds for your submission failed that require your attention\. Choose the **information** icon next to the status for additional troubleshooting information\. 
+  **Investigating** – There was a problem uncovered during the build and scan process\. AWS Marketplace is investigating\. 

**Note**  
If your status remains in the **Investigating** state for four or more business days, contact the [AWS Marketplace Seller Operations team](https://aws.amazon.com/marketplace/management/contact-us/)\.

### OS build state<a name="os-build-state"></a>

 On the **Scan status** page you can click on the arrow next to the package group name to expand the entry to show each OS build that is part of the package group\. The OS build states are: 
+  **Building** – The build of your software on the OS is in progress\. This might take up to an hour to complete for each build\. 
+  **Scanning** – The build process completed successfully and the scan is in progress\. This might take several hours to complete\. 
+  **Successful** – The build and scan process completed successfully\. No further action on your part\. 
+  **Issues found** – There was a problem with the build or the scan process that require your attention\. Choose the **Information** icon next to the status for additional troubleshooting information\. 
+  **Investigating** – The build or scan process failed\. AWS Marketplace is investigating\. 

**Note**  
If your status remains in the **Investigating** state for four or more business days, contact the [AWS Marketplace Seller Operations team](https://aws.amazon.com/marketplace/management/contact-us/)\.

When your package group shows a status of **Successful**, this phase is complete\. Next, you can publish your package group as a new fulfillment option for your product on AWS Marketplace\.

## Submitting your product to AWS Marketplace<a name="submitting-your-listing-to-aws-marketplace"></a>

After you upload a package group AWS Marketplace you can submit a product load form to publish it as a new fulfillment option for your product, or as a new product if it does not already exist\. The load form is an Excel spreadsheet\. The first tab of the spreadsheet provides instructions for providing the metadata needed to publish your product on AWS Marketplace\. 

**To download and complete the load form**

1.  From the [AMMP](https://aws.amazon.com/marketplace/management/tour/), under the **Assets** tab, choose **File upload**\. 

1. On the **File Uploads** page, under **Product load forms and seller guides**, choose **Private Image Form**\. 

1. Download the product load form\. 

1. Complete the form\.

1. From the AMMP **Assets** tab, choose **File upload**\.

1. Choose the files you want to submit and enter a brief description\. 

AWS Marketplace creates or update your product entry\. If there are any questions on your submission, AWS Marketplace will contact you for clarification\. Your product is typically added or updated within five business days\. 

 When adding a package group as a new fulfillment option for your product consider the following options: 
+  Add the package group as an additional fulfillment option to an existing software version, on an existing public product on Marketplace\. With this approach, the software version on the AMI and package fulfillment options must match\. AWS Marketplace cannot replace an AMI on an existing software version\. 
+  If the package group has different software than what currently exists on AWS Marketplace, you can list the package group as a new software version on an existing product\. Using this approach, you must provide a successfully built and scanned AMI from the AMMP **Packages** tab\. You will have the option to test package fulfillment before making the new package group public\. However, the AMI will be visible to buyers right away\. This is consistent with the current experience for new software versions\. 