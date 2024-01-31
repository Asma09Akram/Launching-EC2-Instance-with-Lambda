### Task 1 Login to AWS Management Console
### Task 2 Create a Lambda Function
2.1 Click on Create a function, select Author from Scratch

![image](https://github.com/Asma09Akram/Launching-EC2-Instance-with-Lambda/assets/124654068/bd404aab-5bf1-4123-acb8-195ac8653ed3)

2.2 Give the name as "MyEC2LambdaFunction" and Select Python 3.8

![image](https://github.com/Asma09Akram/Launching-EC2-Instance-with-Lambda/assets/124654068/4463e7c1-b8b6-412a-b311-4dbb82d0cfa0)

2.3 Choose myrole 

![image](https://github.com/Asma09Akram/Launching-EC2-Instance-with-Lambda/assets/124654068/e9b867d7-22fd-4a4e-9b8f-dfcbfe26fe4c)


2.4 We need to configure our lambda function. If you scroll down, you can see the Code source section. Here we need to write some Python code to provision an EC2 instance.
You will be using boto3 SDK for AWS to write the python code. Remove the existing code in the lambda_function.py file. Copy the below code and paste it into your lambda_function.py file.

```
import json
import boto3
import time
from botocore.exceptions import ClientError

def lambda_handler(event, context):
    # Provision and launch the EC2 instance
    ec2_client = boto3.client('ec2')
    try:
        response = ec2_client.run_instances(
            ImageId='ami-0b69ea66ff7391e80',
            InstanceType='t2.micro',
            MinCount=1,
            MaxCount=1
        )
        print(response['Instances'][0], "EC2 Instance Created")
        return {
            'statusCode': 200,
            'body': json.dumps("success")
        }
    except ClientError as e:
        print("Detailed error: ", e)
        return {
            'statusCode': 500,
            'body': json.dumps("error")
        }
    except Exception as e:
        print("Detailed error: ", e)
        return {
            'statusCode': 500,
            'body': json.dumps("error")
        }		

```

![image](https://github.com/Asma09Akram/Launching-EC2-Instance-with-Lambda/assets/124654068/e21c8509-0b47-46b6-b354-e7cb09d6c622)

2.5 Click on Deploy button.

![image](https://github.com/Asma09Akram/Launching-EC2-Instance-with-Lambda/assets/124654068/e417ca7b-c641-4011-b8be-38ac1164a94f)


2.6  Click on Configuration to see General configuration, and click on the Edit button
In the Timeout set seconds as 6 and then click on the Save button.

![image](https://github.com/Asma09Akram/Launching-EC2-Instance-with-Lambda/assets/124654068/ba8412ab-da40-4f1e-a845-8c001a8e56f6)

### Task 3: Configure a Test Event
3.1 Click on the Test button.

In Configure test event page,

Event Name: Enter EC2

Leave other fields as default.

Click on Save button

![image](https://github.com/Asma09Akram/Launching-EC2-Instance-with-Lambda/assets/124654068/dedc1c05-fb19-41b7-8693-fffc3f15d30c)


### Task 4: Provision an EC2 Instance using a Lambda Function

Once the EC2 is configured, we can trigger the lambda manually using this simple test.

Click on the Test button. 

The lambda function now gets executed and an EC2 instance will be provisioned.

Once it's completed, you will be seeing a success message similar to the example shown below. It will display details such as:

Duration : Lambda execution time.

Log Output: Details of the EC2 instance provisioned.

etc...

![image](https://github.com/Asma09Akram/Launching-EC2-Instance-with-Lambda/assets/124654068/08d7a761-e2b4-44b6-bc62-2b1b87e30ee6)


### Task 5: Check that the EC2 instance launched successfully

Navigate to the EC2 page from the services menu.

Go to Instances in the left menu.

Please wait until the ec2 instance is in a running state

![image](https://github.com/Asma09Akram/Launching-EC2-Instance-with-Lambda/assets/124654068/4d0a51aa-406b-4048-b21d-64187971b03c)
