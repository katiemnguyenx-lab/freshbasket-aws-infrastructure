# FreshBasket AWS Infrastructure Design

## Project Overview

This project presents an AWS cloud infrastructure design for FreshBasket, a web application that allows users to submit and view orders. The architecture was designed to support scalability, high availability, fault tolerance, disaster recovery, and secure database access.

## Business Problem

FreshBasket requires a reliable cloud infrastructure that can handle web traffic, process user requests, store order data securely, and remain available if an instance or Availability Zone fails. The goal of this project was to design and document a scalable AWS solution suitable for a small web application.

## Tools and Technologies Used

- Amazon Elastic Beanstalk
- Amazon EC2
- Application Load Balancer
- Auto Scaling Group
- Amazon RDS MySQL
- Amazon VPC
- Public Subnets
- Internet Gateway
- Security Groups
- Amazon CloudWatch
- Amazon SNS
- Draw.io
- PHP
- MySQL

## Architecture Summary

The FreshBasket application is deployed using Elastic Beanstalk, which manages the EC2 instances, Load Balancer, Auto Scaling Group, and CloudWatch monitoring. User requests enter through the Internet Gateway and are routed to the Application Load Balancer. The Load Balancer forwards traffic to healthy EC2 instances across two Availability Zones.

The application connects to an RDS MySQL database to store and retrieve order information. Security Groups are configured so that the database is not directly accessible from the internet and only accepts MySQL traffic from the EC2 instances.

## Key Features

- Designed a custom VPC with public subnets across two Availability Zones
- Configured EC2 instances to run the FreshBasket web application
- Used an Application Load Balancer to distribute traffic across healthy instances
- Designed Auto Scaling rules to scale out when CPU usage increases
- Included RDS MySQL Multi-AZ for database availability and disaster recovery
- Applied Security Groups to control access between web and database layers
- Used CloudWatch for monitoring and SNS for email notifications
- Created an architecture diagram using Draw.io

## Scalability

The architecture uses an Auto Scaling Group to automatically adjust the number of EC2 instances based on CPU usage. When demand increases, additional instances can be launched. When demand decreases, the environment can scale back down to reduce unnecessary resource usage.

## High Availability and Fault Tolerance

The application is designed across two Availability Zones. If one EC2 instance fails, the Load Balancer stops routing traffic to it and sends requests to healthy instances. If one Availability Zone experiences issues, the application can continue running in the other Availability Zone.

## Disaster Recovery

The database layer uses RDS MySQL with Multi-AZ design. This allows the system to maintain a standby database copy in another Availability Zone. If the primary database fails, AWS can fail over to the standby database.

## Security Considerations

The EC2 Security Group allows HTTP traffic for users and SSH access for administration. The RDS Security Group only allows MySQL traffic from the EC2 Security Group, which prevents direct public access to the database.

## What I Learned

Through this project, I improved my understanding of cloud infrastructure design, AWS service integration, system documentation, scalability, disaster recovery, high availability, and secure application deployment.
