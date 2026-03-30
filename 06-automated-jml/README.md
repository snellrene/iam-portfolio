# Automated IAM Lifecycle (JML) Lab using Microsoft Entra ID

##  Overview

This project demonstrates an automated Joiner–Mover–Leaver (JML) lifecycle using Microsoft Entra ID. The solution leverages dynamic groups and user attributes to automatically provision, modify, and revoke access without manual intervention.

##  Architecture

User → Attribute (Department) → Dynamic Group → Access (Application / Role)

##  Implementation

### 1. User Attributes
- Configured user properties such as:
  - Department (IT, HR, Sales)

<img width="1622" height="673" alt="Users" src="https://github.com/user-attachments/assets/4f431b21-34bc-48c2-b0f0-d04530c43bda" />

### 2. Dynamic Groups (ABAC)

Created dynamic security groups based on departments:

- IT-Dynamic-Team  
  Rule:
  (user.department -eq "IT")

- HR-Dynamic-Team  
  Rule:
  (user.department -eq "HR")

- Sales-Dynamic-Team  
  Rule:
  (user.department -eq "Sales")

  <img width="1603" height="674" alt="Dynamic Groups" src="https://github.com/user-attachments/assets/5fedf6a8-8aac-4c5d-99d8-04af0995b6f8" />

### 3. Access Assignment (RBAC)

- Assigned applications to groups:
- HR-Dynamic-Team → HR Application (SailPoint IdentityNow)
- Admin-Dynamic-Team → Application (SAP SuccessFactors)
- Demonstrated role-based access using group membership (where applicable)

<img width="1647" height="548" alt="HR does not have access to any App" src="https://github.com/user-attachments/assets/c9283050-fe7b-4a2f-8a8f-c5c497ba504e" />

<img width="1637" height="657" alt="App assigned to HR Group" src="https://github.com/user-attachments/assets/0c312381-de27-401d-a5fa-cf0f50794bf0" />

<img width="1632" height="428" alt="HR got access to App" src="https://github.com/user-attachments/assets/14c40a73-a420-4002-81a3-d38c61d90440" />


### 4. Automation Scenarios

### Joiner (User Onboarding)
- Created new user with  department = Admin (Claire Black)

<img width="1648" height="729" alt="Admin User added_Joiner" src="https://github.com/user-attachments/assets/2ee88a96-cff4-4a6e-a6fc-9c187327cd57" />

- User automatically added to Admin-Dynamic-Team

<img width="1638" height="550" alt="Admin User added to group" src="https://github.com/user-attachments/assets/a98fb861-4cdd-4d6a-913e-9576390b8231" />

- Application access granted automatically

<img width="1638" height="550" alt="Admin User added to group" src="https://github.com/user-attachments/assets/d49e7127-a15a-443f-b568-b8292f63f4ab" />

### Mover (Role Change)

- Updated user department: IT → HR

<img width="1619" height="746" alt="User moved from IT to HR department" src="https://github.com/user-attachments/assets/e9d285d4-4962-4560-a2df-e4c4bac59923" />

- User automatically removed from IT group

<img width="1612" height="477" alt="User removed from IT Group" src="https://github.com/user-attachments/assets/550362e3-225d-42e8-b865-1228d2768c1c" />
  
- Added to HR group

<img width="1597" height="518" alt="User added to HR Group" src="https://github.com/user-attachments/assets/95a6489d-835c-4c45-9592-00934c78f133" />
  
- Access updated automatically

<img width="1614" height="401" alt="HR User got access to App" src="https://github.com/user-attachments/assets/40bbf32c-57da-405e-a2f1-951e30203178" />

### Leaver (Offboarding)

- Disabled user account

<img width="1619" height="861" alt="HR User offboarded" src="https://github.com/user-attachments/assets/e82ad695-af43-4e75-a1fe-a7c92bdcdde3" />

- Access effectively revoked from Groups and Applications

<img width="1618" height="850" alt="HR User offboarded 2" src="https://github.com/user-attachments/assets/4b53da05-2d2b-4e78-bcf8-390780c927c5" />

Note: Disabling an account alone does not remove users from dynamic groups. Attribute updates are required to trigger automatic deprovisioning.

##  Key Concepts

- Identity Lifecycle Management (JML)
- Dynamic Groups
- Attribute-Based Access Control (ABAC)
- Role-Based Access Control (RBAC)
- Least Privilege
- Access Automation

##  Challenges & Learning

### Challenge
Understanding limitations of assigning privileged roles directly to groups.

### Solution
- Used group-based access for applications

<img width="1624" height="744" alt="HR Application" src="https://github.com/user-attachments/assets/c4f51bc2-6a0d-42f2-8810-ff7b6098f20a" />

- Used Privileged Identity Management (PIM) for admin roles

<img width="1616" height="436" alt="Role assign to IT member using PIM" src="https://github.com/user-attachments/assets/7af46013-e300-4f52-85ce-17a4062094d2" />

### Key Learning
- IAM design requires balancing automation with security controls
- Not all roles support group-based assignment
- PIM is preferred for privileged access

##  Real-World Relevance

This project simulates how modern organizations automate identity lifecycle management using attribute-driven access control.

It reduces manual effort, improves consistency, and enhances security by ensuring users always have appropriate access.

