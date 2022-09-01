# Controlling access to AWS Marketplace Vendor Insights<a name="seller-security-iam-config-vend-insights"></a>

 AWS Identity and Access Management \(IAM\) is an AWS service that helps you control access to AWS resources\. IAM is an AWS service that you can use with no additional charge\. If you're an IAM administrator, you control who can be *authenticated* \(signed in\) and *authorized* \(have permissions\) to use AWS Marketplace resources\. AWS Marketplace Vendor Insights uses IAM to control access to vendor data, assessments, vendor self\-attestation, and industry standard audit reports\.

The recommended way to control who can do what in AWS Marketplace Management Portal is to use IAM to create users and groups\. Then you add the users to the groups, and manage the groups\. You can assign a policy or permissions to the group that provide read\-only permissions\. If you have other users that need read\-only access, you can add them to the group you created rather than adding permissions to their user account\.

A *policy* is a document that defines the permissions that apply to a user, group, or role\. In turn, the permissions determine what users can do in AWS\. A policy typically allows access to specific actions, and can optionally grant that the actions are allowed for specific resources, like Amazon EC2 instances, Amazon S3 buckets, and so on\. Policies can also explicitly deny access\. A *permission* is a statement within a policy that allows or denies access to a particular resource\. 

**Important**  
All of the IAM users that you create authenticate by using their credentials\. However, they use the same AWS account\. Any change that a user makes can impact the whole account\. 

 AWS Marketplace has permissions defined to control the actions that someone with those permissions can take in AWS Marketplace Management Portal\.There are also policies that AWS Marketplace created and manage that combine several permissions\. The `AWSMarketplaceSellerProductsFullAccess` policy gives the user full access to products in the AWS Marketplace Management Portal\. 

For more information about the actions, resources, and condition keys that are available, see [Actions, resources, and condition keys for AWS Marketplace Vendor Insights](https://docs.aws.amazon.com/service-authorization/latest/reference/list_awsmarketplacevendorinsights.html) in the Service Authorization Reference\. 

## Permissions for AWS Marketplace Vendor Insights sellers<a name="permissions-aws-vendor-insights-sellers"></a>

You can use the following permissions in IAM policies for AWS Marketplace Vendor Insights\.

You can combine the preceding permissions into a single IAM policy to grant the permissions that you want\. 

## `CreateSecurityProfile`<a name="vi-permissions-createsecprofile"></a>

Use `CreateSecurityProfile` to grant permissions to create a security profile in AWS Marketplace Vendor Insights\.

This policy grants permissions to create a new security profile in AWS Marketplace Vendor Insights\. 

**Permissions details**

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "vendor-insights:CreateSecurityProfile"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```

## `GetSecurityProfiles`<a name="vi-permissions-getsecprofile"></a>

This policy grants permissions to return the details of an existing security profile of vendors in AWS Marketplace Vendor Insights\. 

**Permissions details**

```
{
      "Name": "GetSecurityProfile",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ReadOnly",
        "ReadWrite"
      ],
      "Description": "Grants permission to return the details of an existing security profile",
      "RequiredResources": [
        {
          "Name": "SecurityProfile"
        }
      ]
    }
```

## `ListSecurityProfiles`<a name="vi-permissions-listsecprofiles"></a>

This policy grants permissions to list existing security profiles for vendors in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "ListSecurityProfiles",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html", 
       "ActionGroups": [
        "ListOnly",
        "ReadOnly",
        "ReadWrite"
      ],
      "Description": "Grants permission to list existing security profiles"
    }
```

## `AssociateDataSource`<a name="vi-permissions-assocdatasource"></a>

This policy grants permissions to associate a security profile with a data source in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "AssociateDataSource",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ReadWrite"
      ],
      "Description": "Grants permission to associate security profile with a data source",
      "RequiredActions": [
        "vendor-insights:GetDataSource"
      ],
      "RequiredResources": [
        {
          "Name": "SecurityProfile"
        }
      ]
    }
```

## `DisassociateDataSource`<a name="vi-permissions-disassocdatasource"></a>

This policy grants permissions to disassociate a security profile from the data source in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "DisassociateDataSource",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ReadWrite"
      ],
      "Description": "Grants permission to disassociate security profile from a data source",
      "RequiredActions": [
        "vendor-insights:GetDataSource"
      ],
      "RequiredResources": [
        {
          "Name": "SecurityProfile"
        }
      ]
    }
```

## `UpdateSecurityProfile`<a name="vi-permissions-updatesecprofile"></a>

This policy grants permissions to update the security profile in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "UpdateSecurityProfile",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ReadWrite"
      ],
      "Description": "Grants permission to update the security profile",
      "RequiredResources": [
        {
          "Name": "SecurityProfile"
        }
      ]
    }
```

## `ActivateSecurityProfile`<a name="vi-permissions-activatesecprofile"></a>

This policy grants permissions to activate a security profile in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "ActivateSecurityProfile",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ReadWrite"
      ],
      "Description": "Grants permission to activate the security profile",
      "RequiredResources": [
        {
          "Name": "SecurityProfile"
        }
      ]
    }
```

## `DeactivateSecurityProfile`<a name="vi-permissions-deactivatesecprofile"></a>

This policy grants permission to deactivate the security profile in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "DeactivateSecurityProfile",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ReadWrite"
      ],
      "Description": "Grants permission to deactivate the security profile",
      "RequiredResources": [
        {
          "Name": "SecurityProfile"
        }
      ]
    }
```

## `GetSecurityProfileSnapshot`<a name="vi-permissions-getsecprofilesnapshot"></a>

This policy grants permissions to return the details of a security profile snapshot in AWS Marketplace Vendor Insights\.

**Permissions details**

```
 {
      "Name": "GetSecurityProfileSnapshot",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ReadOnly",
        "ReadWrite"
      ],
      "Description": "Grants permission to return the details of a security profile snapshot",
      "RequiredResources": [
        {
          "Name": "SecurityProfile"
        }
      ]
    }
```

## `ListSecurityProfileSnapshots`<a name="vi-permissions-listsecprofilesnapshot"></a>

This policy grants permissions to return the snapshot summary list \(or collected information\) for an existing security profile in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "ListSecurityProfileSnapshots",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ListOnly",
        "ReadOnly",
        "ReadWrite"
      ],
      "Description": "Grants permission to return the snapshot summary list for an existing security profile",
      "RequiredResources": [
        {
          "Name": "SecurityProfile"
        }
      ]
    }
```

## `GetEntitledSecurityProfileSnapshot`<a name="vi-permissions-getentitledsecprofilesnapshot"></a>

This policy grants permissions to return the details of a security profile snapshot to the user to view a register entitled to read in AWS Marketplace Vendor Insights\. This allows a user to view detailed security profiles marked as `Entitled`\.

**Permissions details**

```
{
      "Name": "GetEntitledSecurityProfileSnapshot",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html", 
       "ActionGroups": [
        "ReadOnly",
        "ReadWrite"
      ],
      "Description": "Grants permission to return the details of a security profile snapshot that requester is entitled to read",
      "RequiredResources": [
        {
          "Name": "SecurityProfile"
        }
      ]
    }
```

## `ListEntitledSecurityProfileSnapshots`<a name="vi-permissions-listentitledsecprofilesnapshot"></a>

This policy grants permissions to return the snapshot summary list for an existing security profile that the requester is entitled to list in AWS Marketplace Vendor Insights\. This allows a user to view detailed security profiles marked as `Entitled`\.

**Permissions details**

```
{
      "Name": "ListEntitledSecurityProfileSnapshots",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ListOnly",
        "ReadOnly",
        "ReadWrite"
      ],
      "Description": "Grants permission to return the snapshot summary list for an existing security profile that requester is entitled to list",
      "RequiredResources": [
        {
          "Name": "SecurityProfile"
        }
      ]
    }
```

## `ListEntitledSecurityProfile`<a name="vi-permissions-listentitledsecprofile"></a>

This policy grants permissions to list and view entitled security profiles in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "ListEntitledSecurityProfiles",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ListOnly",
        "ReadOnly",
        "ReadWrite"
      ],
      "Description": "Grants permission to list entitled security profiles"
    }
```

## `CreateDataSource`<a name="vi-permissions-createdatasource"></a>

This policy grants permissions to create a data source in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "CreateDataSource",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ReadWrite"
      ],
      "Description": "Grants permission to create a new data source",
      "CreatesResources": [
        {
          "Name": "DataSource"
        }
      ]
    }
```

## `ListDataSources`<a name="vi-permissions-listdatasources"></a>

This policy grants permissions to list and view existing data sources in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "ListDataSources",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ListOnly",
        "ReadOnly",
        "ReadWrite"
      ],
      "Description": "Grants permission to list existing data sources"
    }
```

## `GetDataSource`<a name="vi-permissions-getdatasource"></a>

This policy grants permissions to gather and review details of an existing data source in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "GetDataSource",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ReadOnly",
        "ReadWrite"
      ],
      "Description": "Grants permission to retrieve the details of an existing data source",
      "RequiredResources": [
        {
          "Name": "DataSource"
        }
      ]
    }
```

## `DeleteDataSource`<a name="vi-permissions-deletedatasource"></a>

This policy grants permissions to delete a data source in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "DeleteDataSource",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ReadWrite"
      ],
      "Description": "Grants permission to delete a data source",
      "RequiredResources": [
        {
          "Name": "DataSource"
        }
      ]
    }
```

## `GetProfileAccessTerms`<a name="vi-permissions-getprofileaccessterms"></a>

This policy grants permissions to view access terms for a vendor insights profile in AWS Marketplace Vendor Insights\.

**Permissions details**

```
{
      "Name": "GetProfileAccessTerms",
      "DocPageRel":"buyer-security-iam-config-vend-insights.html",
      "ActionGroups": [
        "ReadOnly",
        "ReadWrite"
      ],
      "Description": "Grants permission to get the access terms for a vendor insights profile"
    }
  ]
}
```

## Additional resources<a name="additional-resources-vi"></a>

 The following resources in the *IAM User Guide* provide more information about getting started and using IAM:
+  [Security best practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) 
+  [Managing IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-using.html#create-managed-policy-console) 
+  [Attaching a policy to an IAM user group](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_groups_manage_attach-policy.html) 
+  [IAM Identities \(users, user groups, and roles\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) 
+  [Creating your first IAM admin user and user group](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html) 
+  [Security best practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html) 
+  [Managing IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-using.html#create-managed-policy-console) 
+  [IAM Identities \(users, user groups, and roles\)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html) 
+  [Controlling access to AWS resources using policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_permissions.html)