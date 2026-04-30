# **Allow VPC Creation but Deny Internet Gateway Creation**

## **Objective**

Create an IAM policy that:

- Allows creation of Virtual Private Clouds (VPCs)

- Denies creation of Internet Gateways

## **Key Concepts**

- IAM policies define permissions using **Allow** and **Deny**

- **Explicit Deny overrides Allow**

- AWS services expose fine-grained actions (e.g., ec2:CreateVpc,
  ec2:CreateInternetGateway)

- Restricting specific actions enables tighter network security control

<img src="images/0e45e19683d5257598c50e81ebff1ce94761190a.png"
style="width:6.5in;height:3.08333in" /><img src="images/5726032d51c641a24fe93d2fc89cbe76638752ca.png"
style="width:6.5in;height:3.08333in" />
