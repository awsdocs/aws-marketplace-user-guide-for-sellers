# Building a private image<a name="building-a-private-image"></a>

When you create a private image, you select the software package in AWS Marketplace and the base AMI in your Amazon EC2 console that you will use to create the new private image\. Before starting the build process you must configure your AWS environment so that you can provide: 
+  The AMI ID for the base image that you will install the AWS Marketplace product on 
+  The name of an Amazon S3 bucket to store the build logs in\. The S3 bucket must be in the region that the AMI will be available in 
+  The Amazon EC2 instance profile that the package will be installed with \(see the previous section\) 
+  The IAM automation role that the image creation process will use to create the AMI \(see the previous section\) 
+  The name of the new private image 

 If you have experience using AWS services, you are likely familiar with choosing regions, finding the AMI ID on your Amazon EC2 dashboard, and working with Amazon S3 buckets\. 

 To find a product that supports building a private image, go to the [AWS Marketplace product search page](https://aws.amazon.com/marketplace/search/results?page=1&ref_=hmpg_categories_all) and, for the **Delivery Method** search filter, choose **Private Amazon Machine Image**\. From the detail page for the product, you configure procurement, configuration, and fulfillment options\. The product that you build is added to your AWS account\. 

 In addition to the prerequisites specified in the previous section, your base AMI must meet the following requirements: 
+  Linux AMIs must have either Wget or cURL installed and configured\. Windows AMIs must have PowerShell installed\. 
+  Linux AMIs must either be able to execute [EC2 User Data scripts](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html) or have the SSM agent pre\-installed\. 
+  Windows AMIs must have the SSM Agent pre\-installed\. 

 To build a private image: 

1.  In [AWS Marketplace](https://aws.amazon.com/marketplace/), from the product's detail page, choose **Continue to Subscribe**\. 

1.  On the **Subscribe to this software** page, under **Terms and Conditions**, choose **Show Details** to view the product instance type, software usage costs, and the end user license agreement \(EULA\)\. Depending on the product, you might see various types of subscriptions\. Once you choose the type of subscription, choose **Accept Terms**\. 

1.  Choose **Continue to Configuration**\. 

1.  On the **Configure this software** page, for **Fulfillment Option**, choose **Private Amazon Machine Image**\. 

1.  In the **Private Image** section, for **1\. Choose a region**, choose your region\. For **2\. Choose a private image to launch**, choose **Create New Private Image**\. 

1.  In the **Create New Private Image** section, for **Select a base AMI to use**, choose **Owned by me**, **Public Images**, or **Private images**\. 

   1.  **Owned by me** – AMIs that are specifically owned by your AWS account 

   1.  **Public Images** – AMIs that have been shared with all AWS accounts 

   1.  **Private images** – AMIs that have been shared with your AWS account 

1.  For **Input public base AMI ID** or **Input private base AMI ID**, either type the AMI ID or use the Amazon EC2 console to copy and paste the AMI ID for the image that you want to use as the base AMI\. 

1.  For **Instance Profile**, choose the instance role that you created as a prerequisite step\. 

1.  For **Automation Role**, choose the automation role that you created as a prerequisite step\. 

1.  For **Build Logs**, type the name of an Amazon S3 bucket that you want the logs to be stored in\. This is the simple bucket name, for example *myawsbucket*, rather than the full DNS name\. 

1.  For **Private Image Name**, type the name for the new private image\. 

 AWS Marketplace recommends using a naming convention for the private images you create to make the images easier to identify\. Also, when the AWS Marketplace Image Building Service creates a new private image, it adds an *AWSMarketplaceFulfillmentID* tag, which can be helpful in later identifying your private images\. You can also complete the following optional steps to provide additional detail, or you can start the build process by choosing **Start Build**\. 

 \(Optional\) To provide additional details about the private image: 

1.  For **Description Notes**, type any relevant information that you want included for the instance that will be used when building the private image\. 

1.  For **Instance Type**, choose the instance type that you want to use when building the private image\. 

1.  For **VPC**, choose the VPC that you want the instance to use when building the private image and then choose the security group and subnet\. 

1.  For **Enable Simple Notification System**, choose an existing topic or create a new topic to receive notifications when the build status changes\. 

1.  Choose **Start Build**\. 

 The build process takes 1\-2 hours to complete\. Note the following information about the process: 
+  The charges for services used during the build process will appear in the AWS account used to start the private image build process\. This includes the instance that runs while the AWS Marketplace product is being installed on the private image and the S3 bucket used for logs\. 
+  You can view the status of the build process or receive Amazon SNS messages\. 
+  Once the build is complete, the new private image is added to your AWS account and is available through the Amazon EC2 console as an AMI listed under **Owned by me**\. 
+  Repositories used to complete the build process must be local\. 
+  During the build, the process blocks access to the Internet\. 