# 📧 AWS-Based Notification Scheduler

A **serverless notification system** for educational platforms that allows scheduling emails and real-time personalized alerts using **AWS Lambda**, **EventBridge**, and **SES/SNS**. Designed to notify users about upcoming classes, exam results, and study suggestions based on live performance data.

---

## 🚀 Features

- ✅ Schedule notifications via a frontend or admin dashboard
- ✅ Real-time data fetch before sending
- ✅ Personalized messages based on academic performance
- ✅ Multi-channel delivery (Email, SMS, Push Notifications)
- ✅ Serverless architecture using AWS Lambda
- ✅ Scheduled execution with Amazon EventBridge

---

## 🛠️ Tech Stack

| Component        | Service          |
|------------------|------------------|
| Scheduling       | Amazon EventBridge |
| Execution Logic  | AWS Lambda       |
| Notification     | Amazon SES / SNS / Firebase |
| Storage (Optional) | Amazon DynamoDB / RDS |
| Monitoring       | Amazon CloudWatch |

---

## 🔄 Workflow

1. User schedules a notification from frontend.
2. Schedule is saved and registered with EventBridge.
3. EventBridge triggers a Lambda function at the scheduled time.
4. Lambda fetches the latest performance data.
5. Message is dynamically generated based on data.
6. Notification is sent via SES (Email), SNS (SMS/Push), or FCM.
7. Notification details are logged.

---

## 🖼️ Architecture Diagram

> See `flowchart.png` or import `drawio/diagram.drawio` for a visual flow of the system.

---

## 📦 Setup

### Prerequisites

- AWS Account
- IAM role with Lambda + SES + EventBridge + SNS permissions
- Python 3.x (or Node.js, if applicable)
- AWS CLI configured

### Deployment (Example for Python)

```bash
# Package Lambda Function
zip function.zip lambda_function.py

# Deploy using AWS CLI
aws lambda create-function \
  --function-name sendNotification \
  --runtime python3.9 \
  --handler lambda_function.lambda_handler \
  --role arn:aws:iam::ACCOUNT_ID:role/lambda-execution-role \
  --zip-file fileb://function.zip
