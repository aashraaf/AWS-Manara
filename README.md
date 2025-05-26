# Scalable Web Application with ALB and Auto Scaling
## 🧭 Solution Overview
This project demonstrates how to deploy a scalable and highly available eCommerce web application on AWS using EC2 instances, an Application Load Balancer (ALB), and Auto Scaling Groups (ASG). Integration with Amazon RDS is included to store product and user data in a persistent and reliable backend.

The architecture is designed to reflect real-world best practices for hosting a dynamic online store, such as handling user traffic spikes, ensuring fault tolerance, and monitoring application health. Security, cost-efficiency, and performance optimization are also core components of the setup.

## 🎯 Key AWS Services
-*Amazon EC2:* Hosts the web application.

-*Application Load Balancer (ALB):* Distributes traffic across multiple EC2 instances.

-*Auto Scaling Group (ASG):* Automatically adjusts capacity based on traffic.

-*Amazon RDS :* Provides a managed relational database.

-*IAM:* Manages secure role-based access.

-*Amazon CloudWatch & SNS:* Monitors system performance and sends alerts.

## 🧱 Architecture Diagram



## 🧩 Default Architecture
The web application is structured to ensure high availability and scalability through the following AWS resources:

VPC with public and private subnets across multiple Availability Zones.

Public Subnets host the Application Load Balancer (ALB).

Private Subnets host EC2 instances in an Auto Scaling Group.

Amazon RDS in a Multi-AZ deployment for data persistence.

IAM Roles assigned to EC2 instances for secure access to necessary AWS services.

CloudWatch Alarms and SNS Topics for real-time monitoring and alerting.

## 🔁 Request Flow and Monitoring
1. *User to Application Load Balancer*
The user sends a request via HTTP/HTTPS. The ALB receives the request and determines how to route traffic based on defined listener rules and target groups.

2. *ALB to EC2 Instances in Auto Scaling Group*
The ALB forwards requests to healthy EC2 instances within the Auto Scaling Group. Traffic is evenly distributed, and scaling policies ensure the group adapts to traffic changes.

3. *EC2 Instances to RDS*
EC2 instances handle application logic and interact with Amazon RDS to store and retrieve data. RDS is deployed with Multi-AZ for high availability.

4. *CloudWatch Monitoring All 3 Services*
Amazon CloudWatch continuously collects metrics from ALB, EC2, and RDS. These metrics are used for dashboard visualization and triggering alarms.

5. *CloudWatch to SNS*
When an alarm condition is met (e.g., high CPU usage or instance failure), CloudWatch sends notifications to an SNS topic, which distributes alerts to subscribers via email or SMS.

