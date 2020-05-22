# Best practices for sample input data and sample notebooks<a name="best-practices-sample-ml"></a>

It is important that developers, as well as machine learning practitioners, find it easy to try your models and algorithms\. We strongly recommend that you provide the following information with your product\.

1. Ideally **ten** input files, but at the very least one sample input file, attached under your product’s additional information section\. If your model performs multi\-class classification, you should provide at least one sample input file for each of the classes\. This helps your customers understand the input format expected by the model/algorithm\. Being able to see more sample input files helps users perform any necessary transformations on their data before performing inference, giving them the best results from your model

1. At least **one** sample output file corresponding to one of the input files you provided, to be attached under your product’s additional information section\. This helps your customers understand what kind of output to expect before having to go through the subscription process and improves the usability of your listing\.

1. Provide the following information for your algorithms: the training data format, necessary pre\-processing snippet, and specify both optional and mandatory features that can be provided by the user\. Also specify whether the PIPE input mode is supported by the listing along with the input format required for it\. Specify whether distributed training \(more than 1 CPU/GPU instances\) is supported\. For tuning, provide the recommend hyperparameters\.

1. From the usage information section of your models, provide a code snippet that shows data preparation steps and usage of the Invoke\-endpoint \(CLI/Python\) API call to perform inference on the endpoint created from your model\. This is crucial for your customers to know exactly how the payload should be sent\.

   **Example model usage information**
   + Supported content types: image/jpeg, image/png, image/bmp
   + Supported response types: application/json \(default\), image/jpeg
   + Example CLI command:

     ```
     aws sagemaker-runtime invoke-endpoint --endpoint-name "endpoint_name" --body fileb:///img_name.jpeg --accept image/jpeg outfile.jpeg
     ```

   If your models require data pre\-processing, provide the necessary Python code snippet\.

   **Example data preprocessing information**

   ```
   import base64
   image = open('image.jpeg', 'rb')
   image_64_encode = base64.b64encode(image.read()).decode('utf-8')
   #Prepare payload for prediction
   payload="{\"source\": \""+str(image_64_encode)+"\"}"
   ```

1. Attach a sample notebook that demonstrates the end\-to\-end workflow under your product's additional information section\. We recommend that you use the Pyhton SDK, instead of the Boto3 API in your sample notebook\. Keep in mind that a well\-developed sample notebook will make it easy for your customers to try and use your listing successfully Keep the following sample notebook best practices in mind:
   + For algorithms, your sample notebook should demonstrate end\-to\-end training, tuning, model creation, standing up endpoints, as well as how to perform inference and batch transform jobs on the model\.
   + For models, your sample notebook should demonstrate real\-time inference, batch transform job inference, and provide a clear picture of the kind of data that is expected by the model\.

   For an example sample notebook that works in all regions, without entering any parameters or having to look for sample data, see [amazon\_demo\_product](https://github.com/awslabs/amazon-sagemaker-examples/tree/master/aws_marketplace/using_algorithms/amazon_demo_product) on GitHub\.
**Note**  
A lack of training data would prevent your customers from running the notebook successfully\. An under\-developed sample notebook might prevent your customers from using it and hamper adoption\.