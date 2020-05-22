# Categories and metadata<a name="categories-and-metadata"></a>

Here are best practices, tips, and notes on supplying product metadata\. AWS Marketplace revises the product metadata solely for quality assurance and error correction\.

## Naming and describing your product<a name="naming-and-describing-your-product"></a>

The information about your product becomes the face of the product to customers\. As you decide on your product name, description, highlights, and so on, consider using information that is compelling and differentiates your software from other software\.

The information that you provide is important to ensure that potential customers have enough information to make informed decisions about choosing and buying your product\. 

### Creating the product name<a name="optimizing-the-product-name-field"></a>

Keep the following guidelines in mind as you create the product name: 
+ Use title case \(capitalize the first letter of each important word\)
+ Ensure that a customer can identify the product by the name alone
+ Use the name of the brand or manufacturer
+ Don't include descriptive data or hyperbole

Example: Smart Solution Load Balancer \- Premium Edition

### Writing the product description<a name="writing-the-product-description"></a>

The product description lists the product's features, benefits, and usage and provides other relevant and specific product information\. The description can be up to 350 characters long\. A customer might read the description if they're interested enough to learn more about the product\.

Keep the following guidelines in mind as you write the product description: 
+ Avoid unnecessary capitalization
+ Avoid unnecessary punctuation marks
+ Don't include redirect information
+ Check the spelling and grammar
+ Include only critical, useful information

Example: Smart Solution automatically distributes incoming application traffic across multiple Amazon EC2 instances\. It enables you to achieve even greater fault tolerance in your applications, seamlessly providing the amount of load\-balancing capacity you need to respond to incoming application traffic\. Smart Solution detects unhealthy instances in a pool and automatically reroutes traffic to healthy instances until the unhealthy instances have been restored\. Customers can enable Smart Solution in a single AWS Availability Zone or across multiple Availability Zones to ensure more consistent application performance\.

### Writing the product highlights<a name="writing-the-product-highlights"></a>

The product information page displays up to three product highlight bullet points\. The descriptive text for each highlight should describe the product's primary selling points in brief, informative language that is easy to understand\.

Example: Projecting costs: With Smart Solution, you pay only for what you use\. You're charged for each hour or partial hour that Smart Solution is running\.

### Writing the release notes<a name="writing-the-release-notes"></a>

Each time you update an AMI product, you must provide a description of the changes in release notes\. The release notes should contain specific information to help the user decide whether to install the update\. Use clear labels for the update, such as "Critical" for a security update or "Important" or "Optional" for other types of updates\.

### Writing the usage instructions<a name="writing-the-usage-instructions"></a>

The usage instructions ensure that each user can successfully configure and run the software\. Because this field appears during the AMI configuration process, the usage instructions must contain all of the information that the user needs\. Failure to provide clear instructions could result in unnecessary support contacts\.

Keep the following guidelines in mind as you write the usage instructions:
+ Write them with a new or moderately technical person in mind and not necessarily an IT manager or engineer\.
+ Don't assume that the user has prior experience with or extensive knowledge of the product or computer operating systems\.
+ Take the customer from 1\-Click launch all the way to using the product, including any configuration or special steps to get the application running\.

 Example: 

1. Launch the product via 1\-Click\.

1. Use a web browser to access the application at https://<EC2\_Instance\_Public\_DNS>/index\.html\.

1. Log in using the following credentials:
   + Username: user
   + Password: the instance\_id of the instance

### Writing the upgrade instructions<a name="writing-upgrade-instructions"></a>

 The upgrade instructions for a new version of an existing product should reflect information on how a customer can upgrade from one version of the product to another\. For example, how the customer can preserve data and settings when creating another instance\. This is to provide a good customer experience\. If there is no upgrade path, edit this field to specifically state there is no upgrade path\. 

**Example**

1. Do \*\*\*\*, and then \*\*\*\*\.

1. Check that all plugins used by your project are compatible with version \*\.\*, by doing \*\*\*\. If they aren't compatible, do \*\*\*\.

1. Make a backup of your data, by doing \*\*\*\.

## Choosing categories and keywords<a name="choosing-categories-and-keywords"></a>

 When you list your product, you can choose up to three software categories and corresponding subcategories for your product\. This helps customers discover your product as they browse or search the products on AWS Marketplace\. Choose only categories that are relevant to your product\. In most cases, only one category applies\. The product load form and the **Products** tab both contain a complete list of categories\. 

 Categories aren't the same as keywords\. The categories and subcategories available are predefined for AWS Marketplace, and you decide which ones apply to your product by selecting them from a list during the product request process\. Keywords aren't predefined, but are created during the process\. You don't need to add the category as a keyword\. 

### Creating search keywords<a name="creating-search-keywords"></a>

During the product request process, you can enter up to three keywords \(single words or phrases\) to help customers discover your product through site searches\. The keywords field can contain a maximum of 250 characters\. 

The following tips can help you to create a relevant set of search keywords:
+ Use terms that are relevant so that customers can easily find your products\.
+ Keywords must not contain the names of products published by other sellers or contain other sellers' names\.
+ Choose keywords from your customer's vocabulary—that is, words and phrases that customers are likely to use when thinking about your type of product\.
+ Create keywords based on specific features in your product\.
+ Don't use the product title as a keyword\. The product title is already indexed in our search\.

 **Note**: Keywords aren't the same as software categories\. Keywords are more specific terms that are related to your product\. 