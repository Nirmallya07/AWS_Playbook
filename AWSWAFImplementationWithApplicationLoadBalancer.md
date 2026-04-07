# **AWS WAF Implementation with Application Load Balancer**

## **Objective**

To implement AWS Web Application Firewall (WAF) with an Application Load Balancer (ALB) and configure security rules including SQL injection protection, rate limiting, and geo blocking. The setup is tested using curl commands from EC2 instances.

## **Architecture Overview**

-   Application Load Balancer (ALB)

-   AWS WAF (Web ACL)

-   EC2 instances (for testing)

-   Internet-facing traffic routed through ALB

## **Steps Performed**

### **1. Create Web ACL (WAF)**

-   Navigated to AWS WAF & Shield

-   Created a Web ACL named webACL1

-   Selected resource type supporting Application Load Balancer\
    \
    ![](./images/1686df66658142cfecd09b8beaac25b3a398be21.png){width="6.25in" height="3.1979166666666665in"}![](./images/31ed2c99a42c5c7b1c4b43b0e23f4f5a18706b9d.png){width="6.25in" height="3.1979166666666665in"}

### **2. Add SQL Injection Protection**

-   Added AWS Managed Rule Group:

    -   AWSManagedRulesSQLiRuleSet

-   Configured rule action as Block

-   Applied to all requests

![](./images/fed1ea3ce5133c5d37d8e756fee340af2c4d84c4.png){width="6.5in" height="3.3229166666666665in"}

### **3. Attach WAF to ALB**

-   Associated Web ACL with ALB (ALB1)

-   Verified integration through WAF console and ALB settings

![](./images/f931f20bb6ffb84f14aa4a289e69b049834c6399.png){width="6.5in" height="3.3229166666666665in"}

### **4. Add Rate Limiting Rule**

-   Created a rate-based rule:

    -   Name: rate-limit-rule

    -   Limit: 100 requests per 5 minutes per IP

    -   Action: Block

![](./images/5b1126f89441d3757205d183161a53491d33ce6c.png){width="6.5in" height="3.3229166666666665in"}

### **5. Add Geo Blocking Rule**

-   Created custom rule:

    -   Name: geo-block-rule

    -   Rule type: Geo match

    -   Blocked country: United States (for testing)

    -   Action: Block

![](./images/7ac8a31a38da84106bfba3f66c77ccd1ac129883.png){width="6.5in" height="3.3229166666666665in"}

### **6. Rule Priority Order**

Rules were configured in the following order:

1.  SQL Injection Rule

2.  Rate Limiting Rule

3.  Geo Blocking Rule

## **Testing**

### **1. Normal Request**

curl <http://> ALB1-715654199.ap-south-1.elb.amazonaws.com

From India ( succesfull )

![](./images/8be79ac3c78802596b42f1427af1b5cae81778aa.png){width="4.447916666666667in" height="2.2310859580052496in"}

From USA

![](./images/db78a9ee2519c6c341a449f9c85adf84a9d598c7.png){width="6.5in" height="3.2604166666666665in"}

Unsuccesful 403 Forbidden.
