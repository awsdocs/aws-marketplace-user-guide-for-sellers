# Configuring a Product<a name="buyer-configuring-a-product"></a>

 Once you have an active subscription, choose **Continue to Configuration**, which will enable you to select an available fulfillment option\. For container products, there may be up to four fulfillment options, which represent different configurations for the software\. For example, an ISV may create one fulfillment option that is a simple configuration used for testing the product, and another fulfillment option that is intended to be deployed at scale within an enterprise\. 

 Each fulfillment option will include information about which services are supported \(for example, Amazon ECS or Amazon EKS\) and also provide software version details\. Once you have chosen the appropriate fulfillment option, you can choose **Continue to Fulfillment**\. 

## Launching a Product<a name="buyer-launching-a-product"></a>

 On the launch or fulfillment page for the product, deploy your selected fulfillment option, which will be shown in the **Configuration Details** section\. Choose **Usage Instructions** to see documentation from the ISV on how to use the product, such as how to log in to a web server, or post\-launch configuration: 

 If the ISV has provided deployment templates to simplify deploying your product on AWS, such as an AWS CloudFormation template, a task definition for Amazon ECS, or a Helm chart for Kubernetes, information will be provided on how to obtain those templates\. There may be up to four deployment templates available for each fulfillment option\. During the preview, there will be links provided to the templates and other configuration documentation, or you may need to contact the ISV directly to access those resources\. 

 If there are no deployment templates provided, or if you would prefer to create your own deployment template or manually configure how the product is launched, you can also access the container images directly from within Amazon ECR, which is a fully managed container registry that makes it easy for developers to store, manage, and deploy Docker container images\. Choose **View container image details** to open a dialog box with instructions on how to configure your client to access the AWS Marketplace repository on Amazon ECR, and to see the appropriate Docker pull commands to use to retrieve the images: 

 Once you have access to the deployment template or templates and container images, you can launch and run the software\. If the product is free or BYOL, there will be no software charges, but there may be charges for the AWS infrastructure on which the product runs\. If the product is paid, either you will pay a fixed monthly charge that provides unlimited usage, or you will pay an hourly charge that is pro\-rated per second with a one\-minute minimum\. 

 Remember that if you cancel a subscription to a product, you will still be charged for any running software until you terminate all instances of the software\. Once you cancel a subscription to a paid product, however, you will not be able to launch any new instances of that software\. 

## Canceling a Subscription<a name="buyer-cancelling-a-subscription"></a>

 To cancel a subscription to a product, use the **Your Software** page\. For the preview, you will need to enter the following URL manually: [https://aws\.amazon\.com/marketplace/library?filterType=container](https://aws.amazon.com/marketplace/library?filterType=container)\. From this page, you can also view the usage instructions for the product, or launch more instances of the product by choosing **Launch More Software**, which will bring you back to the configuration page: 