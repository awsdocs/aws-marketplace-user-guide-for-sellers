# Error Messages<a name="private-image-build-error-messages"></a>

 Use the following table to troubleshoot error messages that you might receive during the build process\. 


|  **Error**  |  **Explanation**  | 
| --- | --- | 
|  InternalServerErrorException  |  The AWS Marketplace Private Image Build Service failed to initiate the custom build\. This might be an intermittent error\. Try again or contact AWS Support if the problem persists\.  | 
|  BuildLimitExceededException  |  You have exceeded the maximum number of concurrent builds\. Wait until one or more of your builds has completed before starting another one\.  | 
|  IdempotentParameterMismatchException  |  The client token and the request differ from the previous request associated with the client token\.  | 
|  InstallerMismatchException  |  The software that you're installing doesn't match the operating system of the base AMI that you selected\. Verify the technical requirements and try again\.  | 
|  InvalidFulfillmentOptionIdException  |  The fulfillment option for the private image that you selected isn't valid\. The option that you entered might not exist or might not be valid in the region that you selected\. Try again or contact AWS Support if the problem persists\.  | 
|  InvalidSourceImageIdException  |  You selected an invalid base AMI\. Verify that the image isn't encrypted and doesn't already have AWS Marketplace software installed\.  | 
|  InvalidDestinationImageNameException  |  The name for the private image doesn't meet the Amazon EC2 guidelines for naming an AMI\. Use a different name and try again\.  | 
|  InvalidDestinationImageDescriptionException  |  The description that you provided exceeds the length limit of 255 characters\.  | 
|  InvalidInstallationLogBucketException  |  The Amazon S3 bucket you provided is not a valid S3 bucket, or the IAM instance role doesn't have permissions to access the S3 bucket\.  | 
|  InvalidSnsTopicArnException  |  The Amazon SNS topic that you provided is not a valid SNS topic\.  | 
|  InvalidNextTokenException  |  The expected NextToken for the process was different from what the process expected\.  | 
|  InvalidMaxResultsException  |  The number of requested builds is invalid\.  | 
|  InvalidFilterException  |  The only allowed filter is FulfillmentOptionID\.  | 
|  UnauthorizedOperationException  |  You don't have permission to perform this operation\. Verify that the AWS account owner has granted you the appropriate permissions\.  | 
|  InvalidSubnetException  |  The subnet that you defined for the VPC is invalid\.  | 
|  InvalidSecurityGroupException  |  The security group that you provided is incorrect\.  | 
|  SubscriptionNotFoundException  |  You aren't subscribed to the product\.  | 
|  InvalidBuildIdException  |  One or both of the following conditions are met: there are duplicate build IDs, and/or the number of build IDs is not between 1 and 50\.  | 
|  BuildIdNotFoundException  |  The build ID that you provided can't be found\.  | 
|  InvalidRoleException  |  The IAM automation role doesn't exist or isn't configured with the proper permissions to use AWS Marketplace Private Image Build\.  | 
|  InvalidInstanceProfileException  |  The IAM profile isn't configured with the proper permissions to use the AWS Marketplace Image Building Service\.  | 
|  OutputImageTagsValidationException  |  The Amazon EC2 instance tags are invalid\. Review the guidelines for adding tags to EC2 instances\.  | 
|  InvalidInstanceTypeException  |  The Amazon EC2 instance type defined is invalid for this product\.  | 