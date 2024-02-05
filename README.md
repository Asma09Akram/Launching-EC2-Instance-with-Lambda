## AWS LAMBDA

AWS Lambda is a serverless compute service. We run code without provisioning or managing servers, creating workload-aware cluster scaling logic, maintaining event integrations, or managing runtimes. 
Run code for virtually any type of application or backend service. Just upload your code as a ZIP file or container image, 
and Lambda automatically allocates compute execution power and runs your code based on the incoming request or event, for any scale of traffic.
Write Lambda functions in your favorite language (Node.js, Python, Go, Java, and more) and use both serverless and container tools, such as AWS SAM or Docker CLI, to build, test, and deploy your functions.


The architecture diagram of this tutorial is given below.

![EC2 Basics](https://github.com/Asma09Akram/Launching-EC2-Instance-with-Lambda/assets/124654068/e5fc8696-7397-477b-8d57-e90f89d81406)

Here in this tutorial we learn how we launch an EC2 instance using AWS Lambda.

Prerequisities:
* Create an IAM Role with any name and give EC2 full access to that role. This role will be assumed by Lambda function to launch the instance.
* Create an AMI and copy the AMI id and paste it in the code which we are going to use in Lambda function.
  
Following are the steps we have followed in this tutorial.
Step 1. Sign in to AWS Management Console
Step 2. We will create a Lambda function and will add the code which will create EC2 instance when we manually trigger Lambda function .
Step 3. We will then configure a Test Event.
Step 4. We will now provision an EC2 Instance using a Lambda Function.
Step 5. We will now verify that EC2 instance is launched successfully or not.

