# AWS CloudFormation - Rabbit MQ Deployment

This CloudFormation template creates an **Amazon Rabbit MQ Broker** with the following components:
- **Broker**: MQ Broker.
- **Security Group**: Secures access to the broker.
- **User**: User configuration to access the Console and broker.

## Features
- **Auto-Maintenance**: Auto maintanence of the broker.
- **Security Groups**: Configures security to allow access only from trusted sources.

## Architecture
The stack consists of:
1. **MQ Broker**: An RabbitMQ broker.
2. **Security Group**: Allows access only to the necessary ports.

## Prerequisites
- AWS CLI or access to AWS Console.
- IAM permissions to create resources.

## Deployment Instructions

### 1. Deploy the CloudFormation Stack

#### Using AWS Console
1. Navigate to the [AWS CloudFormation Console](https://console.aws.amazon.com/cloudformation/).
2. Click on **Create Stack** and choose **With new resources (standard)**.
3. Upload the CloudFormation template (e.g., `cftemplate.json`) or provide the template URL.
4. Provide the necessary parameters if you want to override.
5. Click **Next**, configure stack options as needed, and proceed to **Create Stack**.

#### Using AWS CLI
You can also create the stack using the AWS CLI:
```bash

aws cloudformation create-stack --stack-name app-rabbitmq-cluster --template-body file://cftemplate.json --capabilities CAPABILITY_NAMED_IAM --profile  my-profile 

- If you want to override the parameters from commandline, use below syntax
aws cloudformation create-stack --stack-name appecscluster  --parameters ParameterKey=BrokerName,ParameterValue=RabbitMqBroker \
               ParameterKey=EngineVersion,ParameterValue=3.12.13 \
               ParameterKey=HostInstanceType,ParameterValue=mq.t3.micro --template-body file://cftemplate.json --capabilities CAPABILITY_NAMED_IAM --profile  my-profile 


