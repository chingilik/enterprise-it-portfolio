# **🛡️ IT Support Enterprise Lab Portfolio**

**Administrator:** John Belita

**Location:** Calgary, AB | **Email:** johnalbertbelita@gmail.com

## **🚀 Project Overview**

Welcome to my technical portfolio. This repository serves as documented proof of my hands-on proficiency in enterprise IT support, bridging the gap between my formal Cybersecurity and Networking education and real-world Service Desk operations.

To demonstrate my readiness for IT Support roles, I engineered a comprehensive **Enterprise Home Lab**. This simulated hybrid environment allowed me to execute the daily responsibilities of a Service Desk Analyst, from resolving end-user incidents to managing identity lifecycles, enforcing endpoint security, automating OS deployments, and managing hybrid cloud identities within Microsoft 365 and Exchange Online.

### **🛠️ Tech Stack & Tools Used**

* **Infrastructure:** Windows Server 2022, Windows 11 Pro, Windows 10 Enterprise, Oracle VirtualBox  
* **Identity & Cloud:** Active Directory (AD DS), Microsoft 365, Microsoft Entra ID (Azure AD), Exchange Online  
* **Network Services:** DHCP, DNS, Windows Deployment Services (WDS), PXE Boot, TFTP  
* **ITSM & Ticketing:** Jira Service Management  
* **Endpoint Management:** Action1 RMM  
* **Security:** Group Policy (GPO), NTFS/RBAC, Principle of Least Privilege

### **🎯 Core Competencies Demonstrated**

* **Service Desk Ticket Resolution:** Executing complex, real-world MSP requests including MFA session revocation, secure employee offboarding, and deep-level cloud data recovery.  
* **Exchange Online Administration:** Provisioning Shared Mailboxes, managing proxy addresses (aliases) via AD Attribute Editor, and executing Message Traces to troubleshoot mail flow.  
* **Hybrid Cloud Identity:** Bridging on-premise Active Directory with Microsoft 365 and syncing password hashes via Microsoft Entra Connect.  
* **Identity & Access Management (IAM):** Administering Active Directory user lifecycles, configuring account restrictions, and enforcing security policies.  
* **Automated OS Deployment:** Architecting PXE boot environments to deploy Windows operating systems over the network to bare-metal clients.  
* **IT Service Management (ITSM):** Managing the full ticket lifecycle, practicing First Call Resolution (FCR) methodologies, and enforcing SLAs.  
* **Remote Fleet Management:** Deploying third-party software, monitoring endpoint health, and managing patch compliance.  
* **Security & Compliance:** Architecting secure file shares, applying the Principle of Least Privilege, and enforcing Role-Based Access Control.

## **🏗️ Section 0: Infrastructure Implementation**

*Building the foundational server environment and promoting the Domain Controller.*

### **0.1 Virtual Machine Configuration**

*Provisioned a Windows Server 2022 VM with optimized resource allocation (2 vCPU, 8GB RAM) and installed Guest Additions for improved host-to-guest integration.*

### **0.2 Network Configuration & Shared Storage**

*Configured a static IP (10.0.0.10) for the server and established a secure Shared Folder path to simulate a mapped network drive for file transfer.*

### **0.3 Domain Controller Promotion**

*Promoted the server to a Domain Controller (YYC-DC-01) by installing AD DS roles and creating a new forest root domain (belita.com).*

### **0.4 Verification**

*Verified successful deployment of Active Directory Users and Computers (ADUC).*

## **💻 Section 1: Client Workstation Deployment**

*Configuring and joining a Windows 11 endpoint to the corporate domain.*

### **1.1 OS Installation & Selection**

*Selected Windows 11 Pro to ensure domain-joining capabilities, as Windows 11 Home does not support Active Directory integration.*

### **1.2 DNS Configuration**

*Configured the Windows 11 Client DNS settings to point directly to the Domain Controller (10.0.0.10), ensuring successful name resolution for the belita.com domain.*

### **1.3 Domain Join**

*Successfully joined the Windows 11 client to the 'belita.com' Active Directory domain using administrative credentials.*

## **📂 Section 2: Identity & Access Management (Active Directory)**

*Demonstrating core competency in user lifecycle management, security groups, and organizational structure.*

### **2.1 Organizational Unit (OU) Design**

*Designed a hierarchical OU structure to separate 'Admin' accounts from 'Standard Users' and 'Service Accounts,' ensuring granular policy application.*

### **2.2 Advanced User Provisioning**

*Provisioned new user accounts (e.g., Neil Nepu) with standard naming conventions and configured strict Logon Hours/Account Expiry to enhance security.*

### **2.3 End-to-End Verification**

*Verified end-to-end connectivity by logging into the client workstation using the provisioned Active Directory user account.*

## **🗄️ Section 3: File Server & Storage Management**

*Implementing Role-Based Access Control (RBAC) and secure file sharing.*

### **3.1 File Share Hierarchy**

*Designed a structured file share hierarchy (HR, IT, Data) to segregate sensitive departmental data from public common areas.*

### **3.2 NTFS Permissions & RBAC**

*Configured strict NTFS permissions using Security Groups (e.g., 'IT\_Access') rather than individual users, ensuring scalable access management.*

### **3.3 Permission Validation**

*Validated permission inheritance by confirming 'Access Denied' restrictions when unauthorized users attempted to access restricted folders.*

## **⚙️ Section 4: Group Policy & Security Hardening**

*Showcasing the ability to automate configuration and enforce security protocols.*

### **4.1 Password & Lockout Policies**

*Enforced a strict Password Policy (12-char min, 90-day rotation) and Account Lockout Policy (3 attempts) to mitigate brute-force attacks.*

### **4.2 Security Validation (Simulated Attack)**

*Simulated a brute-force attempt and verified that the account was successfully locked out, preventing unauthorized access. Also verified Logon Hour restrictions.*

## **☁️ Section 5: Cloud RMM & Patch Management (Action1)**

*Demonstrating modern, cloud-based fleet management and vulnerability remediation.*

### **5.1 Hybrid Integration (Active Directory Connector)**

*Configured the Action1 AD Connector to automatically discover and sync on-premise assets with the cloud platform, ensuring real-time fleet visibility.*

### **5.2 Vulnerability Management & Patching**

*Performed automated vulnerability assessments to identify critical CVEs and executed patch remediation workflows to secure the environment.*

### **5.3 Automated Software Deployment**

*Leveraged the Action1 App Store to deploy certified third-party applications (7-Zip) to client endpoints without manual intervention.*

## **📡 Section 6: Remote Administration**

*Utilizing built-in Windows tools for remote troubleshooting and management.*

### **6.1 Administrative Shares (C$)**

*Utilized administrative shares (C$) to remotely access and troubleshoot client file systems without interrupting the user's active session.*

## **🎫 Section 7: IT Service Management (Jira Service Management)**

*Proving the ability to manage the ticket lifecycle, SLAs, and user communication.*

### **7.1 Identity Synchronization**

*Synced on-premise Active Directory users to Jira Service Management, ensuring seamless authentication and customer profile management.*

### **7.2 Ticket Triage & Queue Management**

*Managed the IT Service Desk queue, prioritizing high-impact incidents and using Internal Notes to track investigation steps.*

### **7.3 Service Level Agreement (SLA) Engineering**

*Engineered custom SLA metrics for "Time to First Response" (15m) and "Time to Resolution" (2h). Utilized Jira Query Language (JQL) to write specific conditions (priority in (High, Highest)) to ensure critical incidents automatically trigger accelerated support workflows.*

### **7.4 Service Request Fulfillment**

*Configured a self-service Customer Portal for software requests and fulfilled them using automated RMM workflows.*

### **7.5 Incident Management (Break/Fix)**

*Simulated and resolved a high-impact (Priority: Highest) business outage where the HR department lost access to a critical file share. Documented technical root causes in Internal Notes, while providing clear, jargon-free resolution updates to the non-technical end-users.*

* **Simulated Incident:** "URGENT: HR Department cannot access the Confidential Shared Drive."  
* **Root Cause:** The HR Security Group was inadvertently removed from the folder's Access Control List (ACL) on the file server.  
* **Resolution:** Re-applied the correct Role-Based Access Control (RBAC) group to the folder, verified inheritance, and confirmed access with the end-users using non-technical customer service communication.

*Figure 5: Documenting root cause analysis via Internal Notes and communicating the resolution to the end-user.*

*Figure 6: Verifying the technical resolution by restoring the HR security group to the folder's Access Control List.*

## **💿 Section 8: Automated Network OS Deployment (WDS)**

*Architecting a PXE Boot environment to automate bare-metal OS provisioning.*

### **8.1 WDS Server Initialization & Image Management**

*Configured the Windows Deployment Services role integrated with Active Directory. Successfully mounted the Windows 10 ISO, extracting and publishing both the boot.wim (Windows PE) and install.wim (OS payload) to the WDS console.*

### **8.2 Resolving UDP Port Conflicts (DHCP & WDS)**

*Resolved UDP Port 67 conflicts between co-hosted DHCP and WDS roles by configuring WDS to yield the port and appending PXE-specific DHCP options to ensure proper client network routing.*

### **8.3 Advanced TFTP Troubleshooting**

*Diagnosed and resolved TFTP packet fragmentation (Error Code 1460\) by disabling Variable Window Extension and optimizing the Maximum Block Size to ensure reliable boot image delivery over the virtual network.*

### **8.4 Client PXE Boot Execution**

*Provisioned a bare-metal client utilizing a UEFI motherboard and an Intel PRO/1000 network adapter. The client successfully obtained an IP via DHCP, located the WDS server, and initiated the PXE network boot sequence.*

### **8.5 Successful OS Deployment**

*The client seamlessly loaded the Windows Preinstallation Environment (WinPE) over the network, authenticated against Active Directory using Domain Admin credentials, and successfully initiated the automated Windows 10 installation.*

## **☁️ Section 9: Hybrid Cloud Identity & Exchange Online Administration**

*Simulating a modern enterprise environment by bridging on-premise Active Directory with Microsoft 365, Entra ID, and Exchange Online.*

### **9.1 Cloud Identity Synchronization (Entra Connect)**

*Configured Alternative UPN Suffixes and deployed Microsoft Entra Connect Sync. Verified the successful replication of local user identities and password hashes into the Microsoft 365 Admin Center.*

### **9.2 Shared Mailbox Provisioning & Delegation**

*Created an IT Support Shared Mailbox to simulate a zero-cost departmental email routing strategy. Granted the synced user 'Read and Manage' and 'Send As' delegation, verifying successful access via Outlook Web App (OWA).*

### **9.3 AD Attribute Management (Email Aliases)**

*Utilized the Active Directory Attribute Editor to provision a secondary email alias. Manually configured the proxyAddresses attribute with a lowercase smtp: prefix, then executed Start-ADSyncSyncCycle \-PolicyType Delta via PowerShell to force an immediate replication to the cloud.*

### **9.4 Mail Flow Troubleshooting (Message Trace)**

*Simulated an external mail delivery issue. Executed a Message Trace within the Exchange Admin Center to track inbound email traffic, verifying network routing success and identifying Microsoft 365 spam filter (EOP) handling.*

## **🛠️ Section 10: Common Service Desk Requests (Troubleshooting & Admin)**

*Documented execution of the most frequent Tier 1 and Tier 2 tickets encountered in a Managed Service Provider (MSP) environment.*

### **10.1 Ticket 1: The "New Phone" Lockout (Entra ID MFA Reset)**

* **Scenario:** A user purchased a new smartphone over the weekend and lost access to their Authenticator app, locking them out of all Microsoft 365 services.  
* **Resolution:** Instead of performing a standard password reset, I navigated to the Microsoft Entra Admin Center. Under the user's Authentication Methods, I executed **Require re-register MFA** to prompt a new QR code upon their next login, and utilized **Revoke MFA sessions** to kill any active tokens on their previous device.

### **10.2 Ticket 2: Secure Employee Offboarding & License Reclamation**

* **Scenario:** An employee was terminated. Management requested immediate revocation of access, retention of all historical emails, and the removal of the recurring $22/month Business Premium license.  
* **Resolution:** Disabled the user account in local Active Directory and forced a Delta Sync to immediately block cloud sign-in. Navigated to the Exchange Admin Center to convert the user's inbox to a **Shared Mailbox** (retaining all data for free). Finally, stripped the paid license and granted the manager 'Read and Manage' delegation over the newly converted shared mailbox.

### **10.3 Ticket 3: The "Accidental Deletion" (OneDrive Data Recovery)**

* **Scenario:** A user permanently deleted critical files from their OneDrive and emptied their standard Recycle Bin.  
* **Resolution:** Generated an administrative access link to bypass the user's standard permissions and enter their personal SharePoint Site Collection. Navigated to the hidden **Second-Stage Recycle Bin** to successfully recover the hard-deleted files within the Microsoft 93-day retention window.

## **📜 Education & Certifications**

* **CompTIA Security+** | Certified January 2026  
* **Diploma in Cybersecurity** | ABM College, Calgary, AB | Graduated May 2025  
* **Network Specialist Training** | SAIT, Calgary, AB | 2019

## **📫 Contact**

**John Belita** | Calgary, AB | johnalbertbelita@gmail.com

[⬆ Back to Top](https://www.google.com/search?q=https://github.com/chingilik/it-support-portfolio)
