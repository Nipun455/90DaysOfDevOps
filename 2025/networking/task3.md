AWS EC2 and Security Groups
This document is focuses on launching an Amazon EC2 instance and configuring Security Groups to secure your cloud instance. Amazon EC2 (Elastic Compute Cloud) is a scalable compute service provided by AWS, while Security Groups act as virtual firewalls that control inbound and outbound traffic.

Prerequisites
An active AWS account
Basic understanding of networking concepts (IP addresses, ports, and protocols)
Step 1: Launch an AWS EC2 Instance
Sign in to AWS Console
Go to AWS Management Console
Navigate to the EC2 service (by Searching)
Ensure you're in your desired AWS region
Instance Configuration
Click "Launch Instance"

Configure basic details:

Name: Provide a meaningful name for your instance
Tags: Add relevant tags for resource management
Choose Amazon Machine Image (AMI):

Select "Ubuntu Server 22.04 LTS (HVM)"
Filter for "Free tier eligible" if needed
Select Instance Type:

Choose "t2.micro" (Free tier eligible)
vCPU: 1
Memory: 1 GiB
Network Settings:

VPC: Select your VPC
Subnet: Choose a public subnet
Auto-assign Public IP: Enable
3. Configure Key Pair
When prompted to select a key pair, you can either:

Create a new key pair:

Provide a key pair name.

Select RSA as the key type and PEM as the file format.

Private key file format: .pem (for OpenSSH) or .ppk (for PuTTY)
Download the key pair file. Keep it secure as it is required for SSH access.

Linux/macOS: Store in ~/.ssh/ with permissions chmod 400
Windows: Store in a secure location
Use an existing key pair:

Select from previously created key pairs if available.
Step 2: Configure Security Groups
Security Groups act as virtual firewalls that control traffic to and from your instance.

Inbound Rules
Inbound rules define what traffic is allowed to reach your instance.

Allow SSH Access:

Protocol: TCP
Port Range: 22
Source: Custom IP range (Recommended) or Anywhere (0.0.0.0/0) (less secure)
Description: SSH access from approved IPs
Allow HTTP Traffic: (if needed)

Protocol: TCP
Port Range: 80
Source: Anywhere (0.0.0.0/0)
Description: Web access
Allow HTTPS Traffic: (if needed)

Protocol: TCP
Port Range: 8443
Source: Anywhere (0.0.0.0/0)
Description: Secure web access
Outbound Rules
Default outbound rule (recommended for most cases):

Type: All traffic
Protocol: All
Port Range: All
Destination: 0.0.0.0/0
Step 3: Launch the Instance and Connect
Review and Launch:

Review your configuration and click "Launch Instance"
Wait for the instance to become "Running"
Note the public IP address
Connect to the Instance:

Once the instance is running, click Connect.
-Use the provided instructions to connect via SSH.

Example command for SSH:

chmod 400 path/to/your-key-pair.pem
ssh -i "path/to/your-key-pair.pem" ubuntu@your-instance-public-ip
Conclusion
You have successfully launched an AWS EC2 instance and configured its Security Groups. Proper configuration of Security Groups is essential for maintaining the security of your cloud environment.

Additional Resources
AWS EC2 Documentation
AWS Security Groups Documentation
Hashnode Blog
A more detailed and beginner-friendly blog on this topic is available on Hashnode. It provides step-by-step instructions, screenshots, and best practices for configuring Security Groups and launching EC2 instances.
