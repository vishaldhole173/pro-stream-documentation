# Deployment

You can deploy Visionstream into your local network infrastructure, or extend your infrastructure to include VisionStream.

## Overview

By following the provided scripts and methodology, we have simplified the process of installing a comprehensive solution that enables the creation and management of live streams and broadcast channels within your local network.

## Components

Following are the AWS services used in the VisionStream -

* MediaLive 
* MediaPackage 
* CloudFront 
* SQS
* IVS
* S3
* EventBridge
* Rules
* MediaConvert
* Lambda
* Lambda@Edge
* CloudWatch
* CloudFormation
* RDS
* System Manager - Parameter Store
* EC2
* Elastic Beanstalk
* Load Balancers
* IP addresses
* VPC
* Route53

## Prerequisites

Before deploying VisionStream using the deployment scripts, the following prerequisites need to be met: 

* AWS Account 
  - Ensure you have access to an AWS account with the necessary permissions to create and manage AWS resources. 
* AWS CLI 
  - Install the AWS Command Line Interface (CLI) on your local machine. You can download and install the CLI from the official AWS CLI documentation. 
* Node.js 
  - Ensure Node.js is installed on your local machine. You can download and install Node.js from the official Node.js website. 
* Configuration 
  - Set up the AWS CLI with your AWS credentials by running the aws configure command and providing your Access Key ID, Secret Access Key, default region, and output format. 
* Parameter Values 
  - Prepare the necessary parameter values for the deployment. Review the parameters JSON file for the respective environment and ensure the values are correctly set for the deployment. 
* Environment Variables 
  - Set the required environment variables.

## Tools

To deploy the VisionStream app using the provided scripts, you will utilize the following tools - 

* AWS CLI (Command Line Interface) 
  - The AWS CLI allows you to interact with various AWS services from the command line. It is used to deploy AWS CloudFormation stacks and manage AWS resources. 
* Node.js 
  - Node.js is a JavaScript runtime that allows you to run JavaScript on the server-side. It is used to run the VisionStream app on a t2.micro server.
* Bash Shell 
  - The deployment scripts are written in Bash, a popular Unix shell and command language. You will need a Bash-compatible shell to run the deployment scripts. Most Linux distributions come with Bash pre-installed. For Windows users, you can use Git Bash or Windows Subsystem for Linux (WSL) to execute the scripts. 
* Text Editor 
  - You will need a text editor to review and modify the deployment scripts or configuration files. Popular text editors include Visual Studio Code, Sublime Text, Atom, or Notepad++.

## Deploying the Infrastructure

To deploy the VisionStream infrastructure, follow these steps -  

* Ensure that you have completed the prerequisites mentioned earlier, including setting up the necessary tools and configurations. 
* Access the deployment scripts and navigate to the appropriate directory. 
* Review the build.sh script and modify it if required, ensuring that the necessary parameters are correctly set for the desired environment. 
* Open a terminal or command prompt and navigate to the directory containing the deployment scripts. 
* Run the deployment script with the appropriate parameters for the desired environment. For example, to deploy the test environment in the us-east-1 region, execute the following command:

  `bash scripts/deployment/build.sh test us-east-1r`
  
* Monitor the deployment process as the script executes. It will create the required AWS resources and configure them according to the provided parameters. 
* Once the script completes successfully, the VisionStream infrastructure should be deployed in the specified environment. 
* Verify that the infrastructure has been created by checking the AWS Management Console or using AWS CLI commands to inspect the resources.

## Verifying the deployment

To verify the deployment of the VisionStream infrastructure, follow these steps - 

* Access the deployed VisionStream application using the appropriate endpoint or URL. This information can be obtained from the deployment process or documentation.

* Ensure that the VisionStream app is accessible and loads without errors or issues. Open it in a web browser or use the provided client application.

* Test the functionality of the VisionStream app by performing various actions and interactions, such as creating live streams, managing broadcast channels, and viewing live content.

* Verify that the app is able to handle user interactions correctly and that the expected features and functionalities are working as intended.

* Test the end-to-end streaming process by starting a live stream and verifying that the stream is properly broadcast and accessible to viewers.

* Monitor the system behavior and performance during usage to ensure that it meets the desired requirements. Pay attention to any errors, latency, or unexpected behavior.

* Validate that any integrations or connections with external services, such as MediaLive, MediaPackage, CloudFront, or RDS, are functioning correctly.

* Perform thorough testing across different devices, browsers, and network conditions to ensure the app's compatibility and responsiveness.

* Seek feedback from users or stakeholders to gather their experience and validate that the deployed VisionStream infrastructure meets their expectations.

By following these steps, you can ensure that the VisionStream infrastructure has been successfully deployed and that the app is functioning properly, meeting the desired requirements for livestreaming and broadcast management.

## Deployment Script

```
#!/bin/bash

ENV_TYPE=$1
STACK_NAME=vision-stream-$ENV_TYPE-env

REGION=$2

CF_TEMPLATES_DIR=./infrastructure/cloudformation
BUCKET_NAME_US_WEST_1=vision-stream-rc-builds
BUCKET_NAME=vision-stream-builds-$REGION

cd $CF_TEMPLATES_DIR

aws --region $REGION cloudformation deploy \
    --stack-name ${STACK_NAME} \
    --s3-bucket ${BUCKET_NAME} \
    --s3-prefix cloudformation/templates \
    --template-file templates/visionstream-app-us-west-2.json \
    --parameter-overrides file://parameters/$ENV_TYPE-us-west-2.json \
    --force-upload \
    --no-fail-on-empty-changeset \
    --capabilities CAPABILITY_IAM

aws --region us-west-1 cloudformation deploy \
    --stack-name ${STACK_NAME} \
    --s3-bucket ${BUCKET_NAME_US_WEST_1} \
    --s3-prefix cloudformation/templates \
    --template-file templates/visionstream-app-us-west-1.json \
    --parameter-overrides file://parameters/$ENV_TYPE-us-west-1.json \
    --force-upload \
    --no-fail-on-empty-changeset
```

The purpose of the script is to automate the deployment of the VisionStream infrastructure using AWS CloudFormation. It simplifies the process by allowing the user to provide the environment type and AWS region as arguments.

* #!/bin/bash: This line indicates that the script should be executed using the Bash shell.
* ENV_TYPE=$1: This line assigns the value of the first argument passed to the script to the ENV_TYPE variable. This argument represents the environment type (e.g., "test" or "prod").
* STACK_NAME=vision-stream-$ENV_TYPE-env: This line constructs the stack name by appending the environment type to the base name "vision-stream" and adding "-env" at the end. For example, if the environment type is "test," the stack name will be "vision-stream-test-env".
* REGION=$2: This line assigns the value of the second argument passed to the script to the REGION variable. This argument represents the AWS region where the deployment will take place.
* CF_TEMPLATES_DIR=./infrastructure/cloudformation: This line sets the path to the directory containing the CloudFormation templates relative to the script's location.
* BUCKET_NAME_US_WEST_1=vision-stream-rc-builds: This line sets the name of the S3 bucket where CloudFormation templates are stored for the us-west-1 region.
* BUCKET_NAME=vision-stream-builds-$REGION: This line constructs the name of the S3 bucket for the specified region by appending the region name to the base name "vision-stream-builds-".
* cd $CF_TEMPLATES_DIR: This line changes the current directory to the CloudFormation templates directory.
* aws --region $REGION cloudformation deploy : This line invokes the AWS CLI to deploy the CloudFormation stack.
  - `--region $REGION`: Specifies the AWS region to deploy the stack.
  - `--stack-name ${STACK_NAME}`: Sets the name of the CloudFormation stack.
  - `--s3-bucket ${BUCKET_NAME}`: Specifies the S3 bucket where the CloudFormation template is uploaded.
  - `--s3-prefix cloudformation/templates`: Sets the prefix for the CloudFormation templates in the S3 bucket.
  - `--template-file templates/visionstream-app-us-west-2.json`: Specifies the path to the CloudFormation template file for the given region.
  - `--parameter-overrides file://parameters/$ENV_TYPE-us-west-2.json`: Provides the path to the parameter overrides file specific to the environment type and region.
  - `--force-upload`: Forces the upload of the CloudFormation template to the S3 bucket.
  - `--no-fail-on-empty-changeset`: Prevents the stack deployment from failing if there are no changes in the template.
  - `--capabilities CAPABILITY_IAM`: Specifies the required IAM capabilities for the CloudFormation deployment.
* aws --region us-west-1 cloudformation deploy: This line deploys the CloudFormation stack in the us-west-1 region using a similar set of parameters as in the previous command. This is an additional deployment for a different region.

The script uses the AWS CLI to deploy the CloudFormation stack in the specified regions, leveraging the CloudFormation templates and parameter overrides specific to the environment type and region. It uploads the templates to the respective S3 buckets and configures the stack deployment options.

## Deployment Steps for VisionStream Infrastructure and Services.

* Create RDS MySQL 5 instance:

  - Determine the desired version of MySQL for the test and prod environments.
  - Log in to the AWS Management Console.
  - Navigate to the Amazon RDS service.
  - Select the appropriate region.
  - Click on "Create database" and choose "MySQL" as the database engine.
  - Specify the necessary configuration details, such as instance size, storage, username, password, etc.
  - Follow the on-screen prompts to complete the RDS instance creation process.

* Deploy Lambda@Edge function to us-east-1 region:

  - The Lambda code for VisionStream is located in the infrastructure/lambdas directory.
  - Ensure that you have the necessary access and permissions to access this directory and its contents.
  - Use the Lambda code provided in this directory for deploying the Lambda functions associated with VisionStream.

  Lambda@Edge functions are only supported in the us-east-1 region, as they are used to extend the capabilities of Amazon CloudFront edge locations.

* IAM Permissions for Lambda@Edge:

  - To create and manage Lambda@Edge functions, you need the appropriate IAM permissions.
  - Ensure that your IAM user or role has the necessary permissions to create and manage Lambda@Edge functions, as well as any associated resources such as IAM roles, CloudWatch logs, or CloudFront distributions.
  - Grant the required IAM permissions to your user or role using the AWS Management Console, AWS CLI, or IAM policies.

* Creating Private/Public Keys:

  - Execute the script responsible for generating the private and public key pairs.
  - The script will use cryptographic algorithms to generate the keys, typically using OpenSSL or a similar tool.
  - Specify the key size and other parameters as needed.
  - Save the generated keys in a secure location for later use in configuring SSL/  TLS certificates or other encryption-related tasks.

* Creating a Trusted Key Group:

  - Run the script that facilitates the creation of a trusted key group.
  - Provide the necessary parameters, such as the key group name and the associated keys.
  - The script will use the AWS CLI or SDKs to create the trusted key group in the desired region.
  - Verify the successful creation of the trusted key group by checking the AWS Management Console or using the AWS CLI commands for listing key groups.

* Using Parameter Store to Read Private Key:

  - Store the private key securely in the AWS Systems Manager Parameter Store.
  - Ensure that you have the necessary permissions to access the Parameter Store and read the private key.
  - Modify the Lambda code or configuration to include the logic for retrieving the private key from the Parameter Store during runtime.
  - Update the Lambda code to utilize the retrieved private key as needed for encryption, decryption, or other relevant tasks.

* Create Route53 hosted zone / SSL certificate:

  - Log in to the AWS Management Console.
  - Navigate to the Amazon Route 53 service.
  - Go to the "Hosted zones" section and click on "Create hosted zone."
  - Enter the desired domain name and configure the DNS settings.
  - Follow the prompts to create the hosted zone.
  - To create an SSL certificate, navigate to the AWS Certificate Manager service and follow the instructions to request and validate the certificate.

* Configure Application Load Balancer and target groups:

  - Determine the desired load balancer configuration (e.g., Application Load Balancer).
  - Log in to the AWS Management Console.
  - Navigate to the EC2 service.
  - Create an Application Load Balancer and configure the necessary settings.
  - Create target groups and associate them with the load balancer.
  - Configure the load balancer listeners, health checks, and routing rules as required.

  Note: Make sure to check the specific configuration requirements for supporting web sockets with the chosen load balancer.

* Populate parameters into AWS parameter store:

  - Log in to the AWS Management Console.
  - Navigate to the AWS Systems Manager service.
  - Go to the "Parameter Store" section and click on "Create parameter."
  - Specify the parameter details, such as name, value, type, and description.
  - Repeat the process for each parameter that needs to be stored.

* Deploy CloudFront stack to desired region:

  - Ensure that the desired region, such as us-west-2, supports the required services:  - MediaLive, MediaPackage, and IVS. Verify this information in the AWS documentation or service availability matrix.
  - Run the CloudFormation deployment script specific to CloudFront with the desired region (us-west-2) as an argument.
  - The script will initiate the CloudFormation stack creation process, which provisions the necessary resources, such as CloudFront distributions, caching configurations, SSL certificates, and any other related components specific to CloudFront.
  - Monitor the CloudFormation stack creation process in the AWS Management Console or through the AWS CLI until it reaches a "CREATE_COMPLETE" status.

* Deploy CloudFormation stack to create EB application:

  - Run the CloudFormation deployment script specific to Elastic Beanstalk (EB) application creation.
  - The script will initiate the CloudFormation stack creation process, which sets up the EB application, including the required EC2 instances, load balancers, security groups, and other related resources.
  - Monitor the CloudFormation stack creation process in the AWS Management Console or through the AWS CLI until it reaches a "CREATE_COMPLETE" status.
  - Once the stack creation is complete, the EB application will be available for use and can be managed through the AWS Management Console or CLI.

* Deploy the current branch to the Elastic Beanstalk environment:

  - Ensure that you have the necessary access credentials and permissions to deploy to the Elastic Beanstalk environment.
  - Navigate to the root directory of your project or repository where the Elastic Beanstalk application is configured.
  - Make sure your current working branch is the branch you want to deploy (e.g., develop).
  - Run the appropriate command to deploy the current branch to the Elastic Beanstalk environment. This command may vary depending on your specific deployment setup.
  - Monitor the deployment process and check the deployment logs for any errors or issues.
  - Once the deployment is complete, verify the changes in the Elastic Beanstalk environment through the AWS Management Console or CLI.
  - Test the deployed application to ensure that it is functioning as expected in the Elastic Beanstalk environment.
