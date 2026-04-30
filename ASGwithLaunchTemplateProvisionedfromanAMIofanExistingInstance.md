The purpose of this task was to provision a virtual server using Amazon
Web Services and configure it as a web server by installing Nginx. After
validating the server with a custom web page, an image of the instance
was created and used to define a reusable launch configuration. Finally,
an Auto Scaling setup was implemented to automatically manage multiple
instances based on demand.

## **Steps Performed**

- Logged in to the AWS Management Console and navigated to the EC2
  dashboard.

- Initiated instance creation using the **Launch Instance** option.

- Selected the **Amazon Linux AMI** and configured the instance type as
  **t3.micro**.

- Generated a new key pair and downloaded the .pem file for secure
  access.

- Configured network settings to allow inbound HTTP (port 80) traffic
  for browser access.

- Launched the instance and waited until it reached the **Running**
  state.

- Connected to the instance using **EC2 Instance Connect**.

- Installed the Nginx web server using:

sudo apt install nginx -y

- Started the Nginx service:

sudo systemctl start nginx

- Verified that the service was running correctly.

- Modified the default HTML page to include custom content.

- Accessed the application via the instance’s public IP address in a
  browser to confirm successful deployment.

- Created an **AMI (Amazon Machine Image)** from the configured EC2
  instance.

- Used the AMI to define a **Launch Template**.

- Created an **Auto Scaling Group** based on the launch template.

- Configured scaling parameters including minimum, desired, and maximum
  instance counts.

- Validated that multiple instances were automatically provisioned and
  managed by the Auto Scaling Group.

<img src="images/f51619e4e180d54cde09706eae3942aa8967a0ef.png"
style="width:6.5in;height:3.02083in" /><img src="images/6ecb318628d65fdeba4c2109d0a293c5eccf7b16.png"
style="width:6.5in;height:1.60417in" /><img src="images/0ffe7023e14d8e784758010b21865a0e0883436d.png"
style="width:6.5in;height:3.625in" /><img src="images/1dc94ce847475beea1b9ffd49bad59770a9706b1.png"
style="width:6.5in;height:3in" /><img src="images/80621fe66e7d0d247e9ebf69f2bb87605853ee15.png"
style="width:6.5in;height:3.19792in" /><img src="images/13c3e8c9f752174793f7d1f58c2e18db381d8f97.png"
style="width:6.5in;height:3.19792in" /><img src="images/ee60d6453d72156eeb47a5e060ac95e7d1ab2d55.png"
style="width:6.5in;height:3.19792in" /><img src="images/c4c9befff2906ee7fcb7acac8345f3b28c1c5e75.png"
style="width:6.5in;height:3.19792in" /><img src="images/3a107c475b56ec324183af77dea5f487d9c0454d.png"
style="width:6.5in;height:3.02083in" />
