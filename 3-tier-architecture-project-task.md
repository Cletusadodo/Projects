# 3-Tier AWS Architecture - Console-Based Intern Project Task

## 🎯 Project Overview

This project involves building a production-ready 3-tier architecture on AWS using the AWS Management Console. The intern will manually configure a highly available, fault-tolerant infrastructure following cloud best practices through the web interface.

## 📋 Project Description

### Objective
Build a complete 3-tier web application infrastructure on AWS using the AWS Console that includes:
- **Web Tier**: Public-facing web servers in public subnets
- **Application Tier**: Application servers in private subnets with auto-scaling
- **Database Tier**: RDS database in private subnets

### Key Learning Outcomes
- AWS Management Console navigation and configuration
- AWS networking concepts (VPC, subnets, route tables, security groups)
- High availability and fault tolerance design principles
- Security best practices in cloud architecture
- Monitoring and logging implementation through console
- Manual infrastructure configuration and troubleshooting

## 🏗️ Architecture Requirements

### Infrastructure Components
1. **VPC Configuration**
   - Custom VPC spanning 3 Availability Zones
   - Public subnets for web tier
   - Private subnets for application and database tiers
   - NAT Gateways for private subnet internet access
   - Internet Gateway for public subnet access

2. **Web Tier**
   - EC2 instances in public subnets
   - Application Load Balancer for traffic distribution
   - Security group allowing HTTP/HTTPS traffic

3. **Application Tier**
   - EC2 instances in private subnets
   - Auto Scaling Group for high availability
   - Security group allowing traffic from web tier only

4. **Database Tier**
   - RDS instance (MySQL/PostgreSQL) in private subnets
   - Multi-AZ deployment for high availability
   - Security group allowing access only from application tier

5. **Security & Monitoring**
   - Security Groups for each tier with least-privilege access
   - CloudTrail for API auditing
   - CloudWatch for monitoring and logging
   - S3 bucket for logs storage

## 📁 Project Structure

Create the following documentation structure:
```
3-tier-architecture-documentation/
├── README.md              # Project overview and setup
├── architecture-diagram.md # Network design and layout
├── configuration-guide.md # Step-by-step console procedures
├── screenshots/           # Console configuration screenshots
├── testing-checklist.md   # Verification procedures
├── cost-analysis.md       # Cost tracking and optimization
└── lessons-learned.md     # Project reflection and findings
```

## 🛠️ Implementation Tasks

### Phase 1: Setup and Planning (Week 1)
1. **AWS Console Setup**
   - Create AWS account (if needed)
   - Set up IAM user with appropriate permissions
   - Configure MFA for security
   - Set up billing alerts

2. **Architecture Planning**
   - Create network diagram using draw.io/lucidchart
   - Plan CIDR blocks for VPC and subnets
   - Document security group rules
   - Define resource naming conventions
   - Research AWS console navigation paths

### Phase 2: Core Infrastructure (Week 2)
1. **VPC and Networking (Console Steps)**
   - Navigate to VPC dashboard → Create VPC
   - Configure VPC CIDR (10.0.0.0/16)
   - Create 3 public subnets (different AZs)
   - Create 6 private subnets (3 for app, 3 for DB)
   - Create Internet Gateway and attach to VPC
   - Create NAT Gateways in public subnets
   - Configure route tables for public and private subnets
   - Document each step with screenshots

2. **Security Groups (Console Configuration)**
   - Navigate to EC2 → Security Groups
   - Create Web SG: Allow HTTP/HTTPS from 0.0.0.0/0
   - Create App SG: Allow traffic from Web SG only
   - Create DB SG: Allow traffic from App SG only
   - Document inbound/outbound rules with screenshots

### Phase 3: Application Layers (Week 3)
1. **Web Tier Implementation (Console Steps)**
   - Navigate to EC2 → Launch Instances
   - Select Amazon Linux 2 AMI
   - Configure instance type (t2.micro or t3.micro)
   - Select VPC and public subnets
   - Assign Web Security Group
   - Configure user data script to install Apache/Nginx
   - Launch 2-3 instances across different AZs
   - Document launch configurations with screenshots

2. **Application Load Balancer Setup**
   - Navigate to EC2 → Load Balancers
   - Create Application Load Balancer
   - Select VPC and public subnets
   - Create target group for web instances
   - Configure health checks
   - Register web instances
   - Document ALB configuration

3. **Application Tier Setup (Console Steps)**
   - Navigate to EC2 → Launch Instances
   - Select appropriate AMI (Amazon Linux 2)
   - Configure instance type (t3.small)
   - Select VPC and private subnets
   - Assign Application Security Group
   - Configure IAM role for S3 access (if needed)
   - Launch 2 instances across different AZs

4. **Auto Scaling Group Configuration**
   - Navigate to EC2 → Auto Scaling Groups
   - Create launch configuration/template
   - Define scaling policies (based on CPU/memory)
   - Set minimum/maximum/desired capacity
   - Configure health checks
   - Document ASG settings

5. **Database Tier Configuration (Console Steps)**
   - Navigate to RDS dashboard
   - Create database subnet group using private subnets
   - Select MySQL/PostgreSQL engine
   - Configure instance class (db.t3.micro for cost savings)
   - Enable Multi-AZ deployment
   - Set up backup retention period
   - Configure maintenance window
   - Assign Database Security Group
   - Document RDS configuration steps

## 🎯 Conclusion

This project provides hands-on experience building a production-ready 3-tier architecture on AWS using the Management Console. Upon completion, you will have gained practical skills in:

- **AWS Console Navigation**: Proficiency in configuring multiple AWS services through the web interface
- **Network Architecture**: Understanding of VPC design, subnetting, and security group implementation
- **High Availability**: Implementation of multi-AZ deployments and auto-scaling configurations
- **Security Best Practices**: Application of least-privilege access controls and tier isolation
- **Documentation Skills**: Creating comprehensive guides with screenshots for reproducible deployments

The completed infrastructure will serve as a solid foundation for understanding cloud architecture patterns and can be extended with additional AWS services as needed. Remember to properly document your configurations and clean up resources to avoid unnecessary costs.
