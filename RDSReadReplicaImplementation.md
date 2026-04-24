# **RDS Read Replica Implementation (Simple Guide)**

## **Aim**

To create a MySQL RDS primary database, add a read replica, and test read-heavy workload.

## **What we are doing**

-   Create primary RDS MySQL

-   Add Read Replica

-   Separate read and write traffic

-   Simulate heavy read load

## **Step 1: Create Primary RDS**

1.  Go to RDS Console

2.  Click **Create Database**

3.  Choose:

    a.  Engine: MySQL

> ![](images/7a9dd7bf6ac3cf511c17719dd254a418313f279b.png){width="6.5in" height="3.1666666666666665in"}

### **Fill details**

-   DB identifier: as you wish

-   Username: admin

-   Password: set password\
    \
    ![](images/c3e2f8b334413f9220794566b003c44369620a2c.png){width="6.25in" height="3.0416666666666665in"}

### **Settings**

-   Enable backups ✔

-   Public access: No\
    ![](images/5a81d79749a843a360f76bed18975e9823d3e163.png){width="6.25in" height="3.0416666666666665in"}

4.  Click Create

## **Step 2: Create Read Replica**

1.  Select your primary DB

2.  Click **Actions → Create read replica**

3.  Give name: read-replica-db

4.  Choose same VPC

5.  Click Create\
    \
    ![](images/01c0954715a35d44ca235d3ac909195d56545252.png){width="6.25in" height="3.0416666666666665in"}![](images/ebb291cd4b242b21af5f1c2b29f45661b187df59.png){width="6.25in" height="3.0416666666666665in"}

![](images/b67846b91752f0f55b43fdee21935efe95e22a17.png){width="6.5in" height="3.1666666666666665in"}

## **Step 3: Understand Endpoints**

-   Primary DB → used for **write operations (INSERT, UPDATE, DELETE)**

-   Read Replica → used for **read operations (SELECT)**

## **Step 4: Connect from EC2**

### **Install MySQL client**

sudo apt update

sudo apt install mysql-client -y

### **Connect to primary (write)**

mysql -h \<primary-endpoint\> -u admin --p\
\
![](images/78ea35031ab01a27a7fdfacaf8500c1dc538630b.png){width="6.5in" height="3.1666666666666665in"}

### **Connect to replica (read)**

mysql -h \<replica-endpoint\> -u admin --p\
\
![](images/fd219dc0be21c979641374a8cf9ace60db52a5f4.png){width="6.5in" height="3.1666666666666665in"}

## **Step 5: Simulate Heavy Read Load**

Run multiple read queries:

while true; do

mysql -h \<replica-endpoint\> -u admin --p'YOURPASS' -e \"SELECT \* FROM your_table;\"

Done

![](images/71d87143c698401fba641021f82c5c74bd989cb0.png){width="6.5in" height="0.3333333333333333in"}

![](images/c321b12ca5ddfc990b321e3cf935cf9aaa16fd4e.png){width="6.5in" height="2.2083333333333335in"}

Or open multiple terminals and run SELECT queries.

## **Step 7: Verify**

-   Data written in primary should appear in replica

![](images/375f607e24921f18a9b4b35d38ac7f1621785fa0.png){width="6.5in" height="2.90625in"}

-   Replica handles read traffic![](images/25ca08e8b8ea74bbefeeeb40d7538d874f38dfd4.png){width="6.5in" height="2.90625in"}

We can see that new data inserted in primary db and the read replica has started showing up the same new data.

## **Notes**

-   Helps improve performance for read-heavy apps

-   Can scale by adding more replicas

## **Conclusion**

We created a primary RDS MySQL database, added a read replica, and tested read-heavy workload by sending SELECT queries to the replica.
