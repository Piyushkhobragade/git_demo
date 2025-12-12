# AWS Cost Optimization Report

## Project: CloudApp DevOps Project
### Date: (auto-generated)
### Author: Piyush Khobragade

---

## 1. Overview
This document summarizes the AWS cost optimization techniques implemented on Day 14 of the DevOps project. The goal is to minimize monthly costs while maintaining performance and reliability.

---

## 2. Optimizations Performed

### 2.1 S3 Lifecycle Rules (Frontend Bucket)
Bucket: `piyush-frontend-bucket`

**Actions:**
- Added Lifecycle rule:
  - Transition to STANDARD_IA after 30 days  
  - Transition to GLACIER after 365 days  
  - Abort incomplete multipart uploads after 7 days  

**Benefit:**
- Reduces costs for older build files stored in S3.
- Keeps bucket clean and cheap to maintain long-term.

---

### 2.2 RDS MySQL Instance Right-Sizing
Instance: `cloudapp-db`  
Old size: *unknown*  
Current size: **db.t4g.micro**

**Benefits:**
- Greatly reduced compute cost.
- Suitable for small-scale projects and development environments.

---

### 2.3 EC2 Instance Right-Sizing
Instances:
- `piyushinstance` → **t3.micro**
- `devops-backend` → **t3.micro**

**Benefits:**
- Low-cost burstable performance.
- Perfect for backend development and testing.

---

### 2.4 IAM & Security Optimization
- Implemented least-privilege IAM policy for GitHub Actions.
- Removed unused access keys and rotated secrets.
- Reduced blast radius and maintained cost-efficient security.

---

## 3. Estimated Monthly Cost (AWS)
| Service | Expected Cost After Optimization |
|--------|----------------------------------|
| EC2 (t3.micro x2) | ~$9.60/month |
| RDS (t4g.micro) | ~$15–18/month |
| S3 Storage | Depends on usage, low due to lifecycle rules |
| CloudFront | ~$1–3/month depending on traffic |
| IAM | Free |
| Total Estimate | **~$25–35 per month** |

---

## 4. Future Cost Optimization Ideas
- Move logs to S3 and enable log lifecycle expiration.
- Enable RDS storage autoscaling if database grows.
- Use spot instances for non-critical compute.
- Use AWS Cost Explorer Alerts for billing caps.

---

## 5. Conclusion
The infrastructure has been optimized for minimal cost while maintaining full functionality. These changes bring the stack closer to real-world DevOps standards and ensure predictable monthly billing.

