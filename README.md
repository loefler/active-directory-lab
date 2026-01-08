# Active Directory Domain Services Home Lab

## Objective
This lab demonstrates the deployment and administration of a Windows Active Directory Domain Services (AD DS) environment in a controlled virtual lab. The goal was to configure centralized identity management, implement security policies, and troubleshoot common Active Directory and DNS issues relevant to IT support, systems administration, and cybersecurity roles.

---

## Lab Environment
- Host OS: macOS  
- Virtualization: VirtualBox  
- Network Type: Internal Network  
- Systems:
  - Windows Server (Domain Controller – DC01)
  - Windows 10 Pro (Client – CLIENT01)

---

## Lab Overview
The lab was built from scratch to simulate a small enterprise Windows domain. Core infrastructure services were configured first, followed by directory structure design, user and group management, and Group Policy enforcement. Throughout the process, real-world troubleshooting scenarios were encountered and resolved, including DNS resolution issues and domain join failures.

---

## Methodology & Implementation

### 1. Domain Controller Deployment & DNS Configuration
The lab began with the installation and configuration of the Domain Controller.

Actions performed:
- Installed Windows Server and promoted it to a Domain Controller
- Created a new Active Directory forest (`homelab.local`)
- Configured a static IP address for the Domain Controller
- Configured DNS to point to the Domain Controller itself
- Verified DNS zones and service records

This established a stable foundation for directory services and name resolution.

**Screenshots:**  
`screenshots/07-dns-zones.png`
`screenshots/08-dns-zones.png`

---

### 2. Organizational Unit, User, and Group Design
After the domain was operational, directory structure and identity objects were created.

Actions performed:
- Designed Organizational Units (OUs) for IT, HR, and Workstations
- Created user accounts for each department
- Created security groups to support role-based access:
  - IT_Admins
  - HR_Admins
- Assigned users to appropriate groups based on role

This structure mirrors common enterprise Active Directory design practices.

**Screenshots:**  
`screenshots/03-ad-ou-structure.png`  
`screenshots/04-users-and-groups.png`
`screenshots/05-users-and-groups.png`
`screenshots/06-users-and-groups.png`

---

### 3. Client Domain Join & Troubleshooting
A Windows 10 client system was joined to the domain.

Actions performed:
- Configured client networking and DNS settings
- Troubleshot domain join failures caused by DNS and hostname mismatches
- Successfully joined CLIENT01 to the domain
- Verified domain authentication using domain user credentials

This phase reinforced the critical dependency between Active Directory and DNS.

**Screenshots:**  
`screenshots/11-domain-login.png`

---

### 4. Group Policy Configuration & Enforcement
Security and user policies were implemented using Group Policy.

Actions performed:
- Created a domain-level password and account lockout policy
- Configured password complexity, history, and lockout thresholds
- Created a user-level Group Policy restricting access to Control Panel for IT users
- Verified policy application using `gpupdate` and `gpresult`

This demonstrated proper policy scoping and enforcement at both the domain and OU levels.

**Screenshots:**  
`screenshots/09-group-policy-links`  
`screenshots/10-group-policy-links.png`  
`screenshots/12-control-panel-blocked.png`  
`screenshots/13-gpresult.png`

---

## Results Summary
- Successfully deployed a functional Active Directory domain
- Implemented centralized authentication and authorization
- Designed a realistic OU and group structure
- Applied and verified security and user-based Group Policies
- Troubleshot and resolved DNS and domain join issues

---

## Key Takeaways
- Active Directory relies heavily on proper DNS configuration
- Static IP configuration is critical for Domain Controllers
- OU design enables scalable policy and identity management
- Group Policy precedence and scope are essential for correct enforcement
- Systematic troubleshooting is key to resolving domain issues

---

## Next Steps
- Implement DHCP on the Domain Controller
- Configure additional Group Policies (drive mapping, login banners)
- Add a second Domain Controller to explore replication
- Integrate logging and monitoring for security visibility
