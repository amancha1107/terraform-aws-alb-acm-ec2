# How to Deploy EC2 Instance with a Load Balancer, and SSL Certificate(ACM) in AWS with Terraform

![image](https://user-images.githubusercontent.com/66196388/181624674-53e37858-cc4c-457c-84bb-0cf32a9eb8f8.png)

- open terraform.tfvars file and add keys,public domain name,sub domain record

## Prerequisite #1: AWS Credentials:-

- Before creating our AWS EC2 Instance, we will need AWS Credentials to execute our Terraform code

- The AWS provider offers a few options for providing credentials for authentication:

- Static credentials, Environment variables, Shared credentials/configuration file

- here we will use static credentials in terraform.tfvars file

## Prerequisite #2: AWS Key Pair:-

- We will need an AWS Key Pair, consisting of a public key and a private key. The AWS Key Pair is a set of security credentials that we need to connect to an Amazon EC2 instance.

- Amazon EC2 stores the public key on our instance, and we store the private key in Current Directory. For Linux instances, the private key allows us to securely SSH into our instance.

- A better way is using Terraform to create the AWS Key Pair. First, a file called “key-pair-main.tf” is used to create keypair

- This code will generate an AWS Key Pair, and using the resource “local_file” will save the file to the folder where we run our Terraform code


## Prerequisite #3: Register a Public Zone on AWS Route 53 (optional step required for ACM):-

- We need a public zone on AWS Route 53, if we want to use AWS Certificate Manager to create and manage our SSL certificates.

- Go to the Route 53 console and create a new Public Hosted Zone with public domain(example.com), transfer the name servers into aws route 53 if your doamin is managed by other provider

- And update provider’s DNS records (this step can vary based on your DNS provider). Depending on our DNS provider, the change will take a few minutes to hours. After that, we will be able to manage our domain from AWS Route 53.

