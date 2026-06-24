<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launching VPC Resources

**Project Link:** [View Project](http://nextwork.ai/projects/aws-networks-ec2)

**Author:** Sheika Abuthair  
**Email:** sheikaabuthaircyber11@gmail.com

---

## Launching VPC Resources

![Image](http://nextwork.ai/compassionate_red_daring_abiu/uploads/aws-networks-ec2_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) is an AWS service that allows you to create a private, isolated network environment in the cloud where you can run AWS resources like EC2 instances, databases, and applications.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to build a complete cloud network environment. I created a VPC with public and private subnets, configured route tables, an Internet Gateway, and NAT Gateway for traffic management, and used security groups and network ACLs to control access and secure resources. I also launched public and private EC2 instances inside the VPC to understand how AWS separates internet-facing resources from internal resources while maintaining secure communication.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was...

### This project took me...

This project took me 45 Mins

---

## Setting Up Direct VM Access

Directly accessing your EC2 instance means connecting to your virtual server from your computer over the internet and interacting with it as if you are using a physical machine.

For a public EC2 instance, this usually means using SSH with your key pair to log in to the server using its public IP address. Once connected, you can run commands, install software, manage files, and configure the server.

Example:

Your laptop → Internet → EC2 public IP → EC2 instance

In simple terms: Direct access means you can connect to and control your EC2 instance from outside AWS using a secure connection.

### SSH is a key method for directly accessing a VM

SSH (Secure Shell) is a secure network protocol used to connect remotely to a server or EC2 instance and control it through a command line.

### To enable direct access, I set up key pairs

A key pair in AWS is a security credential used to securely connect to an EC2 instance. It consists of two parts:

Public key: Stored by AWS and placed on the EC2 instance.
Private key: Downloaded by you and used to authenticate your connection.

When you connect to an EC2 instance (for example, using SSH), AWS checks that your private key matches the public key on the instance. If they match, you are allowed access.

In simple terms: A key pair works like a digital password that securely proves you are allowed to access your EC2 server. 🔐

A private key file is a file that is used to securely authenticate and connect to an EC2 instance. AWS provides the private key when you create a key pair.

The common private key file formats are:

.pem (Privacy Enhanced Mail) → Commonly used with Linux, macOS, and OpenSSH connections.
.ppk (PuTTY Private Key) → Used with PuTTY on Windows.

---

## Launching a public server

edited my EC2 instance's networking settings through the AWS Management Console by modifying the instance configuration. I selected the EC2 instance, updated its VPC, subnet, security group, and network settings, and configured it to run inside the required public subnet.

![Image](http://nextwork.ai/compassionate_red_daring_abiu/uploads/aws-networks-ec2_88727bef)

---

## Launching a private server

Your private server uses a different security group from your public server because both servers have different security requirements and purposes.

The public server needs to allow limited internet access (for example, SSH or web traffic) because it is exposed to users outside the VPC.

The private server should not be directly accessible from the internet, so its security group only allows required communication from trusted sources, such as the public server or internal VPC resources.

Using separate security groups follows the principle of least privilege and helps keep private resources more secure.

The source of my new security group is the public subnet's network range (CIDR block). This allows traffic only from resources located in the public subnet while blocking unwanted access from other networks. This setup helps the private server communicate with the public-facing resources while keeping it protected from direct internet access.

![Image](http://nextwork.ai/compassionate_red_daring_abiu/uploads/aws-networks-ec2_4a9e8014)

---

## Speeding up VPC creation

I set up my new VPC using the AWS VPC creation wizard, which automatically created the required networking components. I configured the VPC with the required CIDR range, public and private subnets, route tables, and Internet Gateway. AWS then connected these components together to create a complete network environment, making it faster and easier to deploy compared to creating each resource manually.

A VPC resource map is a visual representation in AWS that shows all the resources inside a VPC and how they are connected. It helps you understand the network architecture by displaying components like VPC, subnets, route tables, Internet Gateway, NAT Gateway, and security configurations.

In simple terms, a VPC resource map works like a network diagram that shows how traffic flows between different AWS networking components and helps with troubleshooting and managing your VPC setup.

Your new VPC can have the same IPv4 CIDR block as the NextWork VPC because the two VPCs are separate and isolated networks. Each VPC has its own private networking environment, so the same IP address range can be reused in different VPCs without conflict.

However, if you try to connect these VPCs together (for example, using VPC Peering or a Transit Gateway), overlapping CIDR blocks can cause routing conflicts, so each connected VPC should have a unique IP range.

![Image](http://nextwork.ai/compassionate_red_daring_abiu/uploads/aws-networks-ec2_1cbb1b88)

---

## Speeding up VPC creation

### Tips for using the VPC resource map

The number of public subnets you can create depends on the IP address range (CIDR block) of your VPC and the number of available IP addresses.

In AWS, a VPC can have multiple public subnets across different Availability Zones. There is no fixed limit based only on being public; AWS allows you to create many subnets as long as they fit within your VPC CIDR range and service limits.

For example, if your VPC has a CIDR block like 10.0.0.0/16, you can divide it into multiple smaller subnet ranges and create multiple public subnets. Each public subnet would need a route to the Internet Gateway through a public route table.

A NAT Gateway (Network Address Translation Gateway) is an AWS service that allows resources in a private subnet to access the internet for outbound connections while preventing direct inbound access from the internet.

![Image](http://nextwork.ai/compassionate_red_daring_abiu/uploads/aws-networks-ec2_8ee57662)

---

---
