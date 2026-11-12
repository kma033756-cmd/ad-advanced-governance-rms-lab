# Advanced Active Directory Governance, Storage Management, & AD RMS Lab (`ETHA.com`)

## 📌 Project Overview
This repository documents advanced Windows Server directory services governance and data security enforcement. It covers Fine-Grained Password Policies (FGPP), granular NTFS/Share security permissions, Encrypted File System (EFS), File Server Resource Manager (FSRM) quotas and active file screening, and Active Directory Rights Management Services (AD RMS) deployment.

## 🏗️ Environment Architecture
* **Domain Controller:** `STO-DC1` (`ETHA.com`)
* **Member Server / File Server:** `STO-SVR1`
* **Client Workstation:** `STO-CL1` (`172.16.0.11`)
* **Core Tools:** Active Directory Administrative Center (ADAC), File Server Resource Manager (FSRM), AD RMS Console, PowerShell ISE (`New-SmbShare`, `fsutil`)
* **Domain Functional Level:** Windows Server 2025

---

## ⚙️ Key Tasks & Technical Implementation

### 1. Fine-Grained Password Policies (FGPP)
* Created shadow security groups and configured targeted Password Settings Objects (PSOs) for specific organizational units (e.g., Research and Sales groups).
* Verified password complexity, history, and length enforcement rules by testing user credential modifications.

### 2. Advanced NTFS & Shared Folder Permissions
* Configured hierarchical folder structures (`C:\Research\Classified\Projects`) with explicit NTFS inheritance blocking.
* Established customized share permissions and evaluated effective access control lists (ACLs) for different security principals (e.g., Aziz Hassouneh vs. Allie Bellew).

### 3. Encrypted File System (EFS)
* Secured sensitive files and directories (`C:\Research\Classified\Personal.txt`) using the Windows Encrypted File System (EFS).
* Verified that unauthorized users attempting to traverse or read encrypted items received explicit access denial errors.

### 4. File Server Resource Manager (FSRM) Quotas & File Screening
* Installed FSRM and configured custom **Quota Templates** with automated Event Viewer warning notifications (Event ID 12325 at 80/85% capacity thresholds).
* Implemented active **File Screens** and custom file groups (`ETHA MPX Media Files`) to block unauthorized file types (e.g., audio/video extensions) and generated on-demand storage audit reports.

### 5. File Classification & Active Directory Rights Management Services (AD RMS)
* Configured local classification properties and automated content classifiers for data confidentiality levels (`High`, `Medium`, `Low`).
* Deployed **Active Directory Rights Management Services (AD RMS)** on `STO-SVR1` utilizing a dedicated service account (`ETHA\ADRMSSVC`) and database cluster configurations.
* Created distributed rights policy templates (`ETHA_ReadOnly`) and configured application exclusion rules for unauthorized client utilities.
