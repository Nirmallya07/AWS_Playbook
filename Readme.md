# AWS Playbook

## Overview

This repository contains a collection of hands-on AWS implementations covering core cloud services, networking, security, monitoring, and deployment patterns. Each document represents a practical scenario with step-by-step configuration and validation.

The focus of this repository is on real-world setups, architectural understanding, and operational practices rather than theoretical explanations.

---

## Repository Structure

The repository is organized as independent modules, each covering a specific AWS concept or use case.

Examples include:

* VPC and networking configurations
* EC2 provisioning and application deployment
* IAM policies and access control
* S3 storage management and lifecycle policies
* Load balancing and high availability
* Monitoring and alerting using CloudWatch
* Disaster recovery and backup strategies

All supporting screenshots are stored in the `images/` directory.

---

## Key Implementations

### Networking and Architecture

* Custom VPC setup with EC2 and Nginx deployment
* Hub and Spoke VPC architecture
* Bastion-less architecture design
* Private EC2 access using VPC endpoints

### Compute and Deployment

* EC2 instance provisioning and web server setup
* Flask application deployment on EC2
* Jenkins setup on EC2
* Auto Scaling Group with launch templates

### Storage and Data

* S3 bucket creation and management using CLI
* S3 lifecycle rule configuration
* Restricting bucket deletion with IAM policies

### Database

* RDS MySQL deployment
* Read replica implementation

### Security and IAM

* IAM best practices implementation
* Policy to allow EC2 actions but deny termination
* Region-based access restrictions
* Denying specific S3 bucket access

### Monitoring and Logging

* CloudWatch monitoring setup
* SNS alert configuration
* Centralized logging architecture

### High Availability and DR

* Route 53 failover routing with multi-region ALB
* Disaster recovery setup

---

## How to Use

Each file in this repository is self-contained and includes:

* Objective of the task
* Step-by-step implementation
* Configuration details
* Screenshots for verification
* Final result

To explore:

1. Open any `.md` file
2. Follow the steps in sequence
3. Refer to screenshots in the `images/` folder

---

## Prerequisites

* AWS account
* Basic understanding of cloud computing concepts
* Familiarity with AWS Management Console or CLI

---

## Notes

* Sensitive data such as private keys should never be committed to the repository
* Security groups, IAM roles, and policies should follow least privilege principles
* Costs may be incurred when running AWS resources; ensure cleanup after testing

---

## Author

Nirmallya Bhowmick

