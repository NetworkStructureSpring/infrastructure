## Create & Setup GitHub Repository for AWS Infrastructure
* Create (Links to an external site.) a new private GitHub repository in the GitHub organization you created.
* GitHub repository name must be infrastructure.
* Grant TAs access to your GitHub repository.
* Update README.md in your repository with instructions for setting up your infrastructure using CloudFormation.
* Fork the GitHub repository in your namespace. You will do all development work on your fork.
* All CloudFormation templates should be in this repository.
* Add appropriate .gitignore to your repository. A collection of useful .gitignore templates can be found here.

## Instructions to setup infrastructure using cloudformation 
* Install and set up AWS command-line interface.
* Create CloudFormation template csye6225-infra.yml that can be used to set up required networking resources.
* Values should not be hardcoded in your CloudFormation template.
* Create Virtual Private Cloud (VPC) 
* Create subnets in your VPC. You must create 3 subnets, each in a different availability zone in the same region in the same VPC.
* Create an Internet Gateway resource and attach the Internet Gateway to the VPC.
* Create a public route table. Attach all subnets created to the route table.
* Create a public route in the public route table created above with destination CIDR block 0.0.0.0/0 and internet gateway created above as the target.
* You must be able to use the same CloudFormation template in the same AWS account and region to create multiple VPCs including all of its resources (listed in the “AWS Networking Setup” section) such as subnets, internet gateway, route table, etc.

## Commands Required

* aws --version
* aws configure --profile=dev
* aws configure --profile=demo , region: us-east-1 
* set AWS_PROFILE=dev
* set AWS_REGION=us-east-1
* aws ec2 describe-vpcs
* aws cloudformation deploy --profile dev --stack-name teststack --template-file csye6225-infra.yml --parameter-overrides file://Parameters.json --capabilities CAPABILITY_IAM
*  aws cloudformation delete-stack --stack-name teststack

psql --host=csye6225.couixgkja1id.us-east-1.rds.amazonaws.com  --port=5432 --username=csye --password --dbname=csye6225
  
SELECT datname,usename, ssl, client_addr 
  FROM pg_stat_ssl
  JOIN pg_stat_activity
    ON pg_stat_ssl.pid = pg_stat_activity.pid;


aws acm import-certificate --certificate fileb://Certificate.pem --certificate-chain fileb://CertificateChain.pem --private-key fileb://PrivateKey.pem