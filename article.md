---
author: "Kyle Jones"
date_published: "September 30, 2024"
date_exported_from_medium: "November 10, 2025"
canonical_link: "https://medium.com/@kyle-t-jones/setting-up-aws-cdk-for-your-projects-713d1d518b9a"
---

# Setting up AWS CDK for your projects The AWS Cloud Development Kit (CDK) lets you create and control your
cloud infrastructure --- creating a simplified and effective way for...

### Setting up AWS CDK for your projects
#### How to get started with CDK, including setting up an AWS account, installing necessary software tools like the AWS CLI and Node.js, choosing a code editor, and configuring the CDK environment
The AWS Cloud Development Kit (CDK) lets you create and control your cloud infrastructure --- creating a simplified and effective way for automatic resource provisioning. CDK aims to simplify cloud development by integrating cloud infrastructure with familiar programming languages such as TypeScript, Python, JavaScript, Java, and C#. To start using the CDK to manage your AWS infrastructure, it is essential to follow the proper steps to set up your environment correctly.

### What you need before starting (AWS account and Software setup)
Before using AWS CDK, you must ensure that you have the necessary components in place. Without these prerequisites, you won't be able to deploy or manage your AWS infrastructure effectively.

**AWS Account Setup**

The most fundamental requirement is an AWS account. This account is the central point of interaction with AWS cloud services, including EC2, Lambda, S3, and many others. If you already have an AWS account, log in and ensure you have access to the services needed for your project. Suppose you don't, sign up for a new account by visiting the AWS sign-up page and completing the necessary information such as email, password, and payment details. AWS offers a Free Tier, which includes various services that allow you to try out their platform without incurring costs for up to a year.

Once the account is created, enable Multi-Factor Authentication (MFA) for additional security. MFA requires an extra code during sign-in, which enhances account security by preventing unauthorized access, even if someone gets hold of your login credentials.

**Setting Up AWS CLI**

The AWS CLI is a powerful tool for managing AWS services through commands in your terminal. CDK heavily relies on the AWS CLI for interacting with AWS services and deploying infrastructure. Installing and configuring the CLI properly is critical to avoid issues later in the process.

To install the CLI for Windows/MacOS go to the AWS CLI documentation and download the appropriate installer for your operating system.

**Linux:** Use your package manager to install the AWS CLI. For example:

``` 
sudo apt install awscli
```

Once the AWS CLI is installed, configure it by running:

``` 
aws configure
```

This command will prompt you to input your AWS Access Key ID, Secret Access Key, default region, and default output format. These credentials are necessary for CDK to interact with AWS on your behalf.

**Node.js Setup**

The AWS CDK is built using Node.js and requires it to function. Even if you use Python, Java, or C#, Node.js is still a mandatory requirement for CDK. Head over to the official Node.js website and install your operating system's long-term support (LTS) version. Once installed, verify the installation by running:

``` 
node --version
npm --version
```

These commands will output the installed versions of Node.js and npm (Node Package Manager).

**Choosing a Code Editor**

Selecting a powerful code editor or Integrated Development Environment (IDE) is essential for improving your development experience. Visual Studio Code (VS Code) is widely recommended due to its comprehensive feature set and support for AWS CDK extensions. VS Code provides useful features such as syntax highlighting, IntelliSense for autocompletion, debugging capabilities, and integrated Git.

To improve your CDK development experience, you can install extensions for AWS, CDK, and specific languages (e.g., TypeScript or Python) directly within VS Code. Popular editors like JetBrains WebStorm or Sublime Text also work well, though VS Code's community support makes it a popular choice.

**Language-Specific Setup**

Although CDK supports several programming languages, installing the specific tools for your preferred language is essential.

For Python, make sure you have pip installed for package management. Additionally, you'll want to set up a virtual environment for each project to isolate dependencies:

``` 
python3 -m venv .env
source .env/bin/activate
```

For Java, ensure you have Maven or Gradle installed. These are widely used for managing dependencies in Java-based CDK projects.

For C#, you'll need .NET Core SDK to build and run C# CDK applications.

These language-specific environments ensure you can seamlessly integrate your code with CDK.

### Installing and Configuring AWS CDK on your local machine
Once you've completed the basic setup, it's time to install and configure AWS CDK on your machine. This process ensures you can start working on your infrastructure as code projects using the CDK framework.

**Installing AWS CDK**

To install AWS CDK, open your terminal and run the following command:

``` 
npm install -g aws-cdk
```

This command installs the AWS CDK globally on your system, making the cdk command available anywhere in your terminal.

After installation, verify that the CDK was installed correctly by running:

``` 
cdk --version
```

This command should return the version of the CDK installed, ensuring that everything is set up correctly.

**Creating a New CDK Project**

After installing CDK, you can create a new CDK project by navigating to your desired project directory and running the following command:

``` 
cdk init app --language typescript
```

This will initialize a new TypeScript-based CDK project with the necessary file structure. If you prefer a different programming language, replace typescript with your chosen language (e.g., Python, Javascript, Java, Csharp). For Python, remember to activate your virtual environment before running this command.

Whats gets created when you initialize a CDK project

**bin**: This directory contains the entry point for your application and the main logic for your CDK app.

**lib**: This directory is where your stacks are defined. CDK stacks contain the infrastructure code that will be deployed.

cdk.**json**: This configuration file helps CDK understand how to run your application, including defining environment variables and project settings.

After creating the project, run the following command to install any additional dependencies:

``` 
npm install
```

**Adding Dependencies**

Depending on the AWS services you plan to use, you may need to install additional CDK libraries. For example, if you're working with S3 buckets, you'll need the \@aws-cdk/aws-s3 library. To install it, run:

``` 
npm install @aws-cdk/aws-s3
```

This ensures that CDK has the necessary constructs available to build your infrastructure.

For Python users, the equivalent command is:

``` 
pip install aws-cdk.aws-s3
```

Each AWS service you use in your CDK project will require its library. Installing the correct dependencies ensures your project is set up correctly.

### Bootstrapping AWS environments for CDK
Before deploying CDK infrastructure, you'll need to bootstrap your AWS environment. Bootstrapping sets up the necessary resources in your AWS account that CDK needs to manage your stacks.

When you run the cdk deploy command, CDK uses AWS CloudFormation to create and update resources in your account. However, CDK requires specific resources to manage this process, such as an S3 bucket for storing assets and IAM roles for permissions. These resources are created when you bootstrap the environment.

To bootstrap your environment, run:

Replace \<account-id\> with your AWS account ID and \<region\> with the area you're deploying to (e.g., us-east-1).

For example, if your account ID is 123456789012 and your region is us-east-1, the command would be:

Bootstrapping is necessary for any new environment and must be repeated for each AWS account or region where you plan to deploy CDK stacks. Once bootstrapped, the environment is ready to support CDK deployments.

The S3 bucket created by the bootstrap process stores deployment assets such as Lambda function code, Docker images, and CloudFormation templates. Additionally, IAM roles are provisioned, which CDK uses to interact with your AWS account.

It's important to note that you'll need to bootstrap each environment individually if you work with multiple environments. This ensures that every environment has the required resources to manage CDK deployments.

### Related Stories
- [[Building cloud resources with AWS CDK](https://medium.com/@kylejones_47003/building-cloud-resources-with-aws-cdk-7a8ee677e309)]
- [[Managing different environments for AWS CDK (Dev, Test, Prod)](https://medium.com/@kylejones_47003/managing-different-environments-for-aws-cdk-dev-test-prod-3ce6336bb7c0)]
- [[How AWS CDK turns code into CloudFormation Templates](https://medium.com/@kylejones_47003/how-aws-cdk-turns-code-into-cloudformation-templates-8f725301ef17)]
