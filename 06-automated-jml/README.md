# Automated IAM Lifecycle (JML) Lab – Microsoft Entra ID

## 📌 Overview
This project demonstrates an automated Joiner–Mover–Leaver (JML) lifecycle using Microsoft Entra ID.

The solution leverages dynamic groups and user attributes to automatically provision, modify, and revoke access without manual intervention.

---

## 🧱 Architecture

User → Attribute (Department) → Dynamic Group → Access (Application / Role)

---

## ⚙️ Implementation

### 1. User Attributes
- Configured user properties such as:
  - Department (IT, HR, Sales)

---

### 2. Dynamic Groups (ABAC)

Created dynamic security groups based on department:

- IT-Dynamic-Team  
  Rule:
  (user.department -eq "IT")

- HR-Dynamic-Team  
  Rule:
  (user.department -eq "HR")

- Sales-Dynamic-Team  
  Rule:
  (user.department -eq "Sales")

---

### 3. Access Assignment (RBAC)

- Assigned applications to groups:
  - HR-Dynamic-Team → HR Application (SSO)
- Demonstrated role-based access using group membership (where applicable)

---

### 4. Automation Scenarios

#### ✅ Joiner (User Onboarding)
- Created new user with department = IT  
- User automatically added to IT-Dynamic-Team  
- Access granted automatically  

---

#### 🔄 Mover (Role Change)
- Updated user department: IT → HR  
- User automatically removed from IT group  
- Added to HR group  
- Access updated automatically  

---

#### 🚪 Leaver (Offboarding)
- Disabled user account  
- Access effectively revoked  

---

## 🧠 Key Concepts

- Identity Lifecycle Management (JML)
- Dynamic Groups
- Attribute-Based Access Control (ABAC)
- Role-Based Access Control (RBAC)
- Least Privilege
- Access Automation

---

## 📸 Screenshots

(Add screenshots here)

- Dynamic group rules  
- User attribute update  
- Automatic group membership  
- Application access assignment  

---

## ⚠️ Challenges & Learning

### Challenge
Understanding limitations of assigning privileged roles directly to groups.

### Solution
- Used group-based access for applications
- Used Privileged Identity Management (PIM) for admin roles

### Key Learning
- IAM design requires balancing automation with security controls
- Not all roles support group-based assignment
- PIM is preferred for privileged access

---

## 🌍 Real-World Relevance

This project simulates how modern organizations automate identity lifecycle management using attribute-driven access control.

It reduces manual effort, improves consistency, and enhances security by ensuring users always have appropriate access.

---

## 🚀 Future Improvements

- Integrate HR system for automated user provisioning
- Automate lifecycle using PowerShell / scripts
- Implement access reviews and governance policies
