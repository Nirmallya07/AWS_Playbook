# **AWS Route 53 Failover Routing with Multi-Region ALB**

## **Overview**

This project demonstrates DNS-based failover routing using Amazon Route 53. The architecture includes two Application Load Balancers (ALBs) deployed in different AWS regions. Route 53 monitors the health of the primary region and automatically redirects traffic to a secondary region in case of failure.

## **Architecture**

-   Primary Region: ap-south-1 (Mumbai)

-   Secondary Region: us-east-1 (N. Virginia)

-   Load Balancers: Application Load Balancer (ALB) in each region

-   DNS Service: Amazon Route 53

-   Health Monitoring: Route 53 Health Checks

## **Components**

### **1. Application Load Balancers**

-   Internet-facing ALBs created in both regions

-   Each ALB forwards traffic to EC2 instances via target groups

![](./images/abb2a0decb951776466948676408c70ad599e9a8.png){width="6.229166666666667in" height="3.0447047244094487in"}\
\
![](./images/c198de21c0d4d7a8ed4466b2244dee727ef864b0.png){width="6.25in" height="3.0520833333333335in"}

### **2. EC2 Instances**

-   Deployed in public subnets

-   Serve HTTP responses for testing\
    ![](./images/f0f511e36281afe669ba4da122a0722532dd5c2f.png){width="6.25in" height="3.0520833333333335in"}![](./images/f31a0b79c41075173b81a0e7cabd222f2bb46d9a.png){width="6.25in" height="3.0520833333333335in"}

### **3. Route 53 Hosted Zone**

-   Public hosted zone created with a test domain:

![](./images/d526ccbaa5794206a00e3cbdfe54fe071f720a96.png){width="6.5in" height="3.1770833333333335in"}![](./images/5c3d8a12ee236ebda90375db2425ab8e793fa689.png){width="6.5in" height="3.1770833333333335in"}

### **4. DNS Records**

Two A records configured with Failover routing:

#### **Primary Record**

-   Name: [www.myapp.local](http://www.myapp.local/)

-   Type: A (Alias)

-   Target: Mumbai ALB

-   Routing policy: Failover (Primary)

-   Health check: Attached

#### **Secondary Record**

-   Name: [www.myapp.local](http://www.myapp.local/)

-   Type: A (Alias)

-   Target: Virginia ALB

-   Routing policy: Failover (Secondary)

-   Health check: Not attached

## **Health Check Configuration**

-   Protocol: HTTP

-   Endpoint: Primary ALB DNS

-   Interval: 30 seconds

-   Failure threshold: 3

-   Success criteria: HTTP 2xx or 3xx response

Requesting Primary region DNS (Simulating no failure)

![](./images/71301f4129bf62ceb87e885ed7fde460f4576ab4.png){width="6.5in" height="0.4895833333333333in"}IP of MUMBAI ALB\
\
Requesting Primary region DNS again (Simulating failure (All instances down))\
![](./images/c0c82ba0c22a3c28d1e0f3dc481bd8ed0817cdc6.png){width="6.5in" height="0.4895833333333333in"}IP of N.VIRGINIA ALB
