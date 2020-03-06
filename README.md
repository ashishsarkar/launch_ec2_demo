# AWS CloudWatch Default Log Group and Log Stream creation 

CloudWatch Log Streams:  A log stream is a sequence of log events that share the same source. Each separate source of logs into CloudWatch Logs makes up a separate log stream.

CloudWatch Log Groups: A log group is a group of log streams that share the same retention, monitoring, and access control settings. You can define log groups and specify which streams to put into each group. There is no limit on the number of log streams that can belong to one log group.


## Installation

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.


## cloudwatch_logGroup_Stream_creation

This project is a Ansible Deployment contains scripts that are integrated with OS Hardening scripts. For creating any automation of Default Log Group and Log Streams:
1) A common by-default log has been implemented in the code.
2) Automation of the Log Stream has been implemented in the code.

Whenever, any OS EC2 Linux Distros is provisioned, the CW Log Group and Streams are created automatically removing the headache of creating any logStream or logGroup.

```
1. Python Script.
2. Ansible Module (defaults, files, handlers, mets, README.md, tasks, templates, tests, vars).
3. Defaults directory contains all the path of the scripts, where it should be placed and acts as a variable.
4. Files contains python scripts for creating CW Log Groups and Log Streams.
5. Tasks contains all the required code for pacing the files in the respective directory of Slaves EC2 machine and cron setup to execute the script at startup.
6. It will be executed in the "root"

```


## Prerequisites

```
1) Python-3+ should be installed
2) PIP should be installed (sudo easy_install pip)
3) Boto3 package should be installed (pip install boto3)
4) Requests package should be installed (pip install requests)
```


## Remote State Fetch

```
No Remote State Fetch is required as of now. 
```


## Getting Started

  
This platform requires Ansible. You will need to execute changes(if any) from Master VM. The access to it will be available to @Amey Erande[AMEY.ERANDE@t-systems.com] and other contact person.

```
terraform 0.12upgrade
```

After cloning

```
env=dev

terraform get -update=true

terraform init -backend-config=environments/${env}/backend.config
```

This will ensure that the modules are registered and any required providers are downloaded.  Now that the build environment is initialized, you must define th$

```
terraform plan -var-file=environments/${env}/variables.tfvars 
```

If everything in the plan looks appropriate, you may apply the Terraform module and begin building out your infrastructure by running:

```
terraform apply -var-file=environments/${env}/variables.tfvars 

```

 

## Backend Configuration

The S3 bucket should be created in advance. Your underlying IAM policy snhould allow TF to have RW access to the Bucket. 


```
terraform {
  required_version = "~> 0.12"
  backend "s3" {
    encrypt = true
  }
}
```

## Configurations added in environments
```
bucket  = "terraform-governance"
key     = "terraform_aws_inspector/terraform_aws_inspector.tfstate"
encrypt = true
region  = "eu-central-1"

```

## README's for AWS Inspector Modules
* Environments - https://gitlab.dol.telekom.de/mcsmco/governance/terraform-aws-inspector/tree/master/environments
* File - https://gitlab.dol.telekom.de/mcsmco/governance/terraform-aws-inspector/tree/master/file
* File SNS - https://gitlab.dol.telekom.de/mcsmco/governance/terraform-aws-inspector/tree/master/file_sns
* Inspector - https://gitlab.dol.telekom.de/mcsmco/governance/terraform-aws-inspector/tree/master/inspector
* Lambda - https://gitlab.dol.telekom.de/mcsmco/governance/terraform-aws-inspector/tree/master/lambda
* Packages - https://gitlab.dol.telekom.de/mcsmco/governance/terraform-aws-inspector/tree/master/packages
* SNS - https://gitlab.dol.telekom.de/mcsmco/governance/terraform-aws-inspector/tree/master/sns
* SNS Lambda - https://gitlab.dol.telekom.de/mcsmco/governance/terraform-aws-inspector/tree/master/snslambda
* SNS Packages - https://gitlab.dol.telekom.de/mcsmco/governance/terraform-aws-inspector/tree/master/snspackages


## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| aws\_cloudwatch\_event\_rule | AWS Lambda = AWS Lambda CW Eventrule | string | n/a | yes |
| aws\_inspector\_assessment\_target\_name | AWS Inspector - Assessment Target Name | string | n/a | yes |
| aws\_inspector\_assessment\_template\_name | AWS Inspector - Assessment Template Name | string | n/a | yes |
| aws\_inspector\_aws\_cw\_event\_rule | AWS Inspector - Assessment IAM Event rule | string | n/a | yes |
| aws\_inspector\_aws\_iam\_event\_policy | AWS Inspector - Assessment IAM Event policy | string | n/a | yes |
| aws\_inspector\_aws\_iam\_event\_role | AWS Inspector - Assessment IAM Event Role | string | n/a | yes |
| aws\_inspector\_resource\_group\_security\_tags | AWS Inspector - tags | string | n/a | yes |
| aws\_inspector\_resource\_group\_ssm\_tags | AWS Inspector - tags | string | n/a | yes |
| aws\_lambda\_archive\_file\_type | AWS Lambda File- AWS Lambda Archive file type | string | n/a | yes |
| aws\_lambda\_filename | AWS Lambda File - AWS Lambda fileName | string | n/a | yes |
| aws\_lambda\_function\_aws\_iam\_role | AWS Lambda - AWS Lambda Output path | string | n/a | yes |
| aws\_lambda\_function\_handler\_name | AWS Lambda - AWS Lambda function Handler name | string | n/a | yes |
| aws\_lambda\_function\_name | AWS Lambda - AWS Lambda Function Name | string | n/a | yes |
| aws\_lambda\_function\_run\_time | AWS Lambda - AWS Lambda Runtime\(Python, NodeJs, etc..\) | string | n/a | yes |
| aws\_lambda\_output\_path | AWS Lambda File - AWS Lambda Output path | string | n/a | yes |
| aws\_lambda\_source\_directory | AWS Lambda File - AWS Lambda source directory | string | n/a | yes |
| aws\_region | Specify your 'REGION' here | string | n/a | yes |
| aws\_sns\_lambda\_archive\_file\_type | AWS SNS Lambda File- AWS Lambda Archive file type | string | n/a | yes |
| aws\_sns\_lambda\_filename | AWS SNS Lambda File - AWS Lambda fileName | string | n/a | yes |
| aws\_sns\_lambda\_function\_aws\_iam\_role | AWS SNS Lambda File - AWS Lambda function name | string | n/a | yes |
| aws\_sns\_lambda\_function\_handler\_name | AWS SNS Lambda File - AWS Lambda function name | string | n/a | yes |
| aws\_sns\_lambda\_function\_name | AWS SNS Lambda File - AWS Lambda function name | string | n/a | yes |
| aws\_sns\_lambda\_function\_run\_time | AWS SNS Lambda File - AWS Lambda function name | string | n/a | yes |
| aws\_sns\_lambda\_output\_path | AWS SNS Lambda File - AWS Lambda Output path | string | n/a | yes |
| aws\_sns\_lambda\_source\_directory | AWS SNS Lambda File - AWS Lambda source directory | string | n/a | yes |
| aws\_sns\_topic\_display\_name | AWS SNS Topic - New SNS Topic display name | string | n/a | yes |
| aws\_sns\_topic\_name | AWS SNS Topic - New SNS Topic Created | string | n/a | yes |
| sns\_tag\_description | AWS SNS Topic -  AWS SNS Description Name | string | n/a | yes |
| sns\_tag\_email | AWS SNS Topic -  AWS SNS Tag Email Name | string | n/a | yes |
| sns\_tag\_owner | AWS SNS Topic -  AWS SNS Tag Owner Name | string | n/a | yes |
| tag\_description | AWS Lambda - AWS Lambda Tag description | string | n/a | yes |
| tag\_email | AWS Lambda - AWS Lambda Tag Owner email | string | n/a | yes |
| tag\_owner | AWS Lambda - AWS Lambda Tag Owner name | string | n/a | yes |

