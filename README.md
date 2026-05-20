# EC2-Reverse-Proxy-NGINX-Deployment-with-Terraform
A fully automated Terraform configuration that deploys an NGINX reverse proxy on an Amazon EC2 instance inside a production‑ready AWS VPC. This project demonstrates real‑world Infrastructure‑as‑Code skills, including custom networking, security hardening, automated server provisioning, and reproducible cloud environments.

![Terraform](https://img.shields.io/badge/Terraform-844FBA?style=for-the-badge&logo=terraform&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![EC2](https://img.shields.io/badge/AWS_EC2-FF9900?style=for-the-badge&logo=amazonec2&logoColor=white)
![NGINX](https://img.shields.io/badge/NGINX-009639?style=for-the-badge&logo=nginx&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

What This Project Does
Builds a custom VPC (10.0.0.0/16) with DNS support

Creates public and private subnets for scalable architectures

Attaches an Internet Gateway and configures routing

Deploys an EC2 instance in the public subnet

Uses user‑data to automatically install and start NGINX

Configures NGINX as a reverse proxy (forwarding HTTP traffic)

Applies a security group allowing inbound HTTP (80)

Outputs the public IP and URL for immediate access
