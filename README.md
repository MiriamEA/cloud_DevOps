
# Introduction
This project describes the process of deploying my [Trading App](github.com/MiriamEA/trading_app)

What project you will deploy and project GitHub URL (your implementation is preferred)
Describe your project at a high level (microserver, psql, java)

# Docker Architecture Diagram
![docker architecture](https://github.com/MiriamEA/cloud_DevOps/blob/master/assets/trading-app-docker.svg)
- trading_app docker diagram including:
 - use draw.io and AWS icons (it's already in draw.io library)
 - images (docker hub and local)
 - bridge network
 - containers
 - label commands

- Two docker files
  - trading-app
   - talk about the process (e.g. compile and package jar and run the app)
  - jrvs-psql
   - talk about how to create tables (e.g. schema.sql)

# Cloud Architecture Diagram
![cloud architecture](https://github.com/MiriamEA/cloud_DevOps/blob/master/assets/trading-app-aws.svg)
- trading app diagram
  - use draw.io and aws icons (it's in the draw.io library)
  - include ec2, alb, auto scaling, target group, rds
  - security groups
  - label all important ports(e.g. ALB HTTP, ec2 tpc:5000, RDS tcp:5432)
  
# AWS EB and Jenkins CI/CD Pipeline Diagram
- Please refer to Jenkins guide architecture diagram.
