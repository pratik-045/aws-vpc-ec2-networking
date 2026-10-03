# AWS VPC + EC2 Networking

## Project Overview

This project demonstrates how to create a basic AWS network using Amazon VPC and deploy a web server on an EC2 instance.

I created a VPC with a public subnet, Internet Gateway, Route Table, Security Group, and EC2 instance. I then deployed an Nginx web server and hosted a custom HTML webpage.

## AWS Services Used

* Amazon VPC
* Amazon EC2
* Internet Gateway
* Route Table
* Security Group

## Technologies Used

* Amazon Linux
* Linux
* Nginx
* HTML
* AWS Networking

## Architecture

```text
Internet
    │
    ▼
Internet Gateway
    │
    ▼
Route Table
    │
    ▼
Public Subnet
    │
    ▼
EC2 Instance
    │
    ▼
Nginx Web Server
    │
    ▼
Custom HTML Website
```

##  Implementation

### 1. Create VPC

Created a VPC with:

* Name: `pratik-vpc`
* CIDR: `10.0.0.0/16`

### 2. Create Public Subnet

Created a public subnet:

* Name: `pratik-public-subnet`
* CIDR: `10.0.1.0/24`

### 3. Create Internet Gateway

Created and attached an Internet Gateway:

* Name: `pratik-igw`
* Attached to: `pratik-vpc`

### 4. Configure Route Table

Created:

* Name: `pratik-public-rt`

Added the internet route:

```text
0.0.0.0/0 → Internet Gateway
```

Associated the route table with `pratik-public-subnet`.

### 5. Configure Security Group

Created:

* Name: `pratik-web-sg`

Inbound rules:

| Protocol | Port | Source    |
| -------- | ---: | --------- |
| SSH      |   22 | My IP     |
| HTTP     |   80 | 0.0.0.0/0 |

### 6. Launch EC2

Launched an Amazon Linux EC2 instance inside:

```text
VPC: pratik-vpc
Subnet: pratik-public-subnet
Security Group: pratik-web-sg
```

Enabled a public IPv4 address.

### 7. Install Nginx

Installed Nginx:

```bash
sudo dnf install nginx -y
```

Started the service:

```bash
sudo systemctl start nginx
```

Enabled Nginx at boot:

```bash
sudo systemctl enable nginx
```

Verified the service:

```bash
sudo systemctl status nginx
```

Nginx was successfully running.

### 8. Deploy Custom Webpage

Created a custom HTML webpage at:

```text
/usr/share/nginx/html/index.html
```

The webpage was accessed using the EC2 public IP address.

## Project Screenshots

### 1. VPC

Shows the `pratik-vpc` configuration.

### 2. Public Subnet

Shows the `pratik-public-subnet` configuration.


### 3. Internet Gateway

Shows the Internet Gateway attached to the VPC.

### 4. Route Table

Shows the route:

```text
0.0.0.0/0 → Internet Gateway
```

### 5. Live Website

Shows the custom webpage deployed on the EC2 instance.

## What I Learned

* How AWS VPC networking works
* How to create and configure a subnet
* How an Internet Gateway provides internet connectivity
* How Route Tables control network traffic
* How Security Groups control inbound traffic
* How to launch EC2 inside a custom VPC
* How to deploy an Nginx web server
* How to host a custom HTML webpage on EC2

## Future Improvements

* Add a private subnet
* Deploy an RDS database
* Add an Application Load Balancer
* Add Auto Scaling
* Add CloudWatch monitoring
* Use HTTPS with SSL/TLS

## Author

**Pratik Sambhaji Gorule**

MCA Student | AWS & Cloud Computing | Linux | Python | DevOps Learner
