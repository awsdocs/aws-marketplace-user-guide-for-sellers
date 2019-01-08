# Private Marketplace IT Administrator<a name="it-administrator"></a>

 If you're in an IT administrators role, you can configure your company’s private marketplace by selecting products, customizing the organization’s private marketplace homepage, and enabling the private marketplace for use by AWS accounts that are part of the organization in AWS Organizations\. 

## Creating Your Private Marketplace<a name="create-your-private-marketplace"></a>

 To create your private marketplace, navigate to [Private Marketplace](https://aws.amazon.com/marketplace/pmp/getstarted) and choose **Create a Private Marketplace\.** 

## Adding Products to Your Private Marketplace<a name="add-products-to-your-private-marketplace"></a>

 To add products to your organization’s private marketplace: 

1.  From the **Private Marketplace** administrator page, on the **Products** tab, choose **All AWS Marketplace products**\. You can search by product name or vendor name to find a product to add to your private marketplace\.

1.  Select the check box next to each product you want to add to your private marketplace and then choose **Add to Private Marketplace**\. This will add the product to your organization’s private marketplace\. 

1.  To verify that a product is in your private marketplace, from the **Private Marketplace** search page, search for the product you added to your private marketplace, and choose the product\. You are redirected to the product detail page for that product\. If the product is not in your private marketplace, a red banner appears at the top of the page\. You can add the product to your private marketplace by choosing **Add** in the red banner\. 

 You can return to the **Private Marketplace** administrator page at any time to add or remove other products\. 

## Customizing Your Private Marketplace<a name="customize-your-private-marketplace"></a>

 Once you have added products to your private marketplace, from the **Private Marketplace** administrator page, you can choose the **Profile** tab to configure your organization’s private marketplace profile\. 

 You can add a logo, create a custom welcome message, and customize to use your organization’s color scheme\. Instructions to customize your private marketplace are available of the profile page\. 

## Configuring Your Private Marketplace<a name="configure-your-private-marketplace"></a>

 After you are satisfied with your product list and your look and feel, you enable your private marketplace\. To enable or disable your private marketplace, from the **AWS Private Marketplace** administrators page, under **Private Marketplace status**, you can toggle the private marketplace status between **live** and **Not live**\. When your private marketplace is live, members of your organization can only subscribe to the products you have added to your private marketplace\. When your private marketplace is disabled, you retain the list of products\. However, disabling removes the procurement restriction control from users in your AWS Organizations organization\. 

## Configuring Procurement for Your Private Marketplace<a name="configuring-procurement-for-your-private-marketplace"></a>

 Private marketplace administrators need to be granted permission to create and modify a private marketplace\. Permission is granted using AWS Identity and Access Management \(IAM\)\. Using an account that is associated with your master \(payer\) account, you create a policy and apply it to a user, group, or role used for IT administration\. The policy enables the role or user to access and perform private marketplace administration actions\. The following policy is an example only\. The final syntax and actions are subject to change\.

```
{
  "Version": "2012-10-17",
  "Statement": [{
    "Effect": "Allow",
    "Action": [
      "aws-marketplace-private-marketplace:AddProduct",
      "aws-marketplace-private-marketplace:RemoveProduct",
      "aws-marketplace-private-marketplace:ListProduct",
      "aws-marketplace-private-marketplace:EnablePrivateMarketplace"
    ],
    "Resource": ["*"]
  }]
}
```

 To grant an administrator access, add the AWS Private Marketplace Admin policy to the specific IAM user\. 