# **Disaster Recovery Setup (AWS)**

## **Overview**

In this project, we implemented a basic Disaster Recovery (DR) setup using AWS services. The aim is to make sure our application can still run even if one AWS region fails.

## **Services Used**

-   Amazon S3

-   Amazon RDS (MySQL)

-   Amazon EC2

-   AMI (Amazon Machine Image)

## **Implementation Steps**

### **1. S3 Cross-Region Replication**

-   Created an S3 bucket in primary region

![](images/be94d93185dec844d00ab7b133a25a724dcc0303.png){width="3.9895833333333335in" height="1.9500371828521434in"}

-   Created another bucket in a different region

![](images/8c121c1c5cba726321f24fdb279217ec51c4a869.png){width="4.416666666666667in" height="2.1587871828521434in"}

-   Enabled versioning on both buckets

![](images/9ff58063af3bb541e9d5ca69bc28fc67ebc0b5ce.png){width="3.284113079615048in" height="1.6052154418197726in"}![](images/ac538fc2b0151e1de7bf74b83060d71a18f37bfd.png){width="3.3035225284339456in" height="1.614702537182852in"}

👉 Now all files uploaded in primary bucket are automatically copied to the secondary region.

![](images/5feecb8ea6e9031699f396b5555117a044f2fba2.png){width="6.5in" height="3.1770833333333335in"}

### **2. RDS Read Replica**

-   Created a primary MySQL RDS instance

-   Added a Read Replica

-   Replica automatically syncs data from primary DB

![](images/18ace9c40d7ebb6b06a21e648e83fa7a6b7f9071.png){width="6.5in" height="3.1770833333333335in"}

👉 Used to handle read traffic and also acts as backup DB.

![](images/47b77eb15261addaa0cda20292f24e90da0815e7.png){width="6.5in" height="3.1666666666666665in"}![](images/ff6a534c75593d2e9c9542bca04eb04909b4d433.png){width="6.5in" height="3.1666666666666665in"}

### **3. AMI Backup**

-   Created an AMI of the EC2 instance

-   AMI stores OS + installed apps + configuration

Can launch a new EC2 instance anytime using this AMI.

![](images/be4d09227b52765e0617c3e13fbbe288ef19bc5d.png){width="5.770833333333333in" height="2.82992782152231in"}

### **4. Simulating Region Failure**

-   Stopped primary EC2 instance

-   Stopped primary RDS database

-   Launched new EC2 instance using AMI

![](images/24d0b1a8f2a80db902c8658fcee613b699add74a.png){width="5.010416666666667in" height="2.457030839895013in"}

-   Accessed from new EC2 launched through AMI:

    -   Data from S3 replicated bucket

> ![](images/db9b41c9a890e3a3c05333f52b131846c78ea81c.png){width="4.958333333333333in" height="0.8820111548556431in"}

-   Data from RDS read replica

> ![](images/9b6d1ade6cbcb62e8fe92582a71c1a7ce450b831.png){width="6.5in" height="3.15625in"}

## **Conclusion**

This setup provides a simple disaster recovery solution:

-   S3 ensures file backup across regions

-   RDS Read Replica provides database failover option

-   AMI helps quickly restore servers
