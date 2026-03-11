# 🛡️ IT Support Enterprise Lab Portfolio

**Administrator:** John Belita  
**Location:** Calgary, AB | **Email:** johnalbertbelita@gmail.com  
**Certifications:** CompTIA Security+ (2026)

---

## 🚀 Project Overview

Welcome to my technical portfolio. This repository serves as documented proof of my hands-on proficiency in enterprise IT support, bridging the gap between my formal Cybersecurity education and real-world Service Desk operations.

To demonstrate readiness for modern IT roles, I engineered a comprehensive **Enterprise Home Lab**. This hybrid environment simulates the daily responsibilities of a Service Desk Analyst: from resolving complex end-user incidents and managing identity lifecycles (IAM) to enforcing endpoint security and administering hybrid cloud identities across **Microsoft 365**, **Intune**, and **Google Workspace**.

### 🛠️ Tech Stack & Tools
* **Infrastructure:** Windows Server 2022, Windows 11 Pro, Oracle VirtualBox
* **Identity & Cloud:** Active Directory (AD DS), Microsoft 365, Google Workspace, Microsoft Entra ID
* **Endpoint Management:** Microsoft Intune (MDM), Action1 RMM, WDS (PXE Boot)
* **Network & Security:** DHCP, DNS, MX/SPF/DMARC, Group Policy (GPO), NTFS/RBAC
* **ITSM & Automation:** Jira Service Management, Microsoft Teams ChatOps, PowerShell

---

## 🏗️ Section 0: Infrastructure Implementation
*Building the foundational server environment and promoting the Domain Controller.*

### 0.1 Virtual Machine & Network Config
> Provisioned Windows Server 2022 (2 vCPU, 8GB RAM). Configured a **Static IP (10.0.0.10)** and established secure Shared Folders to simulate mapped network drives.

![VM Resource Config](screenshots/vm-config-resources.png)
![Static IP Setup](screenshots/server-static-ip.png)

### 0.2 Domain Controller Promotion (YYC-DC-01)
> Promoted the server to a Domain Controller, establishing the forest root `belita.com`. Verified successful deployment via **Active Directory Users and Computers (ADUC)**.

![AD DS Promotion](screenshots/server-promotion-ad.png)
![AD Verification](screenshots/ad-deployment-verified.png)

---

## 💻 Section 1: Client Workstation Deployment
*Joining a Windows 11 Pro endpoint to the corporate domain.*

* **DNS Alignment:** Manually pointed Client DNS to the Domain Controller (10.0.0.10) to ensure proper SRV record resolution.
* **Domain Join:** Successfully authenticated and joined the `belita.com` domain.

![Client DNS](screenshots/client-dns-config.png)
![Domain Join](screenshots/client-domain-join.png)

---

## 📂 Section 2: Identity & Access Management (IAM)
*Demonstrating user lifecycle management and organizational structure.*

### 2.1 OU Design & User Provisioning
> Designed a hierarchical OU structure (Admins, Users, Service Accounts). Provisioned accounts manually with standardized naming conventions and enforced **Account Expiry/Logon Hour** restrictions.

![Active Directory OU Structure](screenshots/ad-ou-structure.png)
![Account Restrictions](screenshots/ad-account-expiry.png)

---

## ⚡ Section 3: Scripting & Automation (PowerShell)
*Eliminating manual data entry and optimizing the HR-to-IT onboarding pipeline.*

### 3.1 Bulk Identity Provisioning
> Engineered a **PowerShell automation script** (`Import-Csv`, `New-ADUser`) to ingest standardized HR onboarding spreadsheets and automatically provision Active Directory accounts en masse.

### 3.2 Standardization & Security Enforcement
> The script dynamically generates standardized `SamAccountNames` (FirstInitial + LastName) and enforces security baselines by setting complex temporary passwords and triggering the `-ChangePasswordAtLogon $true` flag for Zero Trust compliance.

### 3.3 Business Impact
> **Process Improvement:** Reduced standard new-hire provisioning time from ~5 minutes per user manually to under 2 seconds for a bulk batch, completely eliminating Helpdesk typos and localized human error.

![PowerShell AD Automation](screenshots/powershell-ad-automation.png)

---

## 🗄️ Section 4: File Server & RBAC
*Implementing Role-Based Access Control and secure data segregation.*

* **Security Groups:** Managed access via groups (e.g., `IT_Access`, `HR_Access`) rather than individual users to ensure scalability.
* **Validation:** Confirmed "Access Denied" triggers for unauthorized users to verify NTFS permission inheritance.

![NTFS Permissions](screenshots/fs-ntfs-permissions.png)
![Access Denied](screenshots/fs-access-denied.png)

---

## ⚙️ Section 5: Group Policy & Hardening
*Automating security protocols across the domain.*

* **Password Policy:** Enforced 12-character minimums and 90-day rotations.
* **Account Lockout:** Configured a 3-attempt threshold to mitigate brute-force risks.
* **Validation:** Verified the "Account Locked" message on the client-side after failed attempts.

![Password Policy](screenshots/gpo-password-policy.png)
![Account Locked Message](screenshots/client-locked-out-msg.png)

---

## ☁️ Section 6: Modern Fleet Management (Action1 RMM)
*Cloud-based vulnerability remediation and patch management.*

* **AD Connector:** Synced on-premise assets to the cloud for real-time visibility.
* **Patch Management:** Identified critical **CVEs** and executed automated remediation workflows.
* **Software Deployment:** Silently deployed 3rd-party apps (7-Zip) via RMM.

![CVE List](screenshots/action1-cve-list.png)
![Patch Remediation](screenshots/action1-patch-remediation.png)

---

## 🎫 Section 7: ITSM & ChatOps (Jira + Teams)
*Managing the ticket lifecycle and reducing MTTA via chat integration.*

### 7.1 SLA Engineering & Triage
> Engineered custom SLAs (15m Response / 2h Resolution). Used **JQL** (Jira Query Language) to prioritize critical incidents.

![Jira Queue](screenshots/jira-queue-view.png)
![Jira Incident Resolved](screenshots/jira-incident-resolved.png)

### 7.2 Microsoft Teams Integration (Process Improvement)
> Integrated **Jira with Microsoft Teams** to allow end-users to convert chat messages directly into tickets. IT Agents receive automated webhook notifications for High Priority issues in a dedicated Teams channel.

![Jira Teams Integration](screenshots/jira-teams-integration.png)
![Teams Ticket Creation](screenshots/teams-ticket-creation.png)

---

## 💿 Section 8: Automated OS Deployment (WDS)
*Architecting a PXE Boot environment for bare-metal provisioning.*

* **Image Management:** Extracted and published `boot.wim` and `install.wim` images.
* **Troubleshooting:** Resolved **UDP Port 67** conflicts with DHCP and optimized **TFTP Block Size** to fix packet fragmentation (Error 1460).
* **Execution:** Successfully deployed Windows 10 to a bare-metal client via network boot.

![TFTP Block Size](screenshots/wds-tftp-block-size.png)
![PXE Boot Screen](screenshots/wds-pxe-boot-screen.png)

---

## ☁️ Section 9: Hybrid Cloud Identity (Entra ID)
*Bridging on-premise Active Directory with Microsoft 365.*

### 9.1 Cloud Identity Synchronization (Entra Connect)
> Deployed **Microsoft Entra Connect Sync**. Verified successful replication of local user identities and password hashes into the Microsoft 365 Admin Center.

![M365 Active Users Sync](screenshots/entra-m365-active-users.png)

---

## 🛠️ Section 10: Common Service Desk Requests (Troubleshooting)
*Execution of frequent Tier 1 and Tier 2 tickets encountered in MSP environments.*

### 10.1 Ticket: MFA Reset (Entra ID)
> Resolved a user lockout by navigating to Entra ID Authentication Methods, executing **Require re-register MFA**, and revoking active sessions to secure the account during device transition.

### 10.2 Ticket: Secure Offboarding (Mailbox Conversion)
> Disabled account in AD and forced a Delta Sync. Converted the user inbox to a **Shared Mailbox** to retain business data while reclaiming the paid license.

### 10.3 Ticket: Data Recovery (OneDrive)
> Recovered permanently deleted files by accessing the hidden **Second-Stage Recycle Bin** in the SharePoint site collection.

---

## ☁️ Section 11: Cloud SaaS Administration (Google Workspace)
*Demonstrating platform-agnostic identity management and enforcing strict email security protocols.*

### 11.1 Tenant Provisioning & Email Security (SPF/DMARC)
> Provisioned a **Google Workspace Business Standard** tenant via custom DNS routing (`belita.online`). Hardened mail flow by configuring strict **MX, SPF, and DMARC** records in Namecheap to prevent domain spoofing, aligning cloud infrastructure with CompTIA Security+ standards.

### 11.2 User Lifecycle & Alias Management
> Executed standardized user provisioning workflows for Neil Nepu. Managed organizational email routing by configuring secondary **Email Aliases** (`itdirector@belita.online`), providing flexible mail delivery without supplementary licensing costs.

![GWS Email Alias Configuration](screenshots/gws-admin-console.png)

### 11.3 RBAC & Access Control
> Engineered **Google Groups** (`execs@...`) to act as centralized security boundaries for Role-Based Access Control (RBAC). Administered organizational access policies and enforced restricted sharing permissions on sensitive data.

![GWS Group Membership](screenshots/gws-admin-console-groups.png)

---

## 📱 Section 12: Modern Endpoint Management (Microsoft Intune / MDM)
*Implementing Zero-Touch deployment and remote policy enforcement for a distributed workforce.*

### 12.1 MDM Enrollment & Entra ID Join
> Orchestrated the transition from legacy Domain Join to **Microsoft Entra ID Join**. Successfully enrolled Windows 11 endpoints into **Microsoft Intune**, enabling over-the-air (OTA) management without requiring a VPN or local Domain Controller line-of-sight.

### 12.2 Configuration Profiles & Compliance
> Engineered and deployed **Configuration Profiles** to enforce enterprise security baselines, including automated screen-lock timers and alphanumeric password complexity, mapped directly to Zero Trust architecture principles.

### 12.3 Remote Software Asset Management
> Utilized Intune to architect a standardized software suite deployment (Microsoft 365 Apps), ensuring all remote assets remain compliant and equipped with necessary productivity tools automatically upon user sign-in.

![Intune Device Management](screenshots/intune-enrolled-devices.png)
![Intune Policy Enforcement](screenshots/intune-policy-applied.png)

---

## 📜 Education & Certifications

* **CompTIA Security+** | Certified Jan 2026
* **Diploma in Cybersecurity** | ABM College, Calgary, AB | Graduated May 2025
* **Network Specialist Training** | SAIT, Calgary, AB | 2019

---

## 📫 Contact
**John Belita** | Calgary, AB | johnalbertbelita@gmail.com
