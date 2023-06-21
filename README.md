# Real-Time Image Captioning Model Example

This example uses CloudKommand to deploy an Lambda-hosted image captioning machine learning model and then uses AWS S3, DynamoDB, and IAM to host an real-time image captioning model that triggers when you drop an image in the S3 bucket, creating a prediction in the Lambda-hosted model, and storing that prediction in a DynamoDB record. 

A few notes:
The cold start on a lambda function this big is several minutes. By the third call however, it should take maybe a second or two to get a caption for JPEG or PNG images provided. To avoid the 0.1% of calls that would hit this problem, either provision concurrency (the more expensive option, but viable for client-facing apis) or create a Cloudwatch Event to ping the lambda every few minutes to "keep it warm."

Use the kommand.json at the base level of this repo, combined with the folder structure, to develop your own application, and check out the CloudKommand-managed plugins at:

- IAM (role and policy): https://github.com/cloudkommand/iam 
- Lambda (function and layer): https://github.com/cloudkommand/lambda
- S3: https://github.com/cloudkommand/s3
- DynamoDB: https://github.com/cloudkommand/dynamodb