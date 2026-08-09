# Create and Configure an Azure Storage Account

## Project Overview

This project demonstrates the deployment, configuration, security hardening, and data-management features of an **Azure Storage Account** using the **Azure Portal**.

The project was completed as a practical Azure administration and cloud architecture exercise. The implementation is documented step-by-step with screenshots and includes the architectural reasoning behind the major configuration decisions.

The goal is not only to demonstrate **how** to configure Azure Storage, but also **why** particular settings are appropriate from a security, availability, data-protection, and operational perspective.

---

## Objectives

The main objectives of this project were to:

- Create and configure an Azure Storage Account.
- Select an appropriate performance and access tier.
- Configure storage redundancy according to availability requirements.
- Review and configure public network access.
- Apply data-protection features such as soft delete.
- Review storage security and networking settings.
- Configure lifecycle management for automated data management.
- Understand the architectural trade-offs between availability, security, performance, and cost.
- Document the implementation for future reference and portfolio demonstration.

---

## Technologies and Services

| Technology / Service | Purpose |
|---|---|
| Microsoft Azure | Cloud platform |
| Azure Storage Account | Object, file, and blob storage |
| Azure Portal | Resource deployment and management |
| Storage lifecycle management | Automated data-tier and retention management |
| Azure networking controls | Control access to the storage account |
| Data protection | Protection against accidental deletion |
| Storage redundancy | Improved resilience and availability |

---

## Prerequisites

Before starting this exercise, ensure you have:

- An active Azure subscription.
- Access to the Azure Portal.
- Sufficient permissions to create and manage storage accounts.
- A basic understanding of Azure resource groups and storage services.

---

# Implementation

## Step 1 — Create a Standard Azure Storage Account

A storage account was created through the Azure Portal.

### Key configuration areas

- Subscription
- Resource group
- Storage account name
- Region
- Performance
- Redundancy

### Architectural consideration

The storage account configuration should be selected according to the workload rather than simply choosing the highest available option.

Performance, redundancy, availability requirements, and cost should all be considered before deployment.

**Screenshot:** `01-create-a-standard-azure-storage-account.png`

---

## Step 2 — Configure the Access Tier

The appropriate storage access tier was selected from the **Advanced** configuration area.

Storage access tiers are designed around how frequently data is accessed.

### Architectural consideration

Selecting an appropriate access tier can help control storage costs:

- **Hot** — suitable for frequently accessed data.
- **Cool** — suitable for data accessed less frequently.
- **Cold/Archive scenarios** — suitable for increasingly infrequent access, subject to the capabilities and constraints of the selected storage configuration.

The correct choice depends on the workload's access pattern rather than simply selecting the cheapest storage option.

**Screenshot:** `02-on-the-advanced-tab-select-the-hot-tier.png`

---

## Step 3 — Configure Networking and Public Network Access

The networking configuration was reviewed and public network access was restricted according to the intended security posture.

### Architectural consideration

Storage accounts can contain sensitive business data, so unrestricted public access increases the potential attack surface.

Where appropriate, access should be limited through controls such as:

- Selected virtual networks
- IP restrictions
- Private endpoints
- Identity-based access
- Appropriate firewall rules

For production workloads, **private connectivity and identity-based authorization** should generally be considered where the architecture requires stronger network isolation.

**Screenshot:** `03-on-the-networking-tab-disable-public-access.png`

---

## Step 4 — Enable Data Protection

Data-protection settings were reviewed and soft delete was enabled.

### Architectural consideration

Soft delete helps protect data from accidental deletion and provides a recovery mechanism within the configured retention period.

This supports operational resilience against:

- Accidental deletion
- Application errors
- User mistakes
- Unintended administrative actions

Data protection should complement, rather than replace, an appropriate backup and disaster-recovery strategy.

**Screenshot:** `04-on-the-data-protection-tab-enable-soft-delete.png`

---

## Step 5 — Validate and Create the Storage Account

After reviewing the configuration, the deployment was validated before creating the storage account.

### Architectural consideration

Validation before deployment helps identify configuration issues before resources are provisioned.

This is particularly important in production environments where incorrect settings can create:

- Security exposure
- Unexpected costs
- Availability limitations
- Compliance issues

**Screenshot:** `05-click-on-create-after-validation-is-complete.png`

---

## Step 6 — Verify the Deployed Resource

After deployment, the storage account was opened from the Azure Portal and the resulting configuration was reviewed.

### Verification activities

- Confirm the resource was successfully deployed.
- Review the storage account overview.
- Verify the selected configuration.
- Review security and networking settings.
- Confirm redundancy settings.

**Screenshot:** `06-go-to-resource-after-storage-is-completed.png`

---

## Step 7 — Verify the Storage Account

The deployed storage account was reviewed to confirm that the resource was available and configured as intended.

**Screenshot:** `07-created-storage-account.png`

---

## Step 8 — Review Security and Networking

The storage account's **Security + Networking** configuration was reviewed.

### Architectural consideration

Security should be treated as a core architectural requirement rather than an optional configuration.

Important considerations include:

- Restricting unnecessary public exposure.
- Using identity-based authorization where appropriate.
- Applying least-privilege access.
- Protecting data at rest and in transit.
- Monitoring access and configuration changes.

**Screenshot:** `08-under-security-and-networking-blade-select...png`

---

## Step 9 — Restrict Public Network Access

The public network access configuration was reviewed and restricted.

### Architectural rationale

Reducing unnecessary internet exposure lowers the attack surface of the storage service.

For enterprise environments, a stronger architecture may use:

**Application → Private Endpoint → Azure Storage Account**

This can keep storage traffic within private Azure networking rather than exposing the storage endpoint publicly.

**Screenshot:** `09-enable-public-access-for-selected-network...png`

---

## Step 10 — Verify Storage Redundancy

The storage account redundancy configuration was reviewed and verified.

### Architectural consideration

Storage redundancy should be selected according to the required availability and disaster-recovery objectives.

For example:

| Option | General purpose |
|---|---|
| LRS | Protection within a single Azure region |
| ZRS | Replication across availability zones in a region |
| GRS | Replication to a secondary Azure region |
| RA-GRS | GRS with read access to the secondary region |

A geo-redundant configuration can improve resilience against a regional outage, although replication to a secondary region is asynchronous.

**Screenshot:** `10-confirm-your-redundancy-settings-are-set-to-read-access...png`

---

## Step 11 — Configure Lifecycle Management

Lifecycle management was configured to support automated data-tier management.

### Architectural consideration

Lifecycle management can automatically move or delete data based on defined rules.

For example:

**Frequently accessed → Infrequently accessed → Archive → Delete**

The purpose is to reduce unnecessary storage costs while retaining data according to business and compliance requirements.

Lifecycle rules should be designed carefully because moving or deleting data can have cost and operational consequences.

**Screenshot:** `11-select-lifecycle-management-and-add-a-rule...png`

---

# Architecture Considerations

The project demonstrates several important Azure architecture principles.

### 1. Security

Storage resources should follow the principle of **least privilege** and should not be unnecessarily exposed to the public internet.

### 2. Availability

Redundancy should be selected based on the application's availability requirements and recovery objectives.

### 3. Data Protection

Features such as soft delete provide protection against accidental deletion but should not be considered a complete disaster-recovery solution.

### 4. Cost Optimization

Access tiers and lifecycle management can reduce storage costs by aligning the storage tier with actual data-access patterns.

### 5. Operational Excellence

Configuration validation, post-deployment verification, and documented procedures make cloud resources easier to operate and maintain.

---

# Security Recommendations for Production

For a production Azure environment, the following should also be evaluated:

- Use Microsoft Entra ID and Azure RBAC instead of shared keys where practical.
- Apply least-privilege permissions.
- Consider Private Endpoints for sensitive storage accounts.
- Restrict public network access where the workload permits.
- Enable appropriate logging and monitoring.
- Protect storage data against accidental deletion.
- Define backup and disaster-recovery requirements.
- Review storage account configuration regularly.
- Use infrastructure as code for repeatable deployments.

---

# Infrastructure as Code — Future Improvement

The initial implementation was completed through the Azure Portal to demonstrate the configuration process.

A future iteration of this project can deploy the same architecture using:

- Azure Resource Manager (ARM) templates
- Bicep
- Terraform
- Azure CLI / PowerShell

Using Infrastructure as Code would make the deployment:

- Repeatable
- Version controlled
- Auditable
- Easier to reproduce across environments
- Better suited to CI/CD workflows

---

# Skills Demonstrated

This project demonstrates practical experience with:

- Azure Storage Accounts
- Azure Portal
- Storage redundancy
- Storage access tiers
- Azure networking
- Public network access controls
- Data protection
- Soft delete
- Lifecycle management
- Availability and disaster-recovery considerations
- Cloud security fundamentals
- Cost optimization
- Azure architectural decision-making
- Technical documentation

---

# Project Outcome

The Azure Storage Account was successfully created and configured with appropriate storage, networking, security, redundancy, and data-management settings.

The project demonstrates an understanding of both **Azure administration** and the architectural reasoning required to design a more secure, resilient, and cost-conscious cloud storage solution.

---

## Portfolio Value

This project is intended to demonstrate practical Azure skills and the ability to document cloud infrastructure decisions.

It can serve as a foundation for more advanced Azure architecture projects involving:

- Azure Virtual Networks
- Private Endpoints
- Azure Key Vault
- Azure Backup
- Azure Site Recovery
- Azure Monitor
- Infrastructure as Code
- CI/CD deployment
- Multi-region architectures
