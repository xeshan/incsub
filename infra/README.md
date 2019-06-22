
# Incsub trial
### ECS Cluster provision with CloudFormation

This repository aimed to design [Amazon EC2 Container Service (Amazon ECS)](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/Welcome.html) based infrastructure which provision with [AWS CloudFormation](https://aws.amazon.com/cloudformation/).

## Prerequisite step
- Import SSL certificate 

For quick you can launch complete infra by click launch stack:

| AWS Region | Short name | | 
| -- | -- | -- |
| US East (N. Virginia) | us-east-1 | [![cloudformation-launch-button](https://ecswithcf.s3.amazonaws.com/launch-stack.jpg)](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=Incsub-trial&templateURL=https://incsub-trial.s3.amazonaws.com/master.yml) |

It will ask for SSL Certificate Arn which were added in prerequisite step

![arn](https://incsub-trial.s3.amazonaws.com/img/SslCertArn.png)

## Overview


The repository contains templates that deploy the following AWS services:

 - The [VPC](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Introduction.html) with public and private subnets.
 - A highly available ECS cluster on two [Availability Zones](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html) in an [Auto Scaling](https://aws.amazon.com/autoscaling/) group.
 - [NAT gateways](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-nat-gateway.html) (one in each zone) to handle outbound traffic.
 - 2 interconnected containers/microservices deployed as [ECS services](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs_services.html) (WEB and PHP). 
 - An [Application Load Balancer (ALB)](https://aws.amazon.com/elasticloadbalancing/applicationloadbalancer/) to handle inbound traffic.
 - [Auto Scaling Lifecycle Hook](https://docs.aws.amazon.com/autoscaling/ec2/userguide/lifecycle-hooks.html).

####  Deployment/updation & rollback

These CF template to design for not only provision the infrastrucutre but also can use for deployment of new changes.

## Template details

Following are templates included in this repo.

| Template | Description |
| --- | --- | 
| [master.yml](master.yml) | This is the master template - deploy it to CloudFormation and it includes all of the others automatically. |
| [incsub-vpc.yml](incsub-vpc.yml) | Template for VPC with public and private subnets across two different Availabilty Zones with Internet Gateway and default route on the public subnets + NAT Gateways (one in each AZ) and default routes for them in the private subnets.|
| [incsub-sg.yml](incsub-sg.yml) | This template contains the [security groups](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_SecurityGroups.html) required by the entire stack.|
| [incsub-lb.yml](incsub-lb.yml) | Template for ALB  |
| [incsub-ecs-cluster.yml](incsub-ecs-cluster.yml) | Template for ECS cluster deployment on private subnets + Auto Scaling group.
| [incsub-autoscaling.yml](incsub-autoscaling.yml) | Template for autoscaling. |
| [services/php.yml](services/php.yml) | PHP-fpm service|
| [services/web.yml](services/web.yml) | Web service (Nginx) service |



