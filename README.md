# EC2-Reverse-Proxy-NGINX-Deployment-with-Terraform
A fully automated Terraform configuration that deploys an NGINX reverse proxy on an Amazon EC2 instance inside a production‑ready AWS VPC. This project demonstrates real‑world Infrastructure‑as‑Code skills, including custom networking, security hardening, automated server provisioning, and reproducible cloud environments.

![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=for-the-badge&logo=terraform&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![EC2](https://img.shields.io/badge/AWS_EC2-FF9900?style=for-the-badge&logo=amazonec2&logoColor=white)
![NGINX](https://img.shields.io/badge/NGINX-009639?style=for-the-badge&logo=nginx&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)


📌 Overview
This project automates the deployment of:

A custom VPC with DNS support

Public and private subnets for scalable architectures

Internet Gateway and route tables

Security groups hardened for HTTP‑only ingress

EC2 instance running NGINX as a reverse proxy

Automated provisioning via user‑data

Terraform outputs for public IP and URL

It follows production patterns for modularity, security, and future extensibility.



                   AWS Cloud
───────────────────────────────────────────────
                    VPC (10.0.0.0/16)
───────────────────────────────────────────────
        │                         │
 Public Subnet             Private Subnet
 10.0.2.0/24                10.0.1.0/24
   │                             │
 EC2 + NGINX                (Future backend)
   │
 Internet Gateway
   │
 Route Table (0.0.0.0/0 → IGW)


Terraform – EC2 Reverse Proxy with NGINX (VPC, Subnets, IGW)
A fully automated Terraform configuration that deploys an EC2 instance running NGINX, inside a custom VPC, with public/private subnets, Internet Gateway, route table, and security groups.
The EC2 instance is automatically configured using user‑data to install and start NGINX.

🚀 Project Overview
This project provisions:

A custom VPC (10.0.0.0/16)

Public subnet (10.0.2.0/24) with auto‑assign public IP

Private subnet (10.0.1.0/24)

Internet Gateway

Route table with default route to IGW

Security group allowing inbound HTTP (80)

EC2 instance (Amazon Linux 2) running NGINX via user‑data

Terraform outputs for:

Public IP

Public URL

📂 Project Structure
Code
terraform/
│── main.tf
│── Providers.tf
│── VPC.tf
│── security_groups.tf
│── EC2.tf
│── outputs.tf
│── .env
⚙️ Prerequisites
AWS account

IAM user with programmatic access

Terraform v1.x

AWS CLI configured (aws configure)

SSH key pair (optional if you add key_name)

🛠️ How to Deploy
1. Initialize Terraform
Code
terraform init
2. Validate configuration
Code
terraform validate
3. Preview changes
Code
terraform plan
4. Apply infrastructure
Code
terraform apply
Type yes when prompted.

🌐 Outputs
After apply, Terraform prints:

instance_public_ip → Public IPv4

instance_url → http://<public-ip>

Example:

Code
instance_public_ip = "100.54.68.21"
instance_url       = "http://100.54.68.21"


🧩 How NGINX Is Installed
Your EC2 instance uses Terraform user_data to install and start NGINX automatically:

“user_data = … installs nginx and starts the service on boot.”

This ensures the server is reachable immediately after provisioning.


🔐 Security Group Rules
Inbound:

TCP 80 → 0.0.0.0/0

Outbound:

All traffic allowed



🏗️ Architecture Diagram (Conceptual)
Code
                Internet
                    │
            ┌────────────────┐
            │ Internet GW    │
            └────────────────┘
                    │
            ┌────────────────┐
            │  Route Table   │
            │ 0.0.0.0/0 → IGW│
            └────────────────┘
                    │
        ┌──────────────────────────┐
        │        Public Subnet     │
        │   EC2 + NGINX (HTTP 80)  │
        └──────────────────────────┘


📜 Outputs & Verification
Visit the instance URL:

Code
http://<instance_public_ip>
You should see the NGINX welcome page.

📌 Next Steps
Add reverse proxy configuration in /etc/nginx/nginx.conf

Add SSL/TLS using Let’s Encrypt

Add ALB or CloudFront for production

Add Terraform variables for reusability

Troubleshooting help:
Debug Terraform apply issues.

🛑 Destroying Infrastructure
To remove all resources:

Code
terraform destroy
