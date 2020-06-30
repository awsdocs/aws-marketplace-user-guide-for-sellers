# AWS Marketplace for Desktop Applications \(AMDA\)<a name="amda"></a>

AWS Marketplace for Desktop Applications \(AMDA\) is a catalog of virtualized desktop applications that run on Amazon WorkSpaces\. AMDA makes it easy to find and subscribe to free and paid applications across 11 software categories\. Applications run in virtualized containers as if they were natively installed and buyers are charged on a per\-user, per\-month basis\. 

Buyers use the Amazon WorkSpaces Application Manager \(WAM\) console to deploy desktop applications to their WorkSpaces\. The applications are delivered to each WorkSpace through the WAM client application\. 

The virtualization technology enables fast delivery of programs, often without a reboot, so that users can quickly launch and use their subscribed applications\. Users are charged only for those applications they have been assigned, and charges accrue monthly from when they are first launched until the assignment is revoked\. Additional information: 
+  [Amazon WorkSpaces product pages](https://aws.amazon.com/workspaces/) 
+  [Amazon WorkSpaces testimonials](https://aws.amazon.com/workspaces/testimonials/) 
+  [AMDA help pages and frequently asked questions](https://aws.amazon.com/marketplace/help/buyer-desktop-apps?ref=help_ln_sibling) 
+  [AWS Marketplace for Desktop Applications catalog](https://aws.amazon.com/marketplace/desktop/search?ref_=footer_nav_desktop_view_products) 

## Starting the onboarding process<a name="beginning-the-onboarding-process"></a>

Under the terms of our AWS Marketplace for Desktop Applications Publisher Addendum \(the “AMDA Addendum”\), Amazon Web Services, Inc\. is the seller of record for applications you choose to make available through the AMDA channel\. As the seller of record, AWS will need to know the price you will charge AWS for the products you plan to have on AWS Marketplace\. Pricing should be on a per\-month basis, per user\. AWS will help you to determine the final price to buyers\. 

 In order to have your product published in non\-US Regions, AWS will also need you to provide certain export classification information, including the applicable [Export Control Classification Number](https://www.bis.doc.gov/index.php/licensing/commerce-control-list-classification/export-control-classification-number-eccn) \(ECCN\)\. 

During and after the initial testing of your product\(s\), a member of the AMDA Business Development team be available to answer any question you might have\. You will then receive an em ail from aws\-mp\-amda\-contract@amazon\.com with the AMDA Addendum for you to fill out, sign, and return for counter signature\. Note that the AMDA Addendum is an addendum to the Terms and Conditions for AWS Marketplace Sellers, so you will need to establish an AWS Marketplace seller account and click through these terms prior to beginning the onboarding process to have your applications made available on AMDA\. 

## Product submission and packaging<a name="product-submission-and-packaging"></a>

Virtualization and packaging are handled by the AWS Marketplace Managed Catalog Operations \(MCO\) team\. AMDA vendors provide the software installer, installation instructions, and product metadata\. MCO will work with you to complete the packaging and complete the process for AMDA\. Currently, all AMDA software must be packaged by using an MCO administrative account with permissions to the Amazon S3 bucket that will store the package\. AWS is unable to accept shared packages\. Review the following guidelines before you submit your product\. MCO will start processing your packaging request upon receipt of these items: 

1.  Software installer and license key: 

   1.  Amazon S3 bucket or external URL for the hosted Installer file \(\.msi, \.exe, etc\.\) 

   1.  Server license key that is compatible with Windows Server 2008 R2 

1.  Installation instructions: 

   1.  Known issues for Windows Server 2008 R2 

   1.  Silent install command line arguments 

   1.  Licensing mechanism notes: 

      1.  Where is the license stored? 

      1.  How is the license verified? 

      1.  Which actions trigger a license check? 

   1.  Auto\-update 

      1.  If enabled, describe how to disable this function 

   1.  Services or Registry requirements: 

      1.  List each required service or registry key, with a brief description of its purpose 

1.  Test servers, data files, and additional external elements 

   1.  If required for installation, provide a test environment for external components \(for example, SQL Server\) 

   1.  If your program processes data files, include test files so we can ensure performance and functionality 

1.  List all program dependencies, for example: 

   1.  C\+\+ redistributables 

   1.  Java, QuickTime, etc\. 

   1.  GPU/hardware requirements 

1.  Program technical contacts 

   1.  Who is the point of contact for technical questions or issues encountered during testing and packaging? 

## Application packaging types<a name="application-packaging-types"></a>

 AMDA packaging can be completed in two ways: virtualized installation or silent installation\. 

 Virtualized installation relies on AMDA packaging tools to monitor all file changes during the installation process\. AWS will point to the installer executable and click **Install**, which will monitor all file changes\. AWS then makes custom changes to the registry, services, and file structure to ensure program stability and performance\. 

 Some advanced programs require a silent installation mechanism\. In this case, AMDA will virtualize only the installer files so that the software is physically installed only when the application is first launched on the user’s WorkSpace\. Additional steps are required to script the removal of silent installation programs\. 

## Building the AMDA package<a name="building-the-amda-package"></a>

 The packaging process relies on creating a diff of the target installation machine, which is a Windows Server 2008 R2 virtual machine \(VM\)\. The packaging tool monitors the VM during the installation process, creates a manifest of the changed files, and rolls this into a package to be ingested\. 

 After capturing the changes programmatically, an AWS technician will inspect the files, services, and registry entries to ensure all changes were accurately captured\. During this process, the technician will remove all uninstall and auto\-update references to ensure the application stays within the confines of the virtualized package\. 

 Programs that rely on specific Windows services \(background\-running Windows services, \.dll requirements, etc\.\) might require additional testing and packaging\. By default, all program properties are virtualized to run on demand\. Some services might require elevation to ensure they are available to the program at runtime\. 

 License keys will be captured during the packaging process to help ensure a seamless, one\-click experience for end users\. If your program requires the license keys on first launch, include detailed notes about how to manually add the license to the applications files\. 

## Application metadata<a name="application-metadata"></a>

 Enter the application metadata into the AMDAProductDataLoad\.xlsx load form and include it with your application submission\. The current data load form is always available at [https://s3\.amazonaws\.com/aws\-mp\-vendor\-guide/AMDAProductDataLoad\.xlsx](https://s3.amazonaws.com/aws-mp-vendor-guide/AMDAProductDataLoad.xlsx) 
+  Title – This is the title of the product\. 
+  Full Description – This appears on the product detail page\. 
+  Short Description – This appears on the search results page\. 
+  End User License Agreement – This is the EULA that applies to the buyer's use of the product\. 
+  Image – This is the product image or logo that appears on the product detail page, in search results, and elsewhere on the AMDA website\. Provide a URL to a square\-formatted image logo 
+  Categories – This is the software category for the product\. See the AMDA home page to view the available categories\. 
+  Software By – This is the software developer that is displayed on the product page, which is usually your company name\. 
+  Vendor URL – This is the link to your website or a specific page that displays more information on the product\. 
  +  Support text/email/URL \(Only one field is required, but multiple contact points are encouraged\) 

## Ingestion and new version updates<a name="ingestion-and-new-version-updates"></a>

 Ingestion of each AMDA product is handled by the AWS Marketplace MCO team\. The current pipeline supports releases on Thursday\. AWS will lock on metadata and final packaging on Tuesday at noon PST\. Requests after Tuesday noon PST will be eligible on the following week’s publishing day\. New version updates are made on the same schedule\. 

 If no metadata updates are requested, only the installer and associated files are required\. 

 If you are updating metadata, send an updated product data load form to the [https://aws.amazon.com/marketplace/management/contact-us/](https://aws.amazon.com/marketplace/management/contact-us/) team\. 