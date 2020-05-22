# Creating and managing a private marketplace<a name="private-catalog-administration"></a>

 To create and manage a private marketplace you must have the IAM permissions found in the `AWSPrivateMarketplaceAdminFullAccess` IAM policy\. For information on applying this policy to IAM users, groups, and roles, see [Creating a private marketplace IT administrator](it-administrator.md)\.

## Creating your private marketplace<a name="create-your-private-marketplace"></a>

 To create your private marketplace, navigate to [Private Marketplace](https://aws.amazon.com/marketplace/pmp/getstarted) and choose **Create a Private Marketplace**\.

## Adding products to your private marketplace<a name="add-products-to-your-private-marketplace"></a>

 To add products to your organization’s private marketplace: 

1. From the **Private Marketplace** administrator's page, on the **Products** tab, choose **All AWS Marketplace products**\. You can search by product name or seller name\.

1. Select the check box next to each product to add to your private marketplace and then choose **Add to Private Marketplace**\.

### Verifying products in your private marketplace<a name="verify-product-in-marketplace"></a>

To verify that a product is in your private marketplace:

1. From the **Private Marketplace** search page, choose a product\.

1. On the product's detail page, note whether a red banner is shown at the top of the page\. 

   If the red banner isn't shown, the product exists in your private marketplace\. If the red banner is shown, the product isn't in your private marketplace\.

1. \(Optional\) To add the product to your private marketplace, choose **Add** in the red banner\.

 You can return to the **Private Marketplace** administrator's page at any time to add or remove other products\. 

## Managing user requests<a name="manage-user-requests-private-marketplace"></a>

You can allow users to submit requests for products to be added to your private marketplace with the software request feature\. To do so, navigate to the administrator's page for your private marketplace, and from the **Products** tab, choose **Pending requests**\. From here you can review a table of existing requests your users have made for products they've requested to be added to your private marketplace\.

You can add any number of requested products from this page by first selecting the check box next to the name of each requested product, and then choosing **Add to Private Marketplace**\. Similarly, you can also decline one or more selected requests by choosing **Decline**\. To view more information about a product \(or its software request\), choose **View details** in the **Details** column for that request in the table\.

When you decline a product request, you can add a reason and prevent future requests for this product on your private marketplace\. This won't prevent you from adding the product to your private marketplace, but it does prevent your users from requesting the product\.

## Customizing your private marketplace<a name="customize-your-private-marketplace"></a>

On the **Private Marketplace** administrator's page, you can choose the **Profile** tab to configure your organization’s private marketplace profile\. You can add a logo, create a custom welcome message, and customize the user interface to use your organization’s color scheme\. Instructions to customize your private marketplace are available on the profile page\. 

## Configuring your private marketplace<a name="configure-your-private-marketplace"></a>

 After you are satisfied with your product list and your marketplace's appearance, enable your private marketplace\. To enable or disable your private marketplace, from the **AWS Private Marketplace** administrator's page, under **Private Marketplace status**, you can toggle the private marketplace status between **live** and **Not live**\.

You can also allow users to submit software requests with the **Software requests** toggle\. When your private marketplace is live, members of your organization can buy only the products that you added to your private marketplace\. When your private marketplace is disabled, you retain the list of products\. However, disabling removes the procurement restriction control from users in your AWS Organizations organization\. 