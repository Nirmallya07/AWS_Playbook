# **Hub-and-Spoke VPC Architecture (AWS)**

## **Overview**

In this project, I created a Hub-and-Spoke network architecture using AWS VPCs.

-   1 Hub VPC (central network)

-   2 Spoke VPCs (connected to hub)

-   VPC Peering used for connectivity

-   Route tables used to control traffic flow

## **Objectives**

-   Spoke1 can communicate with Hub

-   Spoke2 can communicate with Hub

-   Spoke1 CANNOT communicate with Spoke2

-   Traffic control done using route tables

## **Steps Performed**

### **1. Created VPCs**

-   Hub VPC to CIDR: 10.0.0.0/16

-   Spoke1 VPC to CIDR: 10.1.0.0/16

-   Spoke2 VPC to CIDR: 10.2.0.0/16

![](images/8761ee3a4f6d68f87815cda7111adc971f5787a4.png){width="6.5in" height="3.15625in"}

### **2. Created Subnets**

Each VPC has at least one subnet:

Hub VPC

![](images/4e688ca555237d461bbfe6da3a38dd335cddae25.png){width="6.5in" height="3.15625in"}\
\
Spoke1 VPC

![](images/d0b78fd565884ddc462efd1d6ad997778107eeac.png){width="6.5in" height="3.15625in"}

Spoke2 VPC

![](images/e067a4787a93c4e04d308b529cfbada81ff0c4a7.png){width="6.5in" height="3.15625in"}

### **3. Created VPC Peering Connections**

-   Hub \<-\>Spoke1

-   Hub \<-\> Spoke2

![](images/fc5762f8ee00c2e29ea0de432d1a5e232bac9984.png){width="6.5in" height="3.15625in"}

Accepted both peering requests.

### **4. Updated Route Tables**

#### **For Hub VPC:**

-   Route to Spoke1 to via Peering1

-   Route to Spoke2 to via Peering2

![](images/f4425a756fd3b1d7a5f602aaa7ab95992c19d765.png){width="6.5in" height="3.15625in"}

#### **For Spoke1 VPC:**

-   Route to Hub to via Peering1

![](images/a7bf0c78cb8c6a76464ee56b2b975acfd7c6fbf3.png){width="6.5in" height="3.15625in"}

#### **For Spoke2 VPC:**

-   Route to Hub to via Peering2

![](images/916f7c70bcf425a1a4a573d82757d12ec0315b76.png){width="6.5in" height="3.15625in"}

No routes added between Spoke1 and Spoke2

## **Traffic Control Logic**

-   Hub to Spoke1 Allowed

![](images/6be5e6af757ddb14fedb34fb100a04426edd10f6.png){width="4.78125in" height="2.949970472440945in"}

-   Hub to Spoke2 Allowed

![](images/c214e8c2f0535fa047ed12fef03cc61bdb483844.png){width="6.5in" height="4.010416666666667in"}

-   Spoke1 to Hub Allowed

![](images/5e75721865ededcc1cfb8905ef6a447d8ae18dbe.png){width="6.5in" height="2.7708333333333335in"}

-   Spoke2 to Hub ALLOWED

![](images/70225332d94479bb3da8434ba80a5f86bfad1fed.png){width="6.5in" height="2.5in"}

-   Spoke1to Spoke2 Blocked (No route exists) Not ALLOWED

![](images/1b87a6eea357052581b12e39a1dc57b4bd2b6b3a.png){width="6.5in" height="2.09375in"}

## **Conclusion**

This project demonstrates how Hub-and-Spoke architecture works in AWS using VPC Peering and route tables.

It also shows how traffic can be controlled by simply managing routes instead of complex configurations.
