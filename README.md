# 🛡️ IT Support Enterprise Lab Portfolio

**Administrator:** John Belita  
**Location:** Calgary, AB | **Email:** johnalbertbelita@gmail.com  
**Certifications:** CompTIA Security+ (2026)

---

## 🚀 Project Overview

Welcome to my technical portfolio. This repository serves as documented proof of my hands-on proficiency in enterprise IT support, bridging the gap between my formal Cybersecurity education and real-world Service Desk operations.

To demonstrate readiness for modern Systems Administration and IT Support roles, I engineered a comprehensive **Enterprise Home Lab**. This hybrid environment simulates the daily responsibilities of a Service Desk Analyst: from resolving complex end-user incidents and managing identity lifecycles (IAM) to enforcing endpoint security and administering hybrid cloud identities across **Microsoft 365**, **Intune**, and **Google Workspace**.

### 🛠️ Tech Stack & Tools
* **Infrastructure:** Windows Server 2022, Windows 11 Pro, Oracle VirtualBox
* **Identity & Cloud:** Active Directory (AD DS), Microsoft 365, Google Workspace, Microsoft Entra ID
* **Endpoint Management:** Microsoft Intune (MDM), Action1 RMM, WDS (PXE Boot)
* **Network & Security:** DHCP, DNS, MX/SPF/DMARC, Group Policy (GPO), NTFS/RBAC
* **ITSM & Automation:** Jira Service Management, Microsoft Teams ChatOps, PowerShell

---

## 🏗️ Section 0: Infrastructure Implementation
*Architecting the foundational server environment and promoting the Domain Controller.*

### 0.1 Virtual Machine & Network Configuration
> Provisioned a Windows Server 2022 instance with optimized resource allocation. Configured a **Static IP (10.0.0.10)** to ensure reliable DNS resolution and established secure Shared Folders to simulate mapped corporate network drives.
> 
> ![Static IP Setup](screenshots/server-static-ip.png)
> *Figure 1: Assigning the static IPv4 configuration for the Domain Controller.*

### 0.2 Domain Controller Promotion (YYC-DC-01)
> Promoted the server to a Domain Controller, establishing the forest root `belita.com`. Verified successful directory deployment via **Active Directory Users and Computers (ADUC)**.
>
> ![AD Verification](screenshots/ad-deployment-verified.png)
> *Figure 2: Successful deployment of the belita.com Active Directory forest.*

---

## 💻 Section 1: Client Workstation Deployment
*Joining a Windows 11 Pro endpoint to the corporate domain network.*

### 1.1 DNS Alignment & Domain Join
> Manually configured the Client DNS to point to the local Domain Controller (10.0.0.10) to ensure proper SRV record resolution. Successfully authenticated and joined the workstation to the `belita.com` domain.
>
> ![Domain Join](screenshots/client-domain-join.png)
> *Figure 3: Windows 11 endpoint successfully joined to the local domain.*

---

## 📂 Section 2: Identity & Access Management (IAM)
*Demonstrating user lifecycle management and organizational structure.*

### 2.1 OU Design & User Provisioning
> Designed a hierarchical Organizational Unit (OU) structure to logically separate Admins, Users, and Service Accounts. Provisioned accounts utilizing standardized corporate naming conventions.
>
> ![Active Directory OU Structure](screenshots/ad-ou-structure.png)
> *Figure 4: Segmented OU architecture for granular policy application.*

### 2.2 Security Restrictions
> Enforced strict **Account Expiry** and **Logon Hour** restrictions to mitigate the risk of unauthorized access outside of authorized business hours.
>
> ![Account Restrictions](screenshots/ad-account-expiry.png)
> *Figure 5: Enforcing time-based logon restrictions on a standard user account.*

---

## ⚡ Section 3: Scripting & Automation (PowerShell)
*Optimizing the HR-to-IT onboarding pipeline to eliminate manual data entry errors.*

### 3.1 Bulk Identity Provisioning
> Engineered a **PowerShell automation script** utilizing `Import-Csv` and `New-ADUser` to ingest standardized HR spreadsheets and dynamically provision Active Directory accounts en masse.

### 3.2 Security Baseline Enforcement
> The script automatically generates `SamAccountNames` and enforces Zero Trust security baselines by setting complex temporary passwords and triggering the `-ChangePasswordAtLogon $true` parameter.
>
> ![PowerShell AD Automation](screenshots/powershell-ad-automation.png)
> *Figure 6: Executing the bulk onboarding script via PowerShell ISE.*

---

## 🗄️ Section 4: File Server & RBAC
*Implementing Role-Based Access Control and secure data segregation.*

### 4.1 Security Groups & Access Validation
> Managed file share access strictly via Security Groups (e.g., `IT_Access`, `Finance_Access`) rather than individual users to ensure scalable management. Confirmed "Access Denied" triggers for unauthorized users to verify NTFS permission inheritance.
>
> ![Access Denied](screenshots/fs-access-denied.png)
> *Figure 7: Verifying successful RBAC enforcement (Access Denied for unauthorized user).*

---

## ⚙️ Section 5: Group Policy & Hardening
*Automating security protocols across the domain utilizing GPOs.*

### 5.1 Password Policy & Account Lockout
> Deployed domain-wide Group Policy Objects (GPOs) to enforce a strict 12-character minimum password policy with 90-day rotations. Configured a 3-attempt Account Lockout threshold to mitigate brute-force attacks.
>
> ![Password Policy](screenshots/gpo-password-policy.png)
> *Figure 8: Domain-wide password complexity and history requirements.*

---

## ☁️ Section 6: Modern Fleet Management (Action1 RMM)
*Executing cloud-based vulnerability remediation and patch management.*

### 6.1 Hybrid Integration & Vulnerability Management
> Synced on-premise assets to the cloud via the Action1 AD Connector. Identified critical **CVEs** through automated vulnerability scans and executed patch remediation workflows to secure outdated endpoints.
>
> ![Patch Remediation](screenshots/action1-patch-remediation.png)
> *Figure 9: Cloud-based dashboard showing successful patch deployment.*

---

## 🎫 Section 7: ITSM & ChatOps (Jira + Teams)
*Managing the incident lifecycle and reducing MTTA (Mean Time To Acknowledge).*

### 7.1 SLA Engineering & Teams Integration
> Engineered custom Jira SLAs (15m Response / 2h Resolution). Integrated **Jira with Microsoft Teams** via Webhooks, enabling end-users to generate IT tickets directly from chat messages, significantly streamlining the intake process.
>
> ![Teams Ticket Creation](screenshots/teams-ticket-creation.png)
> *Figure 10: Seamless creation of a trackable Jira incident directly from MS Teams.*

---

## 💿 Section 8: Automated OS Deployment (WDS)
*Architecting a PXE Boot environment for bare-metal OS provisioning.*

### 8.1 Image Management & Network Boot
> Extracted and published `boot.wim` and `install.wim` images to the WDS Server. Resolved **UDP Port 67** conflicts with the co-hosted DHCP server and successfully deployed Windows 10 to a bare-metal client via network boot.
>
> ![PXE Boot Screen](screenshots/wds-pxe-boot-screen.png)
> *Figure 11: Bare-metal client successfully fetching the boot image over the network.*

---

## ☁️ Section 9: Hybrid Cloud Identity (Entra ID)
*Bridging on-premise Active Directory with the Microsoft 365 Cloud.*

### 9.1 Entra Connect Synchronization
> Deployed **Microsoft Entra Connect Sync**. Verified the successful replication of local AD user identities and password hashes into the Microsoft 365 Admin Center, establishing a true hybrid environment.
>
> ![M365 Active Users Sync](screenshots/entra-m365-active-users.png)
> *Figure 12: On-premise Active Directory accounts successfully synced to Microsoft 365.*

---

## 🛠️ Section 10: Service Desk Troubleshooting (Break/Fix)
*Simulated resolution of common Tier 1/Tier 2 support requests typical of an MSP environment.*

### 10.1 Ticket: MFA Reset (Entra ID)
> **Scenario:** User lost access to their Authenticator app after replacing their mobile device. 
> **Resolution:** Navigated to Entra ID Authentication Methods, executed **Require re-register MFA**, and revoked active sessions to secure the account during the device transition.

### 10.2 Ticket: Secure Offboarding (Mailbox Conversion)
> **Scenario:** Immediate termination of an employee requiring access revocation and data retention.
> **Resolution:** Disabled the AD account, forced a Delta Sync, and converted the
