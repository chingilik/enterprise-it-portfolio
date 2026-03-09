# 🛡️ IT Support Enterprise Lab Portfolio

**Administrator:** John Belita  
**Location:** Calgary, AB | **Email:** johnalbertbelita@gmail.com  
**Certifications:** CompTIA Security+ (2026)

---

## 🚀 Project Overview

Welcome to my technical portfolio. This repository documents my hands-on proficiency in enterprise IT support, bridging the gap between my **Cybersecurity and Networking** education and real-world Service Desk operations.

To demonstrate readiness for IT Support roles, I engineered a comprehensive **Enterprise Home Lab**. This hybrid environment simulates the daily responsibilities of a Service Desk Analyst: from resolving complex end-user incidents to managing identity lifecycles (IAM), enforcing endpoint security, and administering hybrid cloud identities within **Microsoft 365** and **Exchange Online**.

### 🛠️ Tech Stack & Tools
* **Infrastructure:** Windows Server 2022, Windows 11 Pro/10 Enterprise, Oracle VirtualBox
* **Identity & Cloud:** Active Directory (AD DS), Microsoft 365, Microsoft Entra ID, Exchange Online
* **Networking:** DHCP, DNS, Windows Deployment Services (WDS), PXE Boot, TFTP
* **ITSM & RMM:** Jira Service Management, Action1 RMM
* **Security:** Group Policy (GPO), NTFS/RBAC, Principle of Least Privilege (PoLP)

---

## 🏗️ Section 0: Infrastructure Implementation
*Building the foundational server environment and promoting the Domain Controller.*

### 0.1 Virtual Machine & Network Config
> Provisioned Windows Server 2022 (2 vCPU, 8GB RAM). Configured a **Static IP (10.0.0.10)** and established secure Shared Folders to simulate mapped network drives.

![VM Resource Config](screenshots/vm-config-resources.png)
![Static IP Setup](screenshots/server-static-ip.png)

### 0.2 Domain Controller Promotion (YYC-DC-01)
> Promoted the server to a Domain Controller, establishing the forest root `belita.com`. Verified via **Active Directory Users and Computers (ADUC)**.

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
> Designed a hierarchical OU structure (Admins, Users, Service Accounts). Provisioned accounts with standardized naming conventions and enforced **Account Expiry/Logon Hour** restrictions.

![Active Directory OU Structure](screenshots/ad-ou-structure.png)
![Account Restrictions](screenshots/ad-account-expiry.png)

---

## 🗄️ Section 3: File Server & RBAC
*Implementing Role-Based Access Control and secure data segregation.*

* **Security Groups:** Managed access via groups (e.g., `IT_Access`, `HR_Access`) rather than individual users to ensure scalability.
* **Validation:** Confirmed "Access Denied" triggers for unauthorized users to verify NTFS permission inheritance.

![NTFS Permissions](screenshots/fs-ntfs-permissions.png)
![Access Denied](screenshots/fs-access-denied.png)

---

## ⚙️ Section 4: Group Policy & Hardening
*Automating security protocols across the domain.*

* **Password Policy:** Enforced 12-character minimums and 90-day rotations.
* **Account Lockout:** Configured a 3-attempt threshold to mitigate brute-force risks.
* **Validation:** Verified the "Account Locked" message on the client-side after failed attempts.

![Password Policy](screenshots/gpo-password-policy.png)
![Account Locked Message](screenshots/client-locked-out-msg.png)

---

## ☁️ Section 5: Modern Fleet Management (Action1 RMM)
*Cloud-based vulnerability remediation and patch management.*

* **AD Connector:** Synced on-premise assets to the cloud for real-time visibility.
* **Patch Management:** Identified critical **CVEs** and executed automated remediation workflows.
* **Software Deployment:** Silently deployed 3rd-party apps (7-Zip) via RMM.

![CVE List](screenshots/action1-cve-list.png)
![Patch Remediation](screenshots/action1-patch-remediation.png)

---

## 🎫 Section 6: ITSM (Jira Service Management)
*Managing the ticket lifecycle and meeting Service Level Agreements (SLAs).*

### 6.1 SLA Engineering & Triage
> Engineered custom SLAs: **15m Time to First Response** and **2h Resolution**. Used **JQL** (Jira Query Language) to prioritize critical incidents.

### 6.2 Incident Management Case Study
* **Issue:** HR Department lost access to a critical shared drive.
* **Root Cause:** Security Group was accidentally stripped from the folder's ACL.
* **Resolution:** Restored RBAC permissions, verified inheritance, and documented the fix in Jira Internal Notes for knowledge base (KB) creation.

![Jira Queue](screenshots/jira-queue-view.png)
![Jira Incident Resolved](screenshots/jira-incident-resolved.png)

---

## 💿 Section 7: Automated OS Deployment (WDS)
*Architecting a PXE Boot environment for bare-metal provisioning.*

* **Image Management:** Extracted and published `boot.wim` and `install.wim` images.
* **Troubleshooting:** Resolved **UDP Port 67** conflicts with DHCP and optimized **TFTP Block Size** to fix packet fragmentation (Error 1460).
* **Execution:** Successfully deployed Windows 10 to a bare-metal client via network boot.

![TFTP Block Size](screenshots/wds-tftp-block-size.png)
![PXE Boot Screen](screenshots/wds-pxe-boot-screen.png)

---

## ☁️ Section 8: Hybrid Cloud & Exchange Online
*Bridging on-premise Active Directory with Microsoft 365.*

* **Entra Connect:** Replicated local identities and password hashes to **Microsoft Entra ID**.
* **Exchange Admin:** Provisioned Shared Mailboxes and managed **SMTP Aliases** via the AD Attribute Editor (`proxyAddresses`).
* **Message Trace:** Troubleshooted mail flow to identify EOP (Exchange Online Protection) handling of inbound external mail.

![M365 Active Users Sync](screenshots/entra-m365-active-users.png)
![Message Trace](screenshots/exchange-message-trace.png)

---

## 📜 Education & Certifications

* **CompTIA Security+** | Certified Jan 2026
* **Diploma in Cybersecurity** | ABM College, Calgary, AB | Graduated May 2025
* **Network Specialist Training** | SAIT, Calgary, AB | 2019

---

## 📫 Contact
**John Belita** | Calgary, AB | johnalbertbelita@gmail.com
