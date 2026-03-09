# 🛡️ IT Support Enterprise Lab Portfolio

**Administrator:** John Belita

**Location:** Calgary, AB | **Email:** johnalbertbelita@gmail.com



---



## 🚀 Project Overview

Welcome to my technical portfolio. This repository serves as documented proof of my hands-on proficiency in enterprise IT support, bridging the gap between my formal Cybersecurity and Networking education and real-world Service Desk operations. 



To demonstrate my readiness for IT Support roles, I engineered a comprehensive **Enterprise Home Lab**. This simulated hybrid environment allowed me to execute the daily responsibilities of a Service Desk Analyst, from resolving end-user incidents to managing identity lifecycles, enforcing endpoint security, automating OS deployments, and managing hybrid cloud identities within Microsoft 365 and Exchange Online.



### 🛠️ Tech Stack & Tools Used

* **Infrastructure:** Windows Server 2022, Windows 11 Pro, Windows 10 Enterprise, Oracle VirtualBox

* **Identity & Cloud:** Active Directory (AD DS), Microsoft 365, Microsoft Entra ID (Azure AD), Exchange Online

* **Network Services:** DHCP, DNS, Windows Deployment Services (WDS), PXE Boot, TFTP

* **ITSM & Ticketing:** Jira Service Management

* **Endpoint Management:** Action1 RMM

* **Security:** Group Policy (GPO), NTFS/RBAC, Principle of Least Privilege



### 🎯 Core Competencies Demonstrated

* **Exchange Online Administration:** Provisioning Shared Mailboxes, managing proxy addresses (aliases) via AD Attribute Editor, and executing Message Traces to troubleshoot mail flow.

* **Hybrid Cloud Identity:** Bridging on-premise Active Directory with Microsoft 365 and syncing password hashes via Microsoft Entra Connect.

* **Identity & Access Management (IAM):** Administering Active Directory user lifecycles, configuring account restrictions, and enforcing security policies.

* **Automated OS Deployment:** Architecting PXE boot environments to deploy Windows operating systems over the network to bare-metal clients.

* **IT Service Management (ITSM):** Managing the full ticket lifecycle, practicing First Call Resolution (FCR) methodologies, and enforcing SLAs.

* **Remote Fleet Management:** Deploying third-party software, monitoring endpoint health, and managing patch compliance.

* **Security & Compliance:** Architecting secure file shares, applying the Principle of Least Privilege, and enforcing Role-Based Access Control.



---



## 🏗️ Section 0: Infrastructure Implementation

*Building the foundational server environment and promoting the Domain Controller.*



### 0.1 Virtual Machine Configuration

> *Provisioned a Windows Server 2022 VM with optimized resource allocation (2 vCPU, 8GB RAM) and installed Guest Additions for improved host-to-guest integration.*



![VM Resource Config](screenshots/vm-config-resources.png)

![Guest Additions](screenshots/vm-guest-additions.png)



### 0.2 Network Configuration & Shared Storage

> *Configured a static IP (10.0.0.10) for the server and established a secure Shared Folder path to simulate a mapped network drive for file transfer.*



![Static IP Setup](screenshots/server-static-ip.png)

![Shared Folder](screenshots/vm-shared-folder.png)



### 0.3 Domain Controller Promotion

> *Promoted the server to a Domain Controller (YYC-DC-01) by installing AD DS roles and creating a new forest root domain (belita.com).*



![Server Rename](screenshots/server-rename.png)

![AD DS Promotion](screenshots/server-promotion-ad.png)



### 0.4 Verification

> *Verified successful deployment of Active Directory Users and Computers (ADUC).*



![AD Verification](screenshots/ad-deployment-verified.png)



---



## 💻 Section 1: Client Workstation Deployment

*Configuring and joining a Windows 11 endpoint to the corporate domain.*



### 1.1 OS Installation & Selection

> *Selected Windows 11 Pro to ensure domain-joining capabilities, as Windows 11 Home does not support Active Directory integration.*



![Win 11 Pro Install](screenshots/client-win11-install.png)



### 1.2 DNS Configuration

> *Configured the Windows 11 Client DNS settings to point directly to the Domain Controller (10.0.0.10), ensuring successful name resolution for the belita.com domain.*



![Client DNS](screenshots/client-dns-config.png)



### 1.3 Domain Join

> *Successfully joined the Windows 11 client to the 'belita.com' Active Directory domain using administrative credentials.*



![Domain Join](screenshots/client-domain-join.png)



---



## 📂 Section 2: Identity & Access Management (Active Directory)

*Demonstrating core competency in user lifecycle management, security groups, and organizational structure.*



### 2.1 Organizational Unit (OU) Design

> *Designed a hierarchical OU structure to separate 'Admin' accounts from 'Standard Users' and 'Service Accounts,' ensuring granular policy application.*



![Active Directory OU Structure](screenshots/ad-ou-structure.png)



### 2.2 Advanced User Provisioning

> *Provisioned new user accounts (e.g., Neil Nepu) with standard naming conventions and configured strict Logon Hours/Account Expiry to enhance security.*



![New User Neil](screenshots/ad-user-neil.png)

![Account Restrictions](screenshots/ad-account-expiry.png)



### 2.3 End-to-End Verification

> *Verified end-to-end connectivity by logging into the client workstation using the provisioned Active Directory user account.*



![Client Login Success](screenshots/client-login-success.png)



---



## 🗄️ Section 3: File Server & Storage Management

*Implementing Role-Based Access Control (RBAC) and secure file sharing.*



### 3.1 File Share Hierarchy

> *Designed a structured file share hierarchy (HR, IT, Data) to segregate sensitive departmental data from public common areas.*



![File Share Hierarchy](screenshots/fs-share-hierarchy.png)



### 3.2 NTFS Permissions & RBAC

> *Configured strict NTFS permissions using Security Groups (e.g., 'IT_Access') rather than individual users, ensuring scalable access management.*



![NTFS Permissions](screenshots/fs-ntfs-permissions.png)

![RBAC Groups](screenshots/fs-rbac-groups.png)



### 3.3 Permission Validation

> *Validated permission inheritance by confirming 'Access Denied' restrictions when unauthorized users attempted to access restricted folders.*



![Access Denied](screenshots/fs-access-denied.png)



---



## ⚙️ Section 4: Group Policy & Security Hardening

*Showcasing the ability to automate configuration and enforce security protocols.*



### 4.1 Password & Lockout Policies

> *Enforced a strict Password Policy (12-char min, 90-day rotation) and Account Lockout Policy (3 attempts) to mitigate brute-force attacks.*



![Password Policy](screenshots/gpo-password-policy.png)

![Lockout Policy](screenshots/gpo-lockout-policy.png)



### 4.2 Security Validation (Simulated Attack)

> *Simulated a brute-force attempt and verified that the account was successfully locked out, preventing unauthorized access. Also verified Logon Hour restrictions.*



![Account Locked Message](screenshots/client-locked-out-msg.png)

![Logon Denied Message](screenshots/client-logon-denied-msg.png)



---



## ☁️ Section 5: Cloud RMM & Patch Management (Action1)

*Demonstrating modern, cloud-based fleet management and vulnerability remediation.*



### 5.1 Hybrid Integration (Active Directory Connector)

> *Configured the Action1 AD Connector to automatically discover and sync on-premise assets with the cloud platform, ensuring real-time fleet visibility.*



![AD Connector Config](screenshots/action1-ad-connector-config.png)

![Agent Install CLI](screenshots/action1-agent-install-cli.png)



### 5.2 Vulnerability Management & Patching

> *Performed automated vulnerability assessments to identify critical CVEs and executed patch remediation workflows to secure the environment.*



![CVE List](screenshots/action1-cve-list.png)

![Patch Remediation](screenshots/action1-patch-remediation.png)

![Compliance Report](screenshots/action1-compliance-report.png)



### 5.3 Automated Software Deployment

> *Leveraged the Action1 App Store to deploy certified third-party applications (7-Zip) to client endpoints without manual intervention.*



![Deploy 7-Zip Task](screenshots/action1-deploy-7zip-task.png)

![Client 7-Zip Installed](screenshots/client-7zip-installed.png)



---



## 📡 Section 6: Remote Administration

*Utilizing built-in Windows tools for remote troubleshooting and management.*



### 6.1 Administrative Shares (C$)

> *Utilized administrative shares (C$) to remotely access and troubleshoot client file systems without interrupting the user's active session.*



![Admin Share C$](screenshots/admin-share-c-drive.png)



---



## 🎫 Section 7: IT Service Management (Jira Service Management)

*Proving the ability to manage the ticket lifecycle, SLAs, and user communication.*



### 7.1 Identity Synchronization

> *Synced on-premise Active Directory users to Jira Service Management, ensuring seamless authentication and customer profile management.*



![Jira Customers](screenshots/jira-customers-sync.png)



### 7.2 Ticket Triage & Queue Management

> *Managed the IT Service Desk queue, prioritizing high-impact incidents and using Internal Notes to track investigation steps.*



![Jira Queue](screenshots/jira-queue-view.png)

![Ticket Assignment](screenshots/jira-ticket-assignment.png)



### 7.3 Service Level Agreement (SLA) Engineering

> *Engineered custom SLA metrics for "Time to First Response" (15m) and "Time to Resolution" (2h). Utilized Jira Query Language (JQL) to write specific conditions (`priority in (High, Highest)`) to ensure critical incidents automatically trigger accelerated support workflows.*



![SLA Timer](screenshots/jira-ticket-sla-triage.png)



### 7.4 Service Request Fulfillment

> *Configured a self-service Customer Portal for software requests and fulfilled them using automated RMM workflows.*



![Customer Portal](screenshots/jira-portal-view.png)

![Resolved Request](screenshots/jira-ticket-request-resolved.png)



### 7.5 Incident Management (Break/Fix)

> *Simulated and resolved a high-impact (Priority: Highest) business outage where the HR department lost access to a critical file share. Documented technical root causes in Internal Notes, while providing clear, jargon-free resolution updates to the non-technical end-users.*



* **Simulated Incident:** "URGENT: HR Department cannot access the Confidential Shared Drive."

* **Root Cause:** The `HR` Security Group was inadvertently removed from the folder's Access Control List (ACL) on the file server.

* **Resolution:** Re-applied the correct Role-Based Access Control (RBAC) group to the folder, verified inheritance, and confirmed access with the end-users using non-technical customer service communication.



![Jira Incident Resolved](screenshots/jira-incident-resolved.png)

*Figure 5: Documenting root cause analysis via Internal Notes and communicating the resolution to the end-user.*



![AD Folder Fix](screenshots/ad-hr-folder-fix.png)

*Figure 6: Verifying the technical resolution by restoring the HR security group to the folder's Access Control List.*



---



## 💿 Section 8: Automated Network OS Deployment (WDS)

*Architecting a PXE Boot environment to automate bare-metal OS provisioning.*



### 8.1 WDS Server Initialization & Image Management

> *Configured the Windows Deployment Services role integrated with Active Directory. Successfully mounted the Windows 10 ISO, extracting and publishing both the `boot.wim` (Windows PE) and `install.wim` (OS payload) to the WDS console.*



![WDS Console](screenshots/wds-console-images.png)



### 8.2 Resolving UDP Port Conflicts (DHCP & WDS)

> *Resolved UDP Port 67 conflicts between co-hosted DHCP and WDS roles by configuring WDS to yield the port and appending PXE-specific DHCP options to ensure proper client network routing.*



![WDS DHCP Config](screenshots/wds-dhcp-conflict-fix.png)



### 8.3 Advanced TFTP Troubleshooting

> *Diagnosed and resolved TFTP packet fragmentation (Error Code 1460) by disabling Variable Window Extension and optimizing the Maximum Block Size to ensure reliable boot image delivery over the virtual network.*



![TFTP Block Size](screenshots/wds-tftp-block-size.png)



### 8.4 Client PXE Boot Execution

> *Provisioned a bare-metal client utilizing a UEFI motherboard and an Intel PRO/1000 network adapter. The client successfully obtained an IP via DHCP, located the WDS server, and initiated the PXE network boot sequence.*



![PXE Boot Screen](screenshots/wds-pxe-boot-screen.png)



### 8.5 Successful OS Deployment

> *The client seamlessly loaded the Windows Preinstallation Environment (WinPE) over the network, authenticated against Active Directory using Domain Admin credentials, and successfully initiated the automated Windows 10 installation.*



![Windows Setup Network](screenshots/wds-windows-setup.png)



---



## ☁️ Section 9: Hybrid Cloud Identity & Exchange Online Administration

*Simulating a modern enterprise environment by bridging on-premise Active Directory with Microsoft 365, Entra ID, and Exchange Online.*



### 9.1 Cloud Identity Synchronization (Entra Connect)

> *Configured Alternative UPN Suffixes and deployed Microsoft Entra Connect Sync. Verified the successful replication of local user identities and password hashes into the Microsoft 365 Admin Center.*



![M365 Active Users Sync](screenshots/entra-m365-active-users.png)



### 9.2 Shared Mailbox Provisioning & Delegation

> *Created an `IT Support` Shared Mailbox to simulate a zero-cost departmental email routing strategy. Granted the synced user 'Read and Manage' and 'Send As' delegation, verifying successful access via Outlook Web App (OWA).*



![Shared Mailbox Outlook](screenshots/exchange-shared-mailbox.png)



### 9.3 AD Attribute Management (Email Aliases)

> *Utilized the Active Directory Attribute Editor to provision a secondary email alias. Manually configured the `proxyAddresses` attribute with a lowercase `smtp:` prefix, then executed `Start-ADSyncSyncCycle -PolicyType Delta` via PowerShell to force an immediate replication to the cloud.*



### 9.4 Mail Flow Troubleshooting (Message Trace)

> *Simulated an external mail delivery issue. Executed a Message Trace within the Exchange Admin Center to track inbound email traffic, verifying network routing success and identifying Microsoft 365 spam filter (EOP) handling.*



![Message Trace](screenshots/exchange-message-trace.png)



---



## 📜 Education & Certifications

* **CompTIA Security+** | Certified January 2026

* **Diploma in Cybersecurity** | ABM College, Calgary, AB | Graduated May 2025

* **Network Specialist Training** | SAIT, Calgary, AB | 2019



---



## 📫 Contact

**John Belita** | Calgary, AB | johnalbertbelita@gmail.com
