# Create and Configure an Azure Storage Account

## Project Overview

This project demonstrates the deployment and configuration of an **Azure Storage Account** using the Azure Portal. The exercise covers core storage-account configuration areas including performance, access tier, networking, data protection, redundancy, and lifecycle management.

The project was completed as a practical Azure administration exercise and documented step-by-step with screenshots.

## Objectives

The main objectives of this project were to:

- Create a standard Azure Storage Account.
- Configure the appropriate storage access tier.
- Review and configure networking and public network access.
- Enable data-protection features such as soft delete.
- Configure and verify storage redundancy.
- Review security and networking settings.
- Configure lifecycle management for automated data-tier management.
- Document the implementation for future reference and portfolio demonstration.

## Technologies and Services

| Technology | Purpose |
|---|---|
| Microsoft Azure | Cloud platform |
| Azure Storage Account | Object/file/blob storage service |
| Azure Portal | Resource deployment and management |
| Storage lifecycle management | Automated data-tier and retention management |
| Azure networking controls | Control access to the storage account |
| Data protection | Protection against accidental deletion |

## Prerequisites

Before starting this exercise, ensure you have:

- An active Azure subscription.
- Access to the Azure Portal.
- Sufficient permissions to create and manage storage accounts.
- A basic understanding of Azure resource groups and storage services.

## Implementation Steps

### Step 1 — Create a Standard Azure Storage Account

Create a new storage account from the Azure Portal.

Key configuration areas include:

- Subscription
- Resource group
- Storage account name
- Region
- Performance
- Redundancy

The storage account name must be globally unique and comply with Azure naming requirements.

![Step 1 - Create a standard Azure Storage Account](Step%201.%20create%20a%20standard%20azure%20storage%20account.png)

---

### Step 2 — Configure the Access Tier

On the **Advanced** configuration section, select the appropriate access tier.

For this exercise, the **Hot** tier was selected. The Hot tier is designed for data that is accessed frequently.

![Step 2 - Select Hot tier](step%202.%20On%20the%20Advanced%20Tab%20select%20the%20Hot%20tier.png)

---

### Step 3 — Configure Networking

Review the **Networking** tab and configure public network access according to the security requirements of the environment.

Restricting public network access can reduce exposure of the storage account and is generally preferable where private or explicitly approved network access is required.

![Step 3 - Configure networking](Step%203.%20On%20the%20Networking%20Tab%20disable%20public%20access.png)

---

### Step 4 — Configure Data Protection

On the **Data Protection** tab, enable the appropriate soft-delete protection settings.

Soft delete helps recover data that has been accidentally deleted during the configured retention period.

![Step 4 - Configure data protection](Step%204.%20On%20the%20Data%20Protection%20Tab%20enable%20soft%20delete.png)

---

### Step 5 — Validate and Create

Review the configuration and select **Review + create**.

Azure performs validation before allowing the storage account to be deployed.

Once validation succeeds, select **Create**.

![Step 5 - Validate and create](Step%205.%20Click%20on%20create%20after%20validation%20is%20complete.png)

---

### Step 6 — Open the Storage Account Resource

After deployment completes, select **Go to resource** to open the newly created storage account.

This provides access to the account's configuration, security, networking, data-management, and monitoring options.

![Step 6 - Go to resource](Step%206.%20Go%20to%20resource%20after%20Storage%20is%20created.png)

---

### Step 7 — Verify the Created Storage Account

Verify that the storage account has been successfully created and that the selected configuration is reflected in the resource overview.

![Step 7 - Created Storage Account](Step%207.%20Created%20Storage%20Account.png)

---

### Step 8 — Review Security and Networking

Open the **Security + networking** section of the storage account.

Review the available controls for:

- Network access
- Public network access
- Firewall and virtual network rules
- Authentication and authorization
- Secure transfer
- Other security-related settings

![Step 8 - Security and networking](Step%208.%20Under%20Security%20and%20Networking%20blade.png)

---

### Step 9 — Configure Network Access

Configure public network access according to the required access model.

Where access is restricted to **selected networks**, only approved virtual networks, IP addresses, or network sources should be permitted.

This demonstrates the principle of limiting storage access to trusted network locations.

![Step 9 - Configure selected network access](Step%209.%20Enable%20Public%20access%20for%20Selected%20Networks.png)

---

### Step 10 — Verify Redundancy

Confirm the configured **data redundancy** setting.

Azure Storage redundancy determines how many copies of data are maintained and whether those copies are distributed within a single datacenter, across availability zones, or to a secondary region.

The selected redundancy option should be based on the application's availability, durability, disaster-recovery, and cost requirements.

![Step 10 - Confirm redundancy](Step%2010.%20Confirm%20your%20redundancy%20setting%20are.png)

---

### Step 11 — Configure Lifecycle Management

Open **Data management → Lifecycle management** and create a lifecycle management rule where appropriate.

Lifecycle management can automatically move blob data between access tiers or delete data when it reaches defined conditions.

A typical lifecycle strategy might include:

1. Keep frequently accessed data in the Hot tier.
2. Move less frequently accessed data to Cool or Archive when appropriate.
3. Delete data after its required retention period.

![Step 11 - Configure lifecycle management](Step%2011.%20Select%20Lifecycle%20management%20and%20add.png)

---

## Architecture / Configuration Summary

The completed exercise demonstrates the following configuration areas:

```text
Azure Subscription
       |
       +-- Resource Group
              |
              +-- Azure Storage Account
                     |
                     +-- Performance: Standard
                     +-- Access Tier: Hot
                     +-- Redundancy: Configured
                     +-- Networking: Restricted/Configured
                     +-- Data Protection: Soft Delete
                     +-- Lifecycle Management
```

## Key Azure Concepts Demonstrated

### Storage Redundancy

Redundancy protects storage data against infrastructure failures. The appropriate option should be selected based on the required availability and disaster-recovery objectives.

### Network Security

Storage accounts can be protected by restricting public network access and allowing connections only from approved sources.

### Soft Delete

Soft delete provides an additional recovery mechanism for accidentally deleted data and helps reduce the impact of operational mistakes.

### Lifecycle Management

Lifecycle policies help automate data-management decisions and can reduce storage costs by moving data to lower-cost access tiers or deleting data that is no longer required.

## Validation Checklist

After completing the configuration, verify:

- [x] Storage account successfully created.
- [x] Standard performance selected.
- [x] Hot access tier configured.
- [x] Networking settings reviewed.
- [x] Data-protection settings configured.
- [x] Storage redundancy verified.
- [x] Security and networking settings reviewed.
- [x] Lifecycle management configured.
- [x] Configuration documented with screenshots.

## Skills Demonstrated

This project demonstrates practical knowledge of:

- Azure Portal administration
- Azure Storage Account deployment
- Azure storage redundancy
- Azure networking and access controls
- Azure data protection
- Storage lifecycle management
- Cloud security fundamentals
- Azure resource configuration and validation
- Technical documentation

## Recommended Improvements

For a production implementation, additional controls could be considered depending on the workload:

- Private Endpoints
- Azure Private DNS
- Microsoft Entra ID-based authentication
- Role-Based Access Control (RBAC)
- Customer-managed keys where required
- Azure Monitor and diagnostic settings
- Storage logging and alerting
- Geo-redundant storage for disaster recovery
- Infrastructure as Code using ARM templates, Bicep, or Terraform

## Project Purpose

This repository serves as a practical demonstration of **Azure Storage administration and cloud infrastructure configuration**. It is intended for learning, technical documentation, and portfolio development.

---

**Author:** Inyambe kani Wogar  
**Platform:** Microsoft Azure  
**Project:** Create and Configure an Azure Storage Account
