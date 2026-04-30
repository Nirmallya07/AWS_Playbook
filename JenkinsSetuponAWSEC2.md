# **Jenkins Setup on AWS EC2**

## **Objective**

The purpose of this project is to install and configure Jenkins on an
AWS EC2 instance and access it through a web browser.

## **Steps Performed**

### **1. Launch EC2 Instance**

- Created a new EC2 instance using:

  - **AMI:** Amazon Linux

  - **Instance Type:** t3.micro

- Configured Security Group to allow:

  - Port **22** (SSH)

  - Port **80** (HTTP)

  - Port **8080** (Jenkins)

<img src="images/c4189ac6902fbcdbe04180c38edd03645d038adc.png"
style="width:6.5in;height:3.16667in" />

### **2. Connect to EC2 Instance**

- Connected to the instance using **EC2 Instance Connect**
  (browser-based terminal).

<img src="images/107bf2d796575ea3851dc8ccb1341c42409b55b9.png"
style="width:6.5in;height:2.6875in" />

### **3. Install Java and Jenkins**

Updated the system and installed required dependencies:

sudo dnf update -y  
sudo dnf install java-17-amazon-corretto -y  
sudo wget -O /etc/yum.repos.d/jenkins.repo
<https://pkg.jenkins.io/redhat-stable/jenkins.repo>  
sudo rpm --import
<https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key>  
sudo dnf install jenkins -y

### **4. Start Jenkins Service**

Start and enable Jenkins:

sudo systemctl start jenkins  
sudo systemctl enable jenkins  
sudo systemctl status jenkins

<img src="images/feeed65a4e6d372c241e4caea7b8edf33467a421.png"
style="width:6.5in;height:2.47917in" />

### **5. Access Jenkins in Browser**

- Open browser and go to:

[http://\<my-instance-public-ip-address\>:8080](http://<my-instance-public-ip-address>:8080)

- Retrieve initial admin password:

sudo cat /var/lib/jenkins/secrets/initialAdminPassword

<img src="images/830f70b404806b41a5b3809bdb88c60911c76a25.png"
style="width:6.5in;height:3.4375in" />

### **6. Install Plugins**

- Selected **"Install Suggested Plugins"**

- Waited for installation to complete

<img src="images/54e34fe9413327ebf9d3a80134635de375e78516.png"
style="width:6.5in;height:3.35417in" />

### **7. Create Admin User**

- Entered:

  - Username

  - Password

  - Email

<img src="images/89c919c99649a65b431456a719463cf9947388c2.png"
style="width:6.5in;height:3.35417in" />

### **8. Jenkins Setup Complete**

- Jenkins dashboard successfully opened

<img src="images/23bcced38529391a343bfced47c951ab7993d200.png"
style="width:6.5in;height:3.19792in" />

## **Result**

Jenkins was successfully installed and configured on an AWS EC2 instance
and is accessible through a web browser.
