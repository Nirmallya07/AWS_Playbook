# **EBS Snapshot and Volume Restoration Demo (AWS EC2)**

## **Objective**

This project demonstrates how to:

- Launch an EC2 instance

- Create files and directories

- Take a snapshot of an EBS volume

- Create a new EBS volume from the snapshot

- Attach it to an EC2 instance

- Verify that the data persists

## **Architecture Overview**

- EC2 Instance (Linux)

- Original EBS Volume

- EBS Snapshot

- Restored EBS Volume

## **Step 1: Launch EC2 Instance**

1.  Go to AWS Console → EC2 → Launch Instance

2.  Configure:

    1.  AMI: Amazon Linux or Ubuntu

    2.  Instance Type: t2.micro

    3.  Key Pair: Create or select an existing key pair

3.  Launch the instance

<img src="images/1cb55e637e05b4df9c1ed67af686ec8408e40784.png"
style="width:6.5in;height:3.1875in" />

## **Step 2: Connect to the Instance**

<img src="images/70760e787ceaf8d273944c675cdde27e24101c6c.png"
style="width:6.5in;height:3.1875in" />

## **Step 3: Create Files and Directories**

mkdir demo_dir  
cd demo_dir  
echo "Hello from original volume" \> file1.txt  
echo "Snapshot test data" \> file2.txt  
mkdir sub_dir  
touch sub_dir/file3.txt

<img src="images/a26c3b0b72e22b69b05988c8ce269c42fb50eefa.png"
style="width:6.5in;height:3.1875in" />

## **Step 4: Identify the EBS Volume**

1.  Go to EC2 Dashboard → Instances

2.  Select your instance → Storage tab

3.  Note the Volume ID attached (root volume)

4.  Click Actions → Create Snapshot

5.  Provide a name and create the snapshot

<img src="images/9f3beeb2801d66505e7655ac49838d84a35db791.png"
style="width:6.5in;height:3.1875in" />

## **Step 6: Create New Volume from Snapshot**

1.  Go to EC2 → Snapshots

2.  Select the snapshot

3.  Click Actions → Create Volume

4.  Create the volume

<img src="images/b041c008cd3588892dc623bef3fff39b4e350e69.png"
style="width:6.5in;height:3.1875in" />

## **Step 7: Attach New Volume to EC2 Instance**

1.  Go to EC2 → Volumes

2.  Select the new volume

3.  Click Actions → Attach Volume

4.  Choose the instance

5.  Device name example:

<img src="images/077924f27e533690a433995435f5da85513d6075.png"
style="width:6.5in;height:3.1875in" />

## **Step 9: Verify Files**

<img src="images/30924ea7a579145ccdfba077e4b98827ee647a97.png"
style="width:6.5in;height:3.08333in" />

Expected: All previously created files and directories should be
present.
