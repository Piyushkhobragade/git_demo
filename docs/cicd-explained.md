==================== START ====================

CI/CD Explained

This document explains how the CI/CD pipelines work for both the frontend and backend of this project.

1. Overview

The project has two automated deployment pipelines:

Frontend CI/CD

Uploads frontend files to S3

Performs CloudFront cache invalidation

Backend CI/CD

Connects to EC2 via SSH

Pulls the latest backend code

Installs dependencies

Restarts backend service

Both pipelines run when changes are pushed to the main branch.

2. Frontend CI/CD (S3 + CloudFront)
What triggers it

Changes in the frontend/ folder.

What it does

Checks out the code

Configures AWS credentials

Syncs the frontend build to S3

Invalidates CloudFront cache

Why it works

S3 hosts the files

CloudFront distributes globally

Invalidation updates the UI instantly

3. Backend CI/CD (EC2 SSH Deploy)
What triggers it

Changes in the Backend/ folder.

What it does

SSH into EC2

Pull latest backend code

Install dependencies

Restart the backend service

Why it works

Automates backend updates

Eliminates manual SSH

Ensures consistent deployment

4. IAM + GitHub Secrets
IAM user used

github-actions-frontend

IAM permissions

Upload to S3

Create CloudFront invalidation

GitHub secrets used

AWS_ACCESS_KEY_ID

AWS_SECRET_ACCESS_KEY

SSH_PRIVATE_KEY

5. Security

Least-privilege IAM policy

EC2 SSH allowed only from GitHub CI

RDS is private (not public)

No excess permissions

6. Summary

Frontend pipeline:
GitHub Actions → S3 Upload → CloudFront Invalidation → Live UI update

Backend pipeline:
GitHub Actions → SSH to EC2 → Pull code → Restart service

This setup mirrors real-world DevOps CI/CD pipelines.

==================== END ====================
