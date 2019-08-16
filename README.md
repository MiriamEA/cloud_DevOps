
# Introduction
This project describes the process of deploying my [Trading App](https://github.com/MiriamEA/trading_app) on AWS.
The trading app is a REST API developed in Java that uses a PostgreSQL database to persist data.

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
