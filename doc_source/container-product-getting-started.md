# Getting started with container products<a name="container-product-getting-started"></a>

This topic outlines how to get started with a container product, and goes through all the steps related to creating, testing, and publishing your first container product\. For this exercise, we assume that you already have at least one container created in Amazon ECS, Amazon EKS, or Fargate, and that you have links for the associated images\. We recommend that you plan your pricing, entitlement, and metering strategy well in advance of publicly publishing your product\.

**Topics**
+ [Creating a container product](#create-container-product)
+ [Downloading and filling out the product load form for container products](#container-product-load-form)
+ [Integrating metering for your container product](#getting-started-integrate-metering)
+ [Publishing container products](#container-product-publishing)
+ [Container product scans](#container-security)

## Creating a container product<a name="create-container-product"></a>

The following procedure outlines how to create a new container product in the AWS Marketplace Management Portal\.

**To create a container product**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the menu bar, expand **Assets**, and choose **Container**\.

1. Provide a customer\-facing name for your product, and choose **Create**\.

1. Make a note of the **Product ID** and **Product code**, as you'll need them when you fill out the product load form\.

1. Choose **Create new group** to create a container group\. Each container group represent a fulfillment option for your product\.

1. Provide a customer\-facing name for your container group\. We strongly recommend that each container group within a product have a unique name\.

1. In **Image location**, provide the URL for one image in this container group, and choose **Add and scan**\. When you submit a container image URL, we scan it and check for security vulnerabilities\. Typically, this scan takes 20 to 25 minutes\. For more information, see [Container product scans](#container-security)\.

   These URL links can be the name of a public external repository or a URL to a private repository such as Amazon Elastic Container Registry \(Amazon ECR\)\. For images in Amazon ECR, you must specify the image tag\. You can have up to four links to deployment templates for each fulfillment option\.

   For example, you could use either of the following formats as pointers to your images: 
   +  `nginx:mytag` 
   +  `123456789012.dkr.ecr.us-west-2.amazonaws.com/nginx:mytag` 

1. Repeat the previous step for each of your images in this container group\. When you have finished adding images to your container group, choose **Submit container group**\.

1. A dialog box will open, prompting you to finalize your container group\. Once finalized, you won't be able to edit the container group again\. To finalize your container group, its name, and the included images, choose **Get ID**\.

1. Make a note of the container group ID, as you'll need it when you fill out the product load form\.

1. \(Optional\) Create additional container groups\. Each container product can have up to 4 container groups, one for each fulfilment option\.

You've now created your container product\. When you first create a container product it is not automatically published\. AWS Marketplace publishes your product once you have submitted the completed product load form with your product metadata and your container images have been successfully scanned\. For more information, see [Publishing container products](#container-product-publishing)\.

Next, you'll need to perform two different processes, downloading and filling out the product load form, and integrate and test metering into your software\. These two steps can be done in any order, or in parallel\.

## Downloading and filling out the product load form for container products<a name="container-product-load-form"></a>

The following procedure outlines what to do with the product load form\.

**To download and fill out the product load form**

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the menu bar, expand **Assets**, and choose **File Upload**\.

1. From **Product load forms for download** on the right side, choose **Containers Product Load Form**\.

1. Open the spreadsheet on your computer and fill out the fields to define your product\. This will include your product ID and container group ID, which you made notes of when you created your container product\.

   Columns `Product ID` through `End User License Agreement URL` are for standard product information such as title, description, product highlights, free trials, product categories, logo image URL, and EULA\. Columns `Container Group 1: Group ID` through `Container Group 1: Deployment Template URL 4` are for metadata specific to your first container fulfillment option\. Additional fulfillment options metadata can be provided from columns `Container Group 2: Group ID` through `Container Group 4: Deployment Template URL 4`\.
**Tip**  
When viewing the product load form in Microsoft Excel, hover over each of the fields to show comments that provide guidance on how to fill in each field\. 

   You must provide pricing and metering dimensions, based on your pricing model for your product\. For more information, see the following:
   + [Product load form for custom metering](container-metering-meterusage.md#custom-metering-product-load-form)
   + [Product load form for hourly metering](container-metering-registerusage.md#hourly-metering-product-load-form)

1. Save your product load form\.

1. Open a web browser and sign into the [AWS Marketplace Management Portal](http://aws.amazon.com/marketplace/management/)\.

1. From the menu bar, expand **Assets**, and choose **File Upload**\.

1. In **Upload File**, browse your computer and choose the product load form file you saved for this container product\.

1. Provide a brief description for your form to help you identify it among the other product load forms you upload\.

1. Choose **Upload**\.

1. Your uploaded product load form will appear in a table at the bottom of the page\.

## Integrating metering for your container product<a name="getting-started-integrate-metering"></a>

You use the [AWS Marketplace Metering Service](https://docs.aws.amazon.com/marketplacemetering/latest/APIReference/Welcome.html) for both checking entitlement to use your product and metering usage for billing\. For more information, see [AWS Marketplace Metering Service integration](entitlement-and-metering-for-paid-products.md)\.

## Publishing container products<a name="container-product-publishing"></a>

When you publicly publish a container product, you make it visible to all AWS customers who can then subscribe and launch your product\. The pricing model can't be changed for publicly published products\. Before you can publish a product, you'll need to have completed the following previous steps:
+ [Creating a container product](#create-container-product)
+ [Downloading and filling out the product load form for container products](#container-product-load-form)
+ [Integrating metering for your container product](#getting-started-integrate-metering)

We will review the information in your product load form, as well as your test calls to the AWS Marketplace Metering Service\. After that, we publish your product in a limited visibility state for your review and approval\. As a parallel effort, you would also complete the necessary engineering integration for your product and related offers\. During this time you should review your product including image links, deployment templates, descriptions, and prices to ensure accuracy\.

Once all testing is complete, and you've approved the product, we publish the container product publicly\. As part of the publishing process, your container images are copied to an AWS Marketplace repository on Amazon ECR\. You must update the references in your deployment templates to point to the new image URLs or your product may not work as intended\.

 The final URL for each image will be of the following format: 

```
mp-account-#.dkr.us-east-1.amazonaws.com/product_id/container_group_id/container_name:version_title-latest
```

**Note**  
The account that you use is the AWS Marketplace account that the secure Amazon ECR repository is created with\. That account Id can change across images and product versions\.

## Container product scans<a name="container-security"></a>

When you submit a container image URL, we scan it and check for security vulnerabilities\. We examine the images you provide for known security vulnerabilities\. To do this, we perform a layer\-by\-layer static scan on the image\. If we find critical vulnerabilities with remotely exploitable risk vectors, we present the list of found issues\. We strongly recommend that you perform your own security analysis using a container image scanner such as Clair, Twistlock, Aqua Security, or Trend Micro to avoid delays in the ingestion and publishing process\. 

Your choice of base image for building your container images can have a significant influence on the security profile of the final image\. If you pick a base image that already has known critical vulnerabilities, they will get flagged because of the base layer, even if your application software layers are clean\. We recommend that you verify that you are starting with a vulnerability\-free base container before you build your images and submit them to AWS Marketplace\. 

After the scan is complete, we will provide the container group ID that you need to use in the product load form to identify the set of images associated with the fulfillment option you are creating\. You can define up to four fulfillment options for each container product you submit, with up to 50 container images in each set\. 