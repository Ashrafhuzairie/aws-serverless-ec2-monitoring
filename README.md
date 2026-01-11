# AWS EC2 Event-Driven Monitoring using EventBridge and Lambda

## 📌 Project Overview

This project demonstrates an **event-driven architecture on AWS** that monitors **Amazon EC2 instance state changes** using **Amazon EventBridge**, triggers an **AWS Lambda function**, and logs execution details to **Amazon CloudWatch**.

---

## 🛠️ AWS Services Used

- Amazon EC2  
- Amazon EventBridge  
- AWS Lambda  
- Amazon CloudWatch  
- IAM  

## 🔄 Implementation Steps (Based on Screenshots)

### Step 1: Navigate AWS Console
From the AWS Console, search for Lambda and open the Lambda service.

<p align="center">
  <img src="docs/images/Project 2 - Step 1.png" width="500" />
</p>

---

### Step 2: View Existing Lambda Functions
Check the Lambda Functions page and verify existing functions.

<p align="center">
  <img src="docs/images/Project 2 - Step 2.png" width="500" />
</p>

---

### Step 3: Create a New Lambda Function

Click Create function and select:
- Author from scratch
- Runtime: Python 3.14
- Architecture: x86_64
  
<p align="center">
  <img src="docs/images/Project 2 - Step 3.png" width="500" />
</p>

---

### Step 4: Configure Lambda Permissions

Attach an existing execution role with permissions to write logs to CloudWatch.

<p align="center">
  <img src="docs/images/Project 2 - Step 4.png" width="500" />
</p>

### Step 5: Lambda Function Overview

After creation, verify the Lambda function overview and confirm the function name.

<p align="center">
  <img src="docs/images/Project 2 - Step 5.png" width="500" />
</p>

### Step 6: Add Lambda Function Code

Edit lambda_function.py to:

- Use boto3 EC2 client
- Retrieve EC2 instance status
- Print instance ID and state information

<p align="center">
  <img src="docs/images/Project 2 - Step 6.png" width="500" />
</p>

### Step 7: Configure Lambda Basic Settings

Set:
- Memory: 128 MB
- Timeout: 3 mins
- Ephemeral storage: 512 MB

<p align="center">
  <img src="docs/images/Project 2 - Step 7.png" width="500" />
</p>

<p align="center">
  <img src="docs/images/Project 2 - Step 8.png" width="500" />
</p>

### Step 8: Access Amazon EventBridge
Navigate to Amazon EventBridge from the AWS Console.

<p align="center">
  <img src="docs/images/Project 2 - Step 9.png" width="500" />
</p>
<p align="center">
  <img src="docs/images/Project 2 - Step 10.png" width="500" />
</p>

<p align="center">
  <img src="docs/images/Project 2 - Step 11.png" width="500" />
</p>

### Step 9: Create EventBridge Rule

Create a new rule with:
- Event bus: default
- Rule name: EC2-Launched
- Rule enabled

<p align="center">
  <img src="docs/images/Project 2 - Step 12.png" width="500" />
</p>

### Step 10: Build Event Pattern

Configure the event pattern:

- Source: aws.ec2
- Detail type: EC2 Instance State-change Notification
- Specific state: running

<p align="center">
  <img src="docs/images/Project 2 - Step 13.png" width="500" />
</p>

<p align="center">
  <img src="docs/images/Project 2 - Step 14.png" width="500" />
</p>

### Step 11: Configure Lambda as Target

Set the target as:
AWS service → Lambda function
Function name: ashraf-lambda-20260106

<p align="center">
  <img src="docs/images/Project 2 - Step 15.png" width="500" />
</p>

### Step 12: Launch an EC2 Instance
1. Navigate to EC2 Dashboard
2. Launch a new EC2 instance:
- AMI: Amazon Linux
- Instance type: t2.micro
- Public IP enabled

<p align="center">
  <img src="docs/images/Project 2 - Step 16.png" width="500" />
</p>
<p align="center">
  <img src="docs/images/Project 2 - Step 17.png" width="500" />
</p>
<p align="center">
  <img src="docs/images/Project 2 - Step 18.png" width="500" />
</p>
<p align="center">
  <img src="docs/images/Project 2 - Step 19.png" width="500" />
</p>

### Step 13: Verify EC2 Instance State
Confirm the instance is in the Running state.

<p align="center">
  <img src="docs/images/Project 2 - Step 20.png" width="500" />
</p>

See the summary of EC2 : 

<p align="center">
  <img src="docs/images/Project 2 - Step 21.png" width="500" />
</p>

### Step 14: Lambda Trigger Execution
The EC2 state change automatically triggers the Lambda function via EventBridge.

<p align="center">
  <img src="docs/images/Project 2 - Step 22.png" width="500" />
</p>

### Step 15: Monitor CloudWatch Logs
Verify Lambda execution logs and metrics in Amazon CloudWatch.

<p align="center">
  <img src="docs/images/Project 2 - Step 23.png" width="500" />
</p>


📊 Monitoring & Observability

- Lambda invocation count and duration tracked via CloudWatch
- EC2 instance details logged automatically
- No manual execution required

✅ Key Learning Outcomes

- Event-driven architecture using Amazon EventBridge
- Serverless compute with AWS Lambda
- EC2 lifecycle monitoring
- CloudWatch logging and observability
- IAM role and permission management
