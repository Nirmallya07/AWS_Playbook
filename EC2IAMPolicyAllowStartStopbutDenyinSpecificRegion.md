# **EC2 IAM Policy: Allow Start/Stop but Deny in Specific Region**

## **Objective**

Create an IAM policy that:

- Allows starting and stopping EC2 instances

- Denies these actions in a specific AWS region

## **Key Concepts**

- IAM policies use **Allow** and **Deny** statements

- **Explicit Deny overrides Allow**

- Region-based restrictions are implemented using **Condition**

- The condition key used is:

aws:RequestedRegion

<img src="images/bae96a033d38507f34d701f6ffc326cad9943525.png"
style="width:6.22956in;height:2.95505in" /><img src="images/8f77bb5110f63cdcd845cd011d7e9c9b06c3506f.png"
style="width:6.18244in;height:2.9327in" />
