# Launching a product<a name="buyer-configuring-a-product"></a>

 After you have an active subscription, choose **Continue to Configuration**, where you can select an available fulfillment option\. For container products, there might be up to four fulfillment options, which represent different configurations for the software\. For example, an ISV might create one fulfillment option that is a simple configuration used for testing the product, and another fulfillment option that is intended to be deployed at scale within an enterprise\. 

 Each fulfillment option includes information about which services are supported \(for example, Amazon ECS or Amazon EKS\) and also provides software version details\. After you have chosen the appropriate fulfillment option, you can choose **Continue to Fulfillment**\. 

## Launch process<a name="buyer-launching-a-product"></a>

 On the launch or fulfillment page for the product, deploy your selected fulfillment option, which is shown in the **Configuration Details** section\. Choose **Usage Instructions** to see documentation from the ISV about how to use the product, such as how to sign in to a web server, or post\-launch configuration\. 

 If the ISV has provided deployment templates to simplify deploying your product on AWS, such as an AWS CloudFormation template, a task definition for Amazon ECS, or a Helm chart for Kubernetes, information is provided for obtaining those templates\. There might be up to four deployment templates available for each fulfillment option\.

 If there are no deployment templates provided, or if you would prefer to create your own deployment template or manually configure how the product is launched, you can also access the container images directly from within Amazon ECR, which is a fully managed container registry that makes it easy for developers to store, manage, and deploy Docker container images\. Choose **View container image details** to open a dialog box with instructions for configuring your client to access the AWS Marketplace repository on Amazon ECR, and to see the appropriate Docker pull commands to use to retrieve the images\. 

After you have access to the deployment template or templates and container images, you can launch and run the software\. If the product is free or BYOL, there are no software charges, but there might be charges for the AWS infrastructure on which the product runs\. If the product is paid, either you pay a fixed monthly charge that provides unlimited usage, or you pay an hourly charge that is prorated per second with a one\-minute minimum\. Remember that if you cancel a subscription to a product, you are still charged for any running software until you terminate all instances of the software\. After you cancel a subscription to a paid product, however, you cannot launch any new instances of that software\.

 To run a paid product, you must create an IAM role that grants permission for your container to call `RegisterUsage`\. The following code can be used to configure these permissions\. You must supply this IAM role in the Amazon ECS [Task Role](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task_definition_parameters.html#task_role_arn) Developer Guide or in Amazon EKS [IAM Roles for Service Accounts](https://docs.aws.amazon.com/eks/latest/userguide/iam-roles-for-service-accounts.html)\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "aws-marketplace:RegisterUsage"
                ],
                "Effect": "Allow",
                "Resource": "*"
        }
    ]
}
```

## Canceling a subscription<a name="buyer-cancelling-a-subscription"></a>

 To cancel a subscription to a product, use the **Your Software** page\. 