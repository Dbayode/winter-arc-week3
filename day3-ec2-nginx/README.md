# Day 18/90 — AWS EC2 Web Server Deployment

## Project Overview

This project demonstrates how to deploy and configure
a web server on an Amazon EC2 instance using Amazon Linux
and Nginx.

It is part of my 90-Day DevOps Winter Arc challenge.

## Technologies Used

- Amazon EC2
- Amazon Linux
- Nginx
- SSH
- Linux
- Git
- GitHub

## Project Architecture

```text
Local Ubuntu Machine
        |
        | SSH
        v
Amazon EC2 Instance
        |
        v
Amazon Linux
        |
        v
Nginx Web Server
        |
        v
Static Website
        |
        v
Public IP Address
```

## Implementation

### 1. Launch EC2 Instance

Created an Amazon Linux EC2 instance through
the AWS Management Console.

### 2. Connect Using SSH

```bash
ssh -i ~/.ssh/devops-winter-arc.pem ec2-user@PUBLIC_IP
```

### 3. Install Nginx

```bash
sudo dnf update -y
sudo dnf install nginx -y
```

### 4. Start Nginx

```bash
sudo systemctl enable --now nginx
```

### 5. Deploy Website

Placed the HTML website in:

```text
/usr/share/nginx/html/index.html
```

### 6. Verify Deployment

```bash
sudo systemctl status nginx
curl -I http://localhost
```

### 7. Configure Networking

Configured the EC2 security group to allow:

- SSH (22) from my IP address.
- HTTP (80) for public website access.

## Challenges Encountered

### HTTPS Connection Failure

Initially encountered a connection failure
when testing localhost on port 443.

The issue occurred because HTTPS had not
been configured.

Resolved by testing the HTTP endpoint:

```bash
curl -I http://localhost
```

## Key Lessons

- EC2 provides cloud-based virtual machines.
- SSH enables secure remote administration.
- Security groups control inbound traffic.
- Nginx serves static web content.
- HTTP and HTTPS use different ports.
- Git and GitHub support project version control.

## Future Improvements

- Configure HTTPS using a domain and TLS certificate.
- Automate deployment using GitHub Actions.
- Implement infrastructure as code using Terraform.
- Explore EBS snapshots and recovery.

## Challenge

Day 18 of 90 — DevOps Winter Arc

Learn → Build → Deploy → Repeat.
