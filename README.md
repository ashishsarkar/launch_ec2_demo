# AWS Inspector Services with Notification Services

Amazon Inspector is an automated security assessment service that helps improve the security and compliance of applications deployed on AWS. Amazon Inspector automatically assesses applications for exposure, vulnerabilities, and deviations from best practices. After performing an assessment, Amazon Inspector produces a detailed list of security findings prioritized by level of severity. 

## Installation

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.


## terraform-inspector-services



The Terraform setup for creating an Inspector services along with the SNS notification services. When any Inspector Assessment is run, the service notifies about the status changes and the reports status being delivered on mail. 
The terraform set up creates several components as below. Refer the script for more details. 

```
1. Inspector 
2. CloudWtach Events for EC2
3. CloudWatch Events for Inspector Assessment
4. Lambda for EC2 for Tagging Instances
5. Lambda for Inspector with SNS notification
6. SNS subscription 

```


# Prerequisites

```
No Prerequisites required as of now.

```


# Remote State Fetch

```
No Remote State Fetch is required as of now. 
```


# Getting Started

  
This code requires using Terraform >=0.12.0.  If you are running a older version of Terraform, you may need to upgrade

```
terraform 0.12upgrade
```

After cloning

```
env=dev

terraform get -update=true

terraform init -backend-config=environments/dev/backend.config
```

This will ensure that the modules are registered and any required providers are downloaded.  Now that the build environment is initialized, you must define th$

```
terraform plan -var-file=environments/${env}/variables.tfvars 
```

If everything in the plan looks appropriate, you may apply the Terraform module and begin building out your infrastructure by running:

```
terraform apply -var-file=environments/${env}/variables.tfvars 

```

 

# Backend Configuration

The S3 bucket should be created in advance. Your underlying IAM policy snhould allow TF to have RW access to the Bucket. 


```
terraform {
  required_version = "~> 0.12"
  backend "s3" {
    encrypt = true
  }
}
```

# Configurations added in environments
```
bucket  = "terraform-governance"
key     = "terraform_aws_inspector/terraform_aws_inspector.tfstate"
encrypt = true
region  = "eu-central-1"

```

