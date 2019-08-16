
# Introduction
This project describes the process of deploying my [Trading App](https://github.com/MiriamEA/trading_app) on AWS.
The trading app is a REST API developed in Java that uses a PostgreSQL database to persist data.

# Docker Deployment
This first method to deploy the app makes use of Docker containers. 
The app requires two containers: one for PostgreSQL to run the database, and one to run the app.
In order for those two containers to communicate a network bridge is required and both containers need to be connected to the network.
The bridge is created with the following command ```sudo docker network create --driver bridge trading-net```.

Building the two containers requires a local docker image for both. 
The instructions on how to create the images are in the two Dockerfiles.
The [Dockerfile for the app image](https://github.com/MiriamEA/trading_app/blob/master/Dockerfile) is built on the maven image and the openjdk image from Docker Hub. Maven is required to compile and package the code into a jar-file and openjdk is required to run the jar-file.
The [Dockerfile for the PSQL image](https://github.com/MiriamEA/trading_app/blob/master/psql/Dockerfile) is built on the postgres image from Docker Hub. It will automatically create the database and all required tables.


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

# Cloud Deployment
![cloud architecture](https://github.com/MiriamEA/cloud_DevOps/blob/master/assets/trading-app-aws.svg)
- trading app diagram
  - use draw.io and aws icons (it's in the draw.io library)
  - include ec2, alb, auto scaling, target group, rds
  - security groups
  - label all important ports(e.g. ALB HTTP, ec2 tpc:5000, RDS tcp:5432)
  
# AWS EB and Jenkins CI/CD Pipeline Diagram
- Please refer to Jenkins guide architecture diagram.
