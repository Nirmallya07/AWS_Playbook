# **S3 Lifecycle Rule Configuration**

## **Objective**

The objective of this task was to create and configure a lifecycle rule
in an Amazon S3 bucket to automatically manage stored objects and reduce
storage costs.

## **Steps Performed**

### **1. Access S3 Service**

- Logged into the AWS Management Console

- Navigated to the S3 service

<img src="images/a44b2ea191aa1384c82f796d1a17aefad626f0d7.png"
style="width:6.5in;height:3.4375in" />

### **2. Create Lifecycle Rule**

- Opened the target S3 bucket

- Navigated to the Management tab

- Selected Create lifecycle rule

<img src="images/510daf38cb710ecb3efa740c2952fc9393b67635.png"
style="width:6.5in;height:3.4375in" />

### **3. Configure Rule Details**

- Entered the rule name: uploads-smart-lifecycle

- Applied the rule to objects with the prefix: uploads/

### **4. Set Expiration Policy**

- Enabled expiration for objects

- Set expiration period to 365 days

<img src="images/72f5aec078e6a4e8409e379d22e7e151c2c00f41.png"
style="width:6.5in;height:3.4375in" />

<img src="images/24b6a402a7b064c109b3871dd86382b3d877f1fd.png"
style="width:6.5in;height:3.4375in" />

### **5. Verify Lifecycle Rule**

- Confirmed that the lifecycle rule was successfully created

- Verified its visibility in the bucket configuration

<img src="images/baac4f8c78f6f622171ae6976a93365107cf17f9.png"
style="width:6.5in;height:3.4375in" />

## **Result**

The lifecycle rule was successfully created and configured. It
automatically manages objects within the specified prefix and helps
optimize storage costs.
