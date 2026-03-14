# Lab 1 – Terraform DevSecOps Infrastructure

## Overview

This project demonstrates Infrastructure as Code (IaC) using Terraform to deploy a secure virtual machine in Google Cloud Platform (GCP). The repository also includes a CI pipeline using GitHub Actions to validate Terraform code and perform security scanning.

The goal of this lab is to apply DevSecOps principles such as automation, security hardening, and continuous integration.

---

## Architecture

The infrastructure created by Terraform includes:

* A Google Compute Engine virtual machine
* Ubuntu 22.04 operating system
* Firewall configuration using UFW
* Fail2ban intrusion protection
* Automatic security updates
* Daily disk snapshots for backup
* CI pipeline for Terraform validation and security scanning

---

## Project Structure

```
lab1-terraform
│
├── main.tf                # Terraform infrastructure configuration
├── variables.tf           # Terraform input variables
├── outputs.tf             # Terraform output values
├── startup.sh             # VM security hardening script
├── .gitignore             # Files ignored by git
│
└── .github
    └── workflows
        └── terraform.yml  # GitHub Actions CI pipeline
```

---

## Prerequisites

To run this project locally you need:

* Terraform installed
* Git installed
* A Google Cloud Platform account
* Access to the GCP project `chas-devsecops-2026`
* Google Cloud CLI (optional but recommended)

---
## Configuration

Create a local Terraform variables file:

`terraform.tfvars`

Example configuration:

```
project_id = "chas-devsecops-2026"
region     = "europe-north1"
student_id = "willibroad"
```

⚠️ This file is ignored by git to prevent sensitive information from being committed.

---

## Deploy Infrastructure

Initialize Terraform:

```
terraform init
```

Validate configuration:

```
terraform validate
```

Preview changes:

```
terraform plan
```

Deploy infrastructure:

```
terraform apply
```

Terraform will provision the virtual machine and configure the backup policy.

---

## Accessing the VM

After deployment Terraform outputs the external IP of the instance.

Example:

```
ssh ubuntu@<vm_external_ip>
```

---

## Security Hardening

The VM startup script installs and configures:

* UFW firewall
* Fail2ban
* Unattended security upgrades

This improves the baseline security of the system.

---

## Backup Strategy

A snapshot policy is configured using Terraform:

* Daily disk snapshots
* Snapshots retained for 7 days
* Snapshots remain even if the VM is deleted

This ensures recoverability of the system.

---

## Continuous Integration (CI)

The repository uses GitHub Actions to automatically run:

1. Terraform formatting checks
2. Infrastructure security scanning using Trivy
3. Terraform validation

This helps ensure infrastructure code quality and security.

---

## Destroy Infrastructure

To avoid unnecessary cloud costs, destroy the infrastructure when finished:

```
terraform destroy
```


---

## Technologies Used

* Terraform
* Google Cloud Platform (GCP)
* GitHub
* GitHub Actions
* Trivy
* Linux (Ubuntu)

---

## Author

Student: `Willibroad Ngebi`
Course: DevSecOps 2026
Lab: Terraform Infrastructure Deployment
