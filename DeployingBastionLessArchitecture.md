# **Bastion-less Access to Private EC2 using AWS Systems Manager**

## **Overview**

This setup enables secure access to a private EC2 instance without using a bastion host or SSH.

Access is achieved via **AWS Systems Manager Session Manager**, keeping the instance fully private.

## **Architecture**

-   EC2 instance in **private subnet**

-   **No public IP**

-   **No inbound ports (SSH disabled)**

-   Access via **SSM over HTTPS (port 443 outbound)**

## **Components Used**

-   Amazon EC2

-   AWS Systems Manager (SSM)

-   IAM Role (AmazonSSMManagedInstanceCore)

-   VPC Interface Endpoints:

    -   ssm

    -   ec2messages

    -   ssmmessages

## **Step-by-Step Setup**

### **1. Launch EC2 Instance**

-   Place instance in a **private subnet**

-   Do **not assign public IP**

![](./images/5e6aa422a6b0bc875b6e43e16e612cef7da3fcd0.png){width="6.5in" height="3.46875in"}

### **2. Attach IAM Role**

Attach role with policy:

AmazonSSMManagedInstanceCore

![](./images/0f13cdafcb767d15795d4e113f0687ac0ce6e601.png){width="6.5in" height="3.3229166666666665in"}

### **3. Enable VPC DNS Settings**

Go to VPC → Edit settings:

-   Enable DNS resolution ✅

-   Enable DNS hostnames ✅

![](./images/edce4ef919da6e2e3b9877a2fccfc1ec35675dca.png){width="6.5in" height="3.3229166666666665in"}

### **4. Create VPC Interface Endpoints**

Create the following endpoints in the same VPC and subnet:

com.amazonaws.\<region\>.ssm\
com.amazonaws.\<region\>.ec2messages\
com.amazonaws.\<region\>.ssmmessages

Configuration:

-   Type: Interface

-   Subnet: Private subnet

-   Security Group: Allow HTTPS (443)

-   Private DNS: Enabled ✅

-   Policy: Full access

![](./images/f47c4f6c07470d8932d93d37f174addcc51a81eb.png){width="6.5in" height="3.3229166666666665in"}

### **5. Security Group Configuration**

#### **EC2 Instance**

-   Inbound: None

-   Outbound: Allow HTTPS (443)

![](./images/fd2b4b66b185eb7c8d60bea171a01188e59e0f54.png){width="6.5in" height="3.3229166666666665in"}

#### **VPC Endpoint**

-   Inbound: HTTPS (443) from VPC CIDR

-   Outbound: Default (allow all)

![](./images/33c7298843e1dc4e7bf6d388691c69dd6d6d73bf.png){width="6.5in" height="3.3229166666666665in"}![](./images/964e883b9eb09f24d3ac00fdf50b152913e3ffc5.png){width="6.5in" height="3.3229166666666665in"}

### **6. Connect via Session Manager**

Navigate:

EC2 → Instance → Connect → Session Manager

![](./images/cd4472043ef76d121f4c58864dbca6f381f8469d.png){width="6.5in" height="3.3229166666666665in"}

OR

Systems Manager → Fleet Manager → Managed Instances

![](./images/678d33a88895ec0fbb5aed96cd83e8de5832ca2a.png){width="6.5in" height="3.3229166666666665in"}

## **Verification**

-   Instance appears under **Managed Instances**

-   Session Manager opens terminal successfully

-   No SSH or public IP required

![](./images/30af715e905fb6dadc80415cad0368b1f25d7482.png){width="6.5in" height="3.3229166666666665in"}

## **Key Benefits**

-   No bastion host required

-   No SSH keys or port 22 exposure

-   Fully private architecture

-   IAM-based access control

-   Audit logging support

## **Optional Enhancements**

-   Enable session logging (CloudWatch / S3)

-   Restrict IAM access to specific users/instances

-   Remove all inbound security group rules

## **Conclusion**

This architecture demonstrates a secure, scalable, and production-ready way to access EC2 instances using AWS-native services without exposing infrastructure to the internet.
