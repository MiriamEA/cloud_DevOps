# Introduction
This project describes the process of deploying my [Trading App](https://github.com/MiriamEA/trading_app) on AWS.
The trading app is a REST API developed in Java that uses a PostgreSQL database to persist data.

# Docker Deployment
This first method to deploy the app makes use of Docker containers on an EC2 instance (needs to be setup manually). 
The app requires two containers: one for PostgreSQL to run the database, and one to run the app.
In order for those two containers to communicate a network bridge is required and both containers need to be connected to the network.
The bridge is created with the following command ```sudo docker network create --driver bridge trading-net```.

Building the two containers requires a local docker image for both. 
The instructions on how to create the images are in the two Dockerfiles.
The [Dockerfile for the app image](https://github.com/MiriamEA/trading_app/blob/master/Dockerfile) is built on the maven image and the openjdk image from Docker Hub. Maven is required to compile and package the code into a jar-file and openjdk is required to run the jar-file.
The [Dockerfile for the PSQL image](https://github.com/MiriamEA/trading_app/blob/master/psql/Dockerfile) is built on the postgres image from Docker Hub. It will automatically create the database and all required tables.
The commands for creating the two local images are the following:
```
sudo docker build -t trading-app .
sudo docker build -t psql .
```
Once the images are created the two container can be built with the following commands:
```
sudo docker run --rm --name psql \
-e POSTGRES_PASSWORD=password \
-e POSTGRES_DB=jrvstrading \
-e POSTGRES_USER=postgres \
--network trading-net \
-d -p 5432:5432 psql
```
and 
```
sudo docker run \
-e "PSQL_URL=jdbc:postgresql://psql:5432/jrvstrading" \
-e "PSQL_USER=postgres" \
-e 'PSQL_PASSWORD=password' \
-e "IEX_PUB_TOKEN=YOUR_TOKEN" \
--network trading-net \
-p 5000:5000 -t trading-app
```
Now, the app is deployed.

This diagram shows the architecture of the deployment with Docker.
![docker architecture](https://github.com/MiriamEA/cloud_DevOps/blob/master/assets/trading-app-docker.svg)

# Cloud Deployment
The second method to deploy the app uses the AWS database service instead of a local database. It also uses an auto scaling group and a load balancer, which allow horizontal scaling of the application.
The auto scaling group decides how many EC2 instances are running in the target group and the load balancer distributes incoming requests among all running EC2 instances in the target group. 

This diagram shows the architecture of the manual cloud deployment.
![cloud architecture](https://github.com/MiriamEA/cloud_DevOps/blob/master/assets/trading-app-aws.svg)
  
# AWS EB and Jenkins CI/CD Pipeline Diagram
- Please refer to Jenkins guide architecture diagram.
