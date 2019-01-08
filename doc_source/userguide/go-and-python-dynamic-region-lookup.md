# Go Dynamic Region Lookup<a name="go-and-python-dynamic-region-lookup"></a>

 The following are examples for how to query the AWS Region from Amazon EC2 instance metadata using Go and Python\. 

## Go Dynamic Region Lookup<a name="go-dynamic-region-lookup"></a>

The following example shows how to query the AWS Region from Amazon EC2 instance metadata\. 

```
// Obtains region from EC2 instance metadata endpoint
// See: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html
func getAwsRegion(sess *session.Session) string {
   svc := ec2metadata.New(sess)
   region, err := svc.Region()
   if err != nil {
      panic(fmt.Errorf("Could not load AWS Region from ec2 instance metadata: %v", err))
   }
   return region
}
```

## Python Dynamic Region Lookup<a name="python-dynamic-region-lookup"></a>

 The following example code snippet shows how to query the AWS Region from Amazon EC2 instance metadata\.

```
def getAwsRegion():
    instanceMetaDataResp = \
        requests.get("http://169.254.169.254/latest/dynamic/instance-identity/document")
    responseData = instanceMetaDataResp.json()

    json_response = json.dumps(responseData)
    instanceMetaDataJson = json.loads(json_response)
    return instanceMetaDataJson["region"]
```