# Providing details for a professional services product<a name="proserv-product-details"></a>

When you publish a professional services product on AWS Marketplace, you must provide the product metadata\. This topic discusses information that is useful when you prepare or edit your product's details\.

**Note**  
For information about guidelines and requirements for professional services products, see [Requirements for professional services products ](proserv-product-guidelines.md)\.

**Topics**
+ [Product descriptions](#proserv-product-descriptions)
+ [Additional resources](#proserv-additional-resources)
+ [Support information](#proserv-support-information)
+ [Pricing dimensions](#proserv-pricing-dimensions)
+ [Product visibility](#proserv-product-visibility)

## Product descriptions<a name="proserv-product-descriptions"></a>

The product descriptions section in the product details is the core of your product\. It describes your product to your potential buyers so that they can make a purchasing decision\. This section of the product details includes the following data:
+ **Product title** – The name of your product\. This is used to identify your product; it's visible on the product page and within search results\. Provide a meaningful name for your product\. It must be unique within AWS Marketplace\.
+ **SKU** – \(Optional\) Used to track your products on AWS Marketplace\. This information is for your own use; buyers don't see it\.  
+ **Short description** – A concise description of your product that appears on the tiles and underneath the product title in the AWS Marketplace product catalog\. 
+ **Long description** – A longer, formatted description that describes the details of your product to buyers\. List the product features, benefits, usage, and other information specific to the product\. Use the available formatting to make the information easier to understand and scan\.
+ **Product logo** – This field is a public S3 URL that points to an image file that represents your product\. The file must be in \.png, \.jpg, or \.gif format, with a transparent or white background, under 5MB, and be between 110\-10,000 pixels wide and tall\. The logo is uploaded during product submission, and stored in AWS Marketplace\. Modifying the contents of the URL will not modify the logo in AWS Marketplace after it is submitted\.
**Note**  
The S3 URL that you provide must be publicly available\. This is a property of the S3 bucket in which the file resides\. For more information, see [How do I edit public access settings for S3 buckets?](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/block-public-access-bucket.html) in the Amazon Simple Storage Service Console User Guide\.
+ **Highlights** – A set of one to three short points about your product, describing its key features or differentiators\. At least one highlight is required\.
+ **Product categories** – The types of service that you provide\. You must choose at least one, and up to three, categories\. There are many categories to choose from, but professional services products must include at least one of the following:  
**Assessment**  
Evaluation of the customer's current operating environment to find the the right solutions for their organization\.  
**Implementation**  
Help with configuration, setup, and deployment of third\-party software\.  
**Premium support**  
Access to guidance and assistance from experts, designed for the customer's needs\.  
**Managed services**  
End\-to\-end environment management on the customer's behalf\.  
**Training**  
Tailored workshops, programs, and educational tools provided by experts to help the customer employees learn best practices\.
+ **Keywords for search results** – Provide up to three keywords that buyers might use to search for your product\. You can list keywords in a comma\-separated list, up to 250 characters\.
+ **Associated products** – Include at least one public product from AWS Marketplace that your service either works with or supports\. AWS Marketplace uses these products as input when selecting products to show on your product's details page or in **Related products** for those products\.

## Additional resources<a name="proserv-additional-resources"></a>

In the **Additional resources** section of the product details, you can provide links to resources that you have created to help your customers\. This is an optional set of one to three downloadable resources that are stored online\. Examples of resources include product information sheets, whitepapers, or product manuals\. For each resource, provide a name and a URL for the resource\.

## Support information<a name="proserv-support-information"></a>

This section is a formatted text field that allows you to describe the support that you provide for your service\.

Customers expect support on issues such as using the services, troubleshooting, and requesting refunds \(if applicable\)\. The support description should contain a statement about the level of support a customer can expect\. Consider including support details for both pre\-purchase questions and post\-purchase issues\.

## Pricing dimensions<a name="proserv-pricing-dimensions"></a>

Pricing dimensions for professional services are packages that you offer\. For example you might offer *Silver*, *Gold*, and *Platinum* support\. Or you might offer 10, 20, or 50 hours of consulting\. For each dimension you want to offer \(at least one, up to 24\), specify a name and a description\. When you create a private offer for the product by working with a buyer directly, you set the actual prices for these dimensions\.

**Note**  
For information about how pricing dimensions are used, and how prices are set, see [Creating private offers](proserv-getting-started.md#proserv-create-offer)\.

## Product visibility<a name="proserv-product-visibility"></a>

Released products can be visible in AWS Marketplace to just your own account, to a small set of test accounts, or to all AWS accounts\. By default, the product is published in private release\. To change the product visibility, see [Editing product visibility](proserv-getting-started.md#proserv-edit-visibility)\.