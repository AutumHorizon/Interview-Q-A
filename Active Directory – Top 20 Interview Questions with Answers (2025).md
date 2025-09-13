# 🗂️ Active Directory Q&A

A collection of commonly asked Active Directory interview questions and answers.

---

## ❓ What is Active Directory?
**Answer:**  
Active Directory (AD) is Microsoft's directory service used to store, organize, and manage objects like users, computers, and resources in a Windows domain environment. It provides authentication, authorization, and centralized management.

---

## ❓ What are the main components of Active Directory?
**Answer:**  
The main components include:  
- **Domain** → logical group of objects like users, computers, groups  
- **Tree** → hierarchical arrangement of multiple domains  
- **Forest** → collection of one or more trees with a common schema and global catalog  
- **Organizational Units (OUs)** → logical containers for delegation and GPO application  
- **Domain Controllers (DCs)** → servers that host ADDS  

---

## ❓ What are FSMO roles?
**Answer:**  
There are five FSMO roles:  
1. Schema Master  
2. Domain Naming Master  
3. RID Master  
4. PDC Emulator  
5. Infrastructure Master  

These roles ensure consistency across AD domains and forests.

---

## ❓ What is a Global Catalog (GC)?
**Answer:**  
The Global Catalog is a distributed data repository that stores a searchable partial replica of all objects in the forest. It assists in login authentication and forest-wide searches.

---

## ❓ What is the difference between LDAP and Kerberos in AD?
**Answer:**  
- **LDAP** → used for querying and modifying directory services  
- **Kerberos** → default authentication protocol in AD, providing secure ticket-based authentication  

---

## ❓ What is the difference between a domain, tree, and forest?
**Answer:**  
- **Domain** → logical group of objects sharing a database  
- **Tree** → set of one or more domains in a hierarchical structure  
- **Forest** → top-level structure containing multiple trees with a shared schema  

---

## ❓ What are Group Policies in AD?
**Answer:**  
Group Policy Objects (GPOs) are settings applied to users and computers for security, software deployment, and configuration management. They ensure centralized control.

---

## ❓ Scenario: A GPO is not applying to a user. How do you troubleshoot?
**Answer:**  
- Run `gpupdate /force`  
- Use `gpresult /R` to check applied policies  
- Verify OU linkage and security filtering  
- Check AD replication and Sysvol health  
- Review Event Viewer logs  

---

## ❓ What is the difference between security groups and distribution groups?
**Answer:**  
- **Security groups** → used to assign permissions to resources  
- **Distribution groups** → used only for email distribution in Exchange  

---

## ❓ What is an RODC and when would you use it?
**Answer:**  
An **RODC (Read-Only Domain Controller)** hosts a read-only copy of the AD database.  
It is used in branch offices with limited security and unreliable connectivity to protect sensitive credentials.

---

## ❓ How does AD replication work?
**Answer:**  
AD uses multi-master replication across Domain Controllers (DCs).  
Replication is managed by sites and site links.  
Critical data is stored in `NTDS.dit` and replicated via the **Knowledge Consistency Checker (KCC).**

---

## ❓ Scenario: A user was removed from a group but still has access to resources. Why?
**Answer:**  
Possible reasons:  
- **Token Caching** → Kerberos ticket still holds old permissions (log off/log on required)  
- **Replication Delay** → group change not yet replicated  
- **Nested Groups/Explicit Permissions** → user may still inherit access  

---

## ❓ What are AD Sites and Services?
**Answer:**  
AD Sites and Services represent the **physical topology of a network**.  
They help optimize replication traffic and ensure clients authenticate to the nearest DC.

---

## ❓ What is the difference between forest trust and external trust?
**Answer:**  
- **Forest trust** → between two forests, **transitive**  
- **External trust** → between a domain in one forest and a domain in another forest, **non-transitive**  

---

## ❓ Scenario: DNS misconfiguration is causing AD login failures. How do you fix it?
**Answer:**  
- Ensure clients use **internal AD DNS servers**  
- Verify `_msdcs.domain.com` SRV records  
- Restart **Net Logon** service to re-register records  
- Run `ipconfig /registerdns`  
- Run `dcdiag /test:DNS`  

---

## ❓ How do you perform an authoritative restore in AD?
**Answer:**  
1. Boot the DC into **Directory Services Restore Mode (DSRM)**  
2. Restore the AD database from backup  
3. Use `ntdsutil` to mark objects as **authoritative**  
4. Replication pushes restored objects to other DCs  

---

## ❓ What is Kerberos delegation?
**Answer:**  
Kerberos delegation allows a service to use a user’s credentials to access another service.  
Types:  
- **Unconstrained Delegation**  
- **Constrained Delegation**  
- **Resource-based Constrained Delegation (RBCD)**  

---

## ❓ What is Active Directory Federation Services (ADFS)?
**Answer:**  
ADFS provides **Single Sign-On (SSO)** across organizational boundaries using claims-based authentication.  
It allows secure access to applications outside the AD forest.

---

## ❓ What is the Protected Users group in AD?
**Answer:**  
The **Protected Users group** enforces restrictions such as:  
- No cached login  
- No delegation  
- Stronger authentication requirements  

It helps secure privileged accounts.

---

## ❓ How do you secure Active Directory in a large enterprise?
**Answer:**  
- Implement MFA and Conditional Access  
- Use a **tiered admin model** and **Privileged Access Workstations (PAWs)**  
- Monitor with **Microsoft Sentinel**  
- Regularly patch Domain Controllers  
- Clean up stale accounts and GPOs  
- Enable **AD auditing** and alerts for privilege escalation  

---
