# AMI product checklist<a name="aws-marketplace-listing-checklist"></a>

Before submitting your AMI product request to AWS Marketplace, review this checklist\. Validating this information will help to make sure your submission goes through the publication process smoothly\. 

 Product usage: 
+ Your AMI must be production\-ready\. 
+ Your AMI can't restrict product usage by time or any other measurements\. 
+ Your AMI must be compatible with the 1\-Click fulfillment experience\. 
+ Everything required to use the product is in the software, including client applications\. 
+ The default user uses a randomized password, or creating the initial user requires verification that the buyer is authorized to use the instance using a value unique to the instance such as instance ID\.

 For free or paid products:
+ No additional license is required to use the product\. 
+ The buyer doesn't have to provide personally identifiable information \(for example, their email address\) to use the product\.

AMI preparation:
+ Uses HVM virtualization and 64\-bit architecture 
+ Doesn't contain any known vulnerabilities, malware or viruses 
+ Buyers have OS\-level administration access to the AMI 
+ Run your AMI through AMI Self\-Service Scanning 

 For Windows AMIs:
+ Uses the most recent version of [EC2ConfigService](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/ec2config-service.html) 
+ `Ec2SetPassword`, `Ec2WindowsActivate`, and `Ec2HandleUserData` are enabled in your AMI
+ No guest accounts or remote desktop users are present 

 For Linux AMIs: 
+ Root login is locked or disabled 
+ No authorized keys, default passwords, or other credentials are included 

Product Load Form or Product tab
+ All required fields are completed 
+ All values are within specified character limits 
+ All URLs load without error 
+ The product image is at least 110 pixels wide and between a 1:1 and 2:1 ratio 
+ Pricing is specified for all enabled instance types \(for hourly, hourly\-based monthly pricing, and hourly\-based annual pricing models\) 
+ Monthly pricing is specified \(for hourly\-based monthly and monthly pricing models\) 