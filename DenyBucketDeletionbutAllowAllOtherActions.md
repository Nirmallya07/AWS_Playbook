# **Deny Bucket Deletion but Allow All Other Actions**

## **Objective**

Create an IAM policy that:

- Allows all Amazon S3 actions

- Explicitly denies deletion of S3 buckets

## **Key Concepts**

- IAM policies follow **Allow** and **Deny** rules

- **Explicit Deny overrides Allow**

- Fine-grained control is achieved by targeting specific actions

- Preventing bucket deletion helps protect critical data

<img src="images/ce4f827070b53ab7cc523b78d6104376626f3266.png"
style="width:6.5in;height:3.08333in" /><img src="images/30a31da4fe01a09c0dbd1ba5adefbd6e9eccb7b7.png"
style="width:6.5in;height:3.08333in" />
