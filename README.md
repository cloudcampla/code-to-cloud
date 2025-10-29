# code-to-cloud


# 🚀 CI/CD 5-Minute Cloud Deploy Demo

![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/cloudcamp/code-to-cloud/main.yml?branch=main&label=CI%2FCD%20Status&style=flat-square)

A beginner-to-intermediate demonstration project showcasing a complete **Code-to-Cloud** pipeline using **GitHub Actions** and **AWS S3** Static Website Hosting.

The core goal is to prove that a single `git push` can trigger a secure, automated deployment, resulting in a live website update in minutes.

---

## 💡 Key DevOps Concepts Demonstrated

This project showcases the following high-value, marketable skills:

* **Continuous Integration (CI):** Automating dependency installation and asset compilation (`npm install`, `npm run build`).
* **Infrastructure as Code (IaC) Principles:** Deploying to the cloud via script, not manual clicks.
* **Security & Least Privilege:** Using **AWS IAM** to create credentials with only the bare minimum required access.
* **Secrets Management:** Securely storing sensitive AWS credentials using **GitHub Secrets**.
* **Deployment Strategy:** Using `aws s3 sync --delete` for clean, reliable deployments.

---

## 🛠️ Prerequisites

Before starting, you must have the following configured:

1.  **AWS Account:** A live AWS account with billing setup.
2.  **S3 Bucket:** An S3 bucket configured for **Static Website Hosting** (including a public bucket policy).
3.  **GitHub Repository:** This code cloned to a new, public GitHub repository.

---

## 🔐 Setup: Security and Credentials

To ensure a secure deployment, we use **Programmatic Access** via a dedicated IAM User:

### 1. Create AWS IAM Policy

Create a new IAM Policy in your AWS console with the following JSON. **Replace `<YOUR_BOOTCAMP_S3_BUCKET_NAME>` with your actual bucket name.**

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowS3DeploymentActions",
            "Effect": "Allow",
            "Action": [
                "s3:PutObject",
                "s3:DeleteObject",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::<YOUR_BOOTCAMP_S3_BUCKET_NAME>/*"
            ]
        }
    ]
}
