# API Reference<a name="api-reference"></a>

 You can use this reference to build private images using the AWS Marketplace Image Build Service API\. The AWS account that you use to build a private image must have the IAM permissions specified in the AWSMarketplaceImageBuildFullAccess managed policies\. You can use an existing role or create a new role using this\. To add the policy to a user, group or role: 

1.  Sign in to the AWS Management Console and open the AWS IAM console at [https://console\.aws\.amazon\.com/iam/](https://console.aws.amazon.com/iam/)\. 

1.  In the navigation pane of the AWS IAM console, choose **Policies**\. 

1.  Next to **Filter policies**, enter *AWSMarketplaceImageBuildFullAccess*\. The policy should be listed in the results\. 

1.  In the **Results** pane, choose **AWSMarketplaceImageBuildFullAccess**\. 

1.  In the **Policy actions** pulldown menu, choose **Attach**\. 

1.  Select the users, groups and roles you want to attach this policy to, and then choose **Attach Policy**\. 

 The next time that a user or member of a group or role you selected accesses the AWS Marketplace website, they can perform the tasks associated with the private image build process\. 

## Building a Private Image Using the CLI<a name="building-a-private-image-using-the-cli"></a>

 Configure your CLI by creating a JSON file using the following code, and then executing the following command\. 

 **Code** 

```
{
  "version":"2.0",
  "metadata":{
    "apiVersion":"2017-12-15",
    "endpointPrefix":"imagebuild.marketplace",
    "jsonVersion":"1.1",
    "protocol":"json",
    "serviceAbbreviation":"Marketplace Image Build",
    "serviceFullName":"AWS Marketplace Image Build Service",
    "serviceId":"Marketplace Image Build",
    "signatureVersion":"v4",
    "signingName":"aws-marketplace",
    "targetPrefix":"AWSMPImageBuilding",
    "uid":"marketplaceimagebuild-2017-12-15"
  },
  "operations":{
    "DescribeBuilds":{
      "name":"DescribeBuilds",
      "http":{
        "method":"POST",
        "requestUri":"/"
      },
      "input":{"shape":"DescribeBuildsRequest"},
      "output":{"shape":"DescribeBuildsResult"},
      "errors":[
        {"shape":"InternalServerErrorException"},
        {"shape":"InvalidNextTokenException"},
        {"shape":"InvalidMaxResultsException"},
        {"shape":"InvalidFilterException"}
      ],
      "documentation":"&lt;p>Retrieves information about build records for all builds associated with the AWS account in use, including status, explanation, and the id of the resulting AMI. The results are in descending order of creation time. You can filter results by build id, status and fulfillment option id. Use the pagination parameters to retrieve results in a set of sequential pages. You can only retrieve information about builds you own.&lt;/p>"
    },
    "StartBuild":{
      "name":"StartBuild",
      "http":{
        "method":"POST",
        "requestUri":"/"
      },
      "input":{"shape":"StartBuildRequest"},
      "output":{"shape":"StartBuildResult"},
      "errors":[
        {"shape":"InternalServerErrorException"},
        {"shape":"BuildLimitExceededException"},
        {"shape":"IdempotentParameterMismatchException"},
        {"shape":"InstallerMismatchException"},
        {"shape":"InvalidFulfillmentOptionIdException"},
        {"shape":"InvalidSourceImageIdException"},
        {"shape":"InvalidDestinationImageNameException"},
        {"shape":"InvalidSnsTopicArnException"},
        {"shape":"UnauthorizedOperationException"}
      ],
      "documentation":"&lt;p>Initiates a build that installs the specified Marketplace product on the source AMI, creating a new AMI in the same region.&lt;/p>"
    }
  },
  "shapes":{
    "Build":{
      "type":"structure",
      "members":{
        "BuildId":{
          "shape":"String",
          "documentation":"&lt;p>Unique identifier for a build.&lt;/p>"
        },
        "DestinationImage":{
          "shape":"DestinationImage",
          "documentation":"&lt;p>Details about the new image to be created in the same region.&lt;/p>"
        },
        "FulfillmentOptionIds":{
          "shape":"StringList",
          "documentation":"&lt;p>List of fulfillment option ids of Marketplace software products to install on the image.They need to be retrieved from the Marketplace Website.&lt;/p>"
        },
        "Products":{
          "shape":"ProductList",
          "documentation":"&lt;p>Details about the Marketplace software products to install on the image. This structure is populated by Marketplace.&lt;/p>"
        },
        "SourceImage":{
          "shape":"SourceImage",
          "documentation":"&lt;p>Details about the existing source image on which to install the software product.&lt;/p>"
        },
        "SnsTopicArn":{
          "shape":"String",
          "documentation":"&lt;p>The full ARN of the SNS topic that will be notified when the build status changes.&lt;/p>"
        },
        "Status":{
          "shape":"BuildStatus",
          "documentation":"&lt;p>Current status of the build. Possible build statuses include the following:&lt;/p> &lt;ul> &lt;li> &lt;p>InProgress - A new build has been defined and started.&lt;/p> &lt;/li> &lt;li> &lt;p>InternalError - The build was terminated due to a retryable error.&lt;/p> &lt;/li> &lt;li> &lt;p>Failed - The build has failed and a new image has not been created.&lt;/p> &lt;/li> &lt;li> &lt;p>Succeeded - The build has finished and a new image has been created.&lt;/p> &lt;/li> &lt;/ul>"
        },
        "StandardOutputUrl":{
          "shape":"String",
          "documentation":"&lt;p> A presigned S3 URL to the logs emitted by the installer on STDOUT during install process.&lt;/p>"
        },
        "StandardErrorUrl":{
          "shape":"String",
          "documentation":"&lt;p> A presigned S3 URL to the logs emitted by the installer on STDERR during install process.&lt;/p>"
        },
        "ErrorDetail":{"shape":"ErrorDetail"},
        "StartTime":{
          "shape":"DateTime",
          "documentation":"&lt;p>Time stamp indicating when the build was created, in ISO 8601 format.&lt;/p>"
        },
        "LastUpdateTime":{
          "shape":"DateTime",
          "documentation":"&lt;p>Time stamp indicating when the build was last updated, in ISO 8601 format.&lt;/p>"
        }
      },
      "documentation":"&lt;p>Container for the properties describing each build that meets the filter requirements.&lt;/p>"
    },
    "BuildLimitExceededException":{
      "type":"structure",
      "members":{
        "Message":{"shape":"String"}
      },
      "documentation":"&lt;p>This exception is thrown when the number of concurrent builds exceeds the maximum allowed.&lt;/p>",
      "exception":true
    },
    "BuildList":{
      "type":"list",
      "member":{"shape":"Build"}
    },
    "BuildStatus":{
      "type":"string",
      "enum":[
        "InProgress",
        "InternalError",
        "Failed",
        "Succeeded"
      ]
    },
    "DateTime":{"type":"timestamp"},
    "DescribeBuildsRequest":{
      "type":"structure",
      "members":{
        "NextToken":{
          "shape":"NextToken",
          "documentation":"&lt;p>(Optional) Token that indicates the start of the next sequential page of results. Use the token that is returned with a previous call to this action. To specify the start of the result set, do not specify a value.&lt;/p>"
        },
        "MaxResults":{
          "shape":"MaxResults",
          "documentation":"&lt;p>(Optional) An upper limit on the number of build descriptions that can be returned.&lt;/p>"
        },
        "Filters":{
          "shape":"FilterList",
          "documentation":"&lt;p>(Optional) One or more filters. Possible values are:&lt;/p> &lt;ul> &lt;li> &lt;p>build-id - A unique identifier which refers to a particular build.&lt;/p> &lt;/li> &lt;li> &lt;p>fulfillment-option-id - A fulfillment option identifier which refers to a set of builds.&lt;/p> &lt;/li> &lt;li> &lt;p>product-id - A product identifier which refers to a set of builds.&lt;/p> &lt;/li> &lt;li> &lt;p>status - Build status (in-progress | internal-error | failed | succeeded) which refers to a set of builds.&lt;/p> &lt;/li> &lt;/ul>"
        }
      },
      "documentation":"&lt;p>Container for request parameters to the DescribeBuilds operation.&lt;/p>"
    },
    "DescribeBuildsResult":{
      "type":"structure",
      "members":{
        "NextToken":{
          "shape":"NextToken",
          "documentation":"&lt;p>Token that indicates the start of the next sequential page of results.&lt;/p>"
        },
        "Builds":{
          "shape":"BuildList",
          "documentation":"&lt;p>List of builds, which hold properties describing each build that meets the filter requirements.&lt;/p>"
        }
      },
      "documentation":"&lt;p>Container for the result of the DescribeBuilds operation.&lt;/p>"
    },
    "DestinationImage":{
      "type":"structure",
      "members":{
        "Id":{
          "shape":"String",
          "documentation":"&lt;p>The id of the new image on which the software product has been installed.&lt;/p>"
        },
        "Description":{
          "shape":"String",
          "documentation":"&lt;p>A description for the new image to be created in the same region.&lt;/p>"
        },
        "Name":{
          "shape":"String",
          "documentation":"&lt;p>A name for the new image.&lt;/p> &lt;p>Constraints: 3-128 alphanumeric characters, parentheses (()), square brackets ([]), spaces ( ), periods (.), slashes (/), dashes (-), single quotes ('), at-signs (@), or underscores(_)&lt;/p>"
        }
      },
      "documentation":"&lt;p>Details about the new image to be created in the same region.&lt;/p>"
    },
    "ErrorCode":{
      "type":"string",
      "documentation":"&lt;ul> &lt;li> &lt;p>SSMAgentNotFound - Error code representing condition when either SSM agent was not running on the instance or was unreachable.&lt;/p> &lt;/li> &lt;li> &lt;p>InstallFailed - Error code representing condition when installtion timed out or exited with non zero return value.&lt;/p> &lt;/li> &lt;/ul>",
      "enum":[
        "SSMAgentNotFound",
        "InstallFailed"
      ]
    },
    "ErrorDetail":{
      "type":"structure",
      "members":{
        "Code":{
          "shape":"ErrorCode",
          "documentation":"&lt;p>Error code providing specific detail on the error.&lt;/p>"
        },
        "Message":{
          "shape":"String",
          "documentation":"&lt;p>Error message providing specific detail on the error.&lt;/p>"
        }
      },
      "documentation":"&lt;p>A container for error code and an error message.&lt;/p>"
    },
    "Filter":{
      "type":"structure",
      "members":{
        "Name":{
          "shape":"String",
          "documentation":"&lt;p>The name of the filter. Filter names are case-sensitive.&lt;/p>"
        },
        "Values":{
          "shape":"StringList",
          "documentation":"&lt;p>One or more filter values. Filter values are case-sensitive.&lt;/p>"
        }
      },
      "documentation":"&lt;p>A filter name and value pair that is used to return a more specific list of results. Filters can be used to match a set of resources by various criteria, such as tags, attributes, or ids.&lt;/p>"
    },
    "FilterList":{
      "type":"list",
      "member":{"shape":"Filter"}
    },
    "IdempotentParameterMismatchException":{
      "type":"structure",
      "members":{
        "Message":{"shape":"String"}
      },
      "documentation":"&lt;p>This exception is thrown when an idempotent operation is retried and the parameters do not match the original call with the same idempotency token.&lt;/p>",
      "exception":true
    },
    "InstallerMismatchException":{
      "type":"structure",
      "members":{
        "Message":{"shape":"String"}
      },
      "documentation":"&lt;p>This exception is thrown when the specified fulfillment option id is not compatible with the platform of the specified source image id.&lt;/p>",
      "exception":true
    },
    "InternalServerErrorException":{
      "type":"structure",
      "members":{
        "Message":{"shape":"String"}
      },
      "documentation":"&lt;p>This exception is thrown on an internal server error.&lt;/p>",
      "exception":true,
      "fault":true
    },
    "InvalidDestinationImageNameException":{
      "type":"structure",
      "members":{
        "Message":{"shape":"String"}
      },
      "documentation":"&lt;p>This exception is thrown when the specified destination image name does not meet the constraints.&lt;/p>",
      "exception":true
    },
    "InvalidFilterException":{
      "type":"structure",
      "members":{
        "Message":{"shape":"String"}
      },
      "documentation":"&lt;p>This exception is thrown when the specified filter does not exist.&lt;/p>",
      "exception":true
    },
    "InvalidFulfillmentOptionIdException":{
      "type":"structure",
      "members":{
        "Message":{"shape":"String"}
      },
      "documentation":"&lt;p>This exception is thrown when the specified fulfillment option id does not exist.&lt;/p>",
      "exception":true
    },
    "InvalidMaxResultsException":{
      "type":"structure",
      "members":{
        "Message":{"shape":"String"}
      },
      "documentation":"&lt;p>This exception is thrown when the specified value for maximum number of results to be returned is not valid.&lt;/p>",
      "exception":true
    },
    "InvalidNextTokenException":{
      "type":"structure",
      "members":{
        "Message":{"shape":"String"}
      },
      "documentation":"&lt;p>This exception is thrown when the specified next token is not valid.&lt;/p>",
      "exception":true
    },
    "InvalidSnsTopicArnException":{
      "type":"structure",
      "members":{
        "Message":{"shape":"String"}
      },
      "documentation":"&lt;p>This exception is thrown when the specified SNS topic ARN does not exist.&lt;/p>",
      "exception":true
    },
    "InvalidSourceImageIdException":{
      "type":"structure",
      "members":{
        "Message":{"shape":"String"}
      },
      "documentation":"&lt;p>This exception is thrown when the specified source image id does not exist.&lt;/p>",
      "exception":true
    },
    "MaxResults":{
      "type":"integer",
      "max":256,
      "min":0
    },
    "NextToken":{
      "type":"string",
      "max":1024,
      "min":1
    },
    "Product":{
      "type":"structure",
      "members":{
        "Id":{
          "shape":"String",
          "documentation":"&lt;p>The id of the Marketplace software product to install on the image. This field is populated by Marketplace.&lt;/p>"
        },
        "Version":{
          "shape":"String",
          "documentation":"&lt;p>The version of the Marketplace software product to install on the image. This field is populated by Marketplace.&lt;/p>"
        },
        "Title":{
          "shape":"String",
          "documentation":"&lt;p>The title of the Marketplace software product to install on the image. This field is populated by Marketplace.&lt;/p>"
        }
      },
      "documentation":"&lt;p>Details about the Marketplace software product to install on the image. This structure is populated by Marketplace.&lt;/p>"
    },
    "ProductList":{
      "type":"list",
      "member":{"shape":"Product"}
    },
    "SourceImage":{
      "type":"structure",
      "members":{
        "Id":{
          "shape":"String",
          "documentation":"&lt;p>The id of the existing source image.&lt;/p>"
        },
        "Name":{
          "shape":"String",
          "documentation":"&lt;p>The name of the existing source image.&lt;/p>"
        }
      },
      "documentation":"&lt;p>Details about the existing source image on which to install the software product&lt;/p>"
    },
    "StartBuildRequest":{
      "type":"structure",
      "required":[
        "FulfillmentOptionIds",
        "SourceImageId",
        "DestinationImageName"
      ],
      "members":{
        "ClientToken":{
          "shape":"String",
          "documentation":"&lt;p>(Optional) Unique, case-sensitive identifier you provide to ensure idempotency of the request. We recommend UUID.&lt;/p>",
          "idempotencyToken":true
        },
        "FulfillmentOptionIds":{
          "shape":"StringList",
          "documentation":"&lt;p>List of fulfillment option ids of Marketplace software products to install on the image.They need to be retrieved from the Marketplace Website.&lt;/p>"
        },
        "SourceImageId":{
          "shape":"String",
          "documentation":"&lt;p>The id of the image on which to install the software product.&lt;/p>"
        },
        "DestinationImageName":{
          "shape":"String",
          "documentation":"&lt;p>A name for the new image.&lt;/p> &lt;p>Constraints: 3-128 alphanumeric characters, parentheses (()), square brackets ([]), spaces ( ), periods (.), slashes (/), dashes (-), single quotes ('), at-signs (@), or underscores(_)&lt;/p>"
        },
        "DestinationImageDescription":{
          "shape":"String",
          "documentation":"&lt;p>(Optional) A description for the new image in the same region.&lt;/p>"
        },
        "SnsTopicArn":{
          "shape":"String",
          "documentation":"&lt;p>(Optional) The full ARN of the SNS Topic that will be notified when the build status changes.&lt;/p>"
        }
      },
      "documentation":"&lt;p>Container for request parameters to the StartBuild operation.&lt;/p>"
    },
    "StartBuildResult":{
      "type":"structure",
      "members":{
        "BuildId":{
          "shape":"String",
          "documentation":"&lt;p>Unique identifier for the started build.&lt;/p>"
        },
        "Products":{
          "shape":"ProductList",
          "documentation":"&lt;p>Details about the Marketplace software products to install on the image. This structure is populated by Marketplace.&lt;/p>"
        }
      },
      "documentation":"&lt;p>Container for the result of the StartBuild operation.&lt;/p>"
    },
    "String":{"type":"string"},
    "StringList":{
      "type":"list",
      "member":{"shape":"String"}
    },
    "UnauthorizedOperationException":{
      "type":"structure",
      "members":{
        "Message":{"shape":"String"}
      },
      "documentation":"&lt;p>This exception is thrown when the IAM principal referred to by the request credentials does not have appropriate permissions.&lt;/p>",
      "exception":true
    }
  },
  "documentation":"&lt;fullname>AWS Marketplace Image Build Service&lt;/fullname> &lt;p>AWS Marketplace customers can use this API to build new images and to retrieve information about all of their builds.&lt;/p>"
}
```

 **Command** 

```
$ aws configure add-model --service-model file:<insert path to
      marketplaceimagebuild-2017-12-15.normal.json> --service-name
      marketplaceimagebuild
```

 To start a build, execute the following code\. 

```
$ aws marketplaceimagebuild start-build \
      --input-fulfillment-option-ids "fo-ids4xf7qagwyc" \ 
      --input-image-id ami-58d7e821 \ 
      --output-image-name "ubuntu-ami" \ 
      --output-image-description "Ubuntu" \ 
      --input-instance-type "m4.xlarge" \ 
      --output-installation-log-s3-bucket-name "ssm-logs-641549025415" \ 
      --input-automation-role SSMAutomationRole \ 
      --input-instance-profile SSMInstanceRole 
      --region eu-west-1
{
    "BuildId": "d33cffa8-b49a-42b7-b98b-54c41ca26b3a",
    "Status": "InProgress"
}
```

 To describe a build, execute the following code\. 

```
$ aws marketplaceimagebuild describe-builds --build-ids "1f84f17b-35c6-4e5b-9170-c98f279c6345" --region=us-west-2
{"Builds": 
  [
    {"BuildId": "1f84f17b-35c6-4e5b-9170-c98f279c6345", 
     "InputFulfillmentOptions": 
      [
        {"Id": "fo-ids4xf7qagwyc", 
         "Product": 
          {"Title": "Test Ubuntu product", 
           "Version": "Test 1.0"}
        }
      ], 
     "InputImage": 
      {"Id": "ami-86743afe", 
       "Name": "Ubuntu 16.04"}, 
     "LastUpdateTime": 1529960569.43, 
     "OutputImage": 
      {"Description": "Ubuntu 16.04", 
       "Name": "Ubuntu"}, 
     "OutputInstallationLogS3BucketName": "ssm-logs-s3-bucket", 
     "StartTime": 1529960569.43, 
     "Status": "InProgress"}, 
  ]
}
```

 To access documentation, execute the following command\. 

```
$ aws marketplaceimagebuild help
```

## Using the AWS SDK for Java<a name="using-the-aws-sdk-for-java"></a>

 To install the AWS SDK for Java: 

1.  Download the [AWS SDK for Java](https://aws.amazon.com/sdk-for-java/)\. 

1.  Create a new project using your IDE and add the AWS SDK for Java JAR as a library\. 

1.  Verify that everything is linked correctly by calling an existing AWS service\. 

1.  Download the JAR and add it as a library to your project\. 

1.  Verify that you can call AWSMarketplaceImageBuild\. 