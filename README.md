# CloudApp – Full DevOps Project (AWS + Terraform + CI/CD)

This project is a full cloud infrastructure setup built using AWS services, Terraform, GitHub Actions, EC2, RDS, S3, and CloudFront. It is designed to simulate a real DevOps environment with automation, monitoring, security, CI/CD, and cost optimization.

## 🚀 Architecture Overview
- **Frontend:** S3 + CloudFront (HTTPS enforced)
- **Backend:** EC2 instance
- **Database:** RDS MySQL (private, not public)
- **Monitoring:** CloudWatch logs + metrics + dashboard
- **Automation:** Terraform infrastructure + GitHub Actions CI/CD
- **Security:** IAM least-privilege, SG hardening, access key rotation

## 📂 Repository Structure

Frontend → S3 → CloudFront  
Backend → EC2 → CloudWatch  
Database → RDS  

Terraform manages:
- EC2  
- RDS  
- S3  
- IAM  
- Security groups  
- CloudWatch  

## 🔒 Security
- RDS is **not public**
- Security groups allow **only required traffic**
- IAM policy for GitHub Actions is **least privilege**
- Access keys rotated
- HTTPS forced using CloudFront

## 💸 Cost Optimization
- EC2 → t3.micro  
- RDS → db.t4g.micro  
- S3 lifecycle rules enabled  
- Estimated monthly cost: **₹2000–₹2800**

## 🧑‍💻 Author
**Piyush Khobragade**

