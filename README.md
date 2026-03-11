# AWS EC2 Web Server Project

## Project Overview
This project demonstrates the deployment of a public web server on AWS using a custom VPC, public subnet, Internet Gateway, route table, security groups, and an EC2 instance running Apache HTTP Server.

The goal of this project was to build foundational cloud infrastructure manually in AWS and understand how networking, routing, and security components work together to host a live website.

---

## Architecture
The architecture for this project is:

Internet  
→ Internet Gateway  
→ Public Route Table  
→ Public Subnet  
→ EC2 Instance  
→ Apache Web Server

---

## AWS Services Used
- Amazon VPC
- Subnet
- Internet Gateway
- Route Table
- Security Group
- Amazon EC2
- Apache HTTP Server

---

## Configuration Details

### VPC
- Name: `cloud-project-vpc`
- CIDR Block: `10.0.0.0/16`

### Public Subnet
- Name: `public-subnet`
- CIDR Block: `10.0.1.0/24`

### Route Table
- Route: `0.0.0.0/0 → Internet Gateway`

### Security Group
- SSH (22) from trusted IP
- HTTP (80) from anywhere

### EC2 Instance
- Amazon Linux 2023
- Instance type: `t3.micro`

---

## Deployment Steps
1. Created a custom VPC with CIDR block `10.0.0.0/16`
2. Created a public subnet with CIDR block `10.0.1.0/24`
3. Created and attached an Internet Gateway to the VPC
4. Created a route table and added a default route to the Internet Gateway
5. Associated the public subnet with the public route table
6. Launched an EC2 instance inside the public subnet
7. Configured the security group to allow SSH and HTTP
8. Connected to the EC2 instance and installed Apache
9. Hosted a custom web page using Apache

---

## Commands Used

```bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
echo "<h1>Umesh Cloud Project</h1><p>My first AWS web server is live.</p>" | sudo tee /var/www/html/index.html
