# AWS-Cloud-Infrastructure-Lab
Designed, secured, and deployed a production-ready static portfolio website on AWS using Amazon S3, CloudFront, Route 53, AWS Certificate Manager, IAM, CloudWatch, AWS Budgets, and GitHub Actions while implementing AWS Well-Architected Framework best practices.
# AWS Cloud Infrastructure Lab

## Overview

This project demonstrates the design, deployment, and administration of a secure cloud-hosted infrastructure using core Amazon Web Services (AWS). The environment was built to simulate a production-ready static web hosting solution while implementing security, networking, monitoring, and cost management best practices.

The lab was designed around AWS Cloud Practitioner (CLF-C02) concepts and provides hands-on experience with cloud infrastructure deployment, identity and access management, content delivery, monitoring, and cloud cost optimization.

The project includes:

* Amazon S3 Static Website Hosting
* AWS Identity and Access Management (IAM)
* AWS Certificate Manager (ACM)
* Amazon CloudFront
* Amazon Route 53
* Amazon CloudWatch
* AWS Budgets
* AWS Cost Explorer
* IAM Security Best Practices
* GitHub Version Control
* GitHub Actions (CI/CD)
* AWS Well-Architected Framework Review

The objective of this project was to gain practical experience deploying cloud infrastructure while implementing AWS security, reliability, operational excellence, performance efficiency, and cost optimization best practices.

---

## Environment

| Component               | Purpose                               |
| ----------------------- | ------------------------------------- |
| AWS Management Console  | Cloud administration                  |
| Amazon S3               | Static website hosting                |
| Amazon CloudFront       | Global content delivery network (CDN) |
| Amazon Route 53         | DNS management                        |
| AWS Certificate Manager | SSL/TLS certificate management        |
| AWS IAM                 | Identity and access management        |
| Amazon CloudWatch       | Monitoring and metrics                |
| AWS Budgets             | Cost monitoring                       |
| AWS Cost Explorer       | Billing analysis                      |
| GitHub                  | Source code management                |
| GitHub Actions          | Continuous deployment                 |

---

## Cloud Architecture

### User Request Flow

```text
Internet User
      │
      ▼
Amazon Route 53
      │
      ▼
Amazon CloudFront
      │
      ▼
AWS Certificate Manager (HTTPS)
      │
      ▼
Amazon S3 Static Website
      │
      ▼
HTML • CSS • JavaScript
```

### Management Services

The environment utilizes several AWS services to provide security, monitoring, and operational visibility.

* IAM manages authentication and authorization.
* CloudWatch collects metrics and operational data.
* AWS Budgets monitors monthly spending.
* Cost Explorer provides cost analysis and forecasting.
* GitHub Actions automates website deployments.

---

## Project Objectives

* Deploy a production-ready static website using Amazon S3.
* Secure cloud resources using IAM least privilege principles.
* Configure HTTPS using AWS Certificate Manager.
* Deliver content globally using Amazon CloudFront.
* Configure DNS with Amazon Route 53.
* Monitor infrastructure using Amazon CloudWatch.
* Implement AWS Budgets for cost monitoring.
* Analyze cloud spending using AWS Cost Explorer.
* Automate deployments using GitHub Actions.
* Apply AWS Well-Architected Framework principles.

---

# Phase 1: AWS Account Security

## Configure AWS Account

The AWS account was secured by implementing security best practices before deploying any infrastructure.

### Security Tasks

* Enabled Multi-Factor Authentication (MFA)
* Created administrative IAM user
* Restricted use of the root account
* Configured account password policy
* Verified account contact information

### IAM Administrator Account

| Setting     | Value               |
| ----------- | ------------------- |
| Username    | cloudadmin          |
| Access Type | Console Access      |
| MFA         | Enabled             |
| Permissions | AdministratorAccess |

### Outcome

Administrative activities are performed using an IAM user instead of the root account, reducing risk and following AWS security best practices.

**Screenshot**

```
screenshots/01-aws-console.png
```

---

# Phase 2: Identity and Access Management

## Configure IAM

AWS Identity and Access Management (IAM) was used to create secure identities and control access to AWS resources.

### Tasks Completed

* Created IAM users
* Configured IAM groups
* Assigned permissions
* Enabled MFA
* Reviewed IAM policies
* Applied least privilege principles

### IAM Groups

| Group          | Permissions         |
| -------------- | ------------------- |
| Administrators | AdministratorAccess |
| Developers     | PowerUserAccess     |
| ReadOnly       | ReadOnlyAccess      |

### Security Features

* Multi-Factor Authentication
* Password Policy
* Least Privilege
* Role-Based Access Control (RBAC)

### Outcome

Access to AWS resources is controlled through IAM users and groups rather than using the root account.

**Screenshot**

```
screenshots/02-iam-users.png
```

---

# Phase 3: Amazon S3 Static Website Hosting

## Create Amazon S3 Bucket

An Amazon S3 bucket was created to host a static portfolio website.

### Bucket Configuration

| Setting             | Value                           |
| ------------------- | ------------------------------- |
| Bucket Name         | aws-cloud-portfolio-platform    |
| Region              | us-east-1                       |
| Versioning          | Enabled                         |
| Encryption          | AES-256                         |
| Block Public Access | Disabled (Website Hosting Only) |

### Website Files

The following files were uploaded:

* index.html
* style.css
* script.js
* assets/
* images/

### Static Website Hosting

Static website hosting was enabled through the bucket properties.

### Bucket Policy

A bucket policy was configured to allow public read access for website content while limiting administrative access through IAM.

### Outcome

The website became publicly accessible through the Amazon S3 website endpoint.

**Screenshot**

```
screenshots/03-s3-bucket.png
```

---

# Phase 4: Amazon CloudFront

## Configure Content Delivery Network

Amazon CloudFront was deployed in front of the S3 bucket to improve website performance, reduce latency, and provide HTTPS support.

### Distribution Configuration

| Setting     | Value                  |
| ----------- | ---------------------- |
| Origin      | Amazon S3              |
| Protocol    | HTTPS                  |
| Compression | Enabled                |
| Caching     | Enabled                |
| Price Class | Use All Edge Locations |

### Benefits

* Global content delivery
* Lower latency
* HTTPS encryption
* Edge caching
* Improved availability
* DDoS resilience

### Outcome

Website traffic is delivered through AWS edge locations, improving performance for users worldwide.

**Screenshot**

```
screenshots/04-cloudfront.png
```

---

# Phase 5: AWS Certificate Manager

## Configure HTTPS

An SSL/TLS certificate was requested through AWS Certificate Manager and attached to the CloudFront distribution.

### Certificate Details

| Setting    | Value                   |
| ---------- | ----------------------- |
| Service    | AWS Certificate Manager |
| Validation | DNS                     |
| Status     | Issued                  |
| Protocol   | HTTPS                   |

### Tasks Completed

* Requested SSL certificate
* Verified domain ownership
* Validated DNS records
* Attached certificate to CloudFront

### Outcome

The website now uses encrypted HTTPS connections, improving security and user trust.

**Screenshot**

```
screenshots/05-acm-certificate.png
```

---

# Phase 6: Amazon Route 53

## Configure DNS

Amazon Route 53 was configured to manage DNS records and route traffic to the CloudFront distribution.

### Hosted Zone

| Record Type | Target                  |
| ----------- | ----------------------- |
| A (Alias)   | CloudFront Distribution |
| AAAA        | CloudFront Distribution |

### Tasks Completed

* Created Hosted Zone
* Configured Alias records
* Linked custom domain
* Verified DNS propagation

### Outcome

Users can access the website using a custom domain name secured with HTTPS.

**Screenshot**

```
screenshots/06-route53.png
```
