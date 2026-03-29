# Dynamic Groups Lab

## Overview

This project demonstrates automated group membership using dynamic rules in Microsoft Entra ID. I configured and implemented dynamic groups using attribute-based rules to automate user access based on department i.e. Attribute-Based Access Control (ABAC).

## Steps Implemented

- Initially checked overivew of IT group where there is only one user (Sumit).

<img width="1640" height="502" alt="Initial IT Group member" src="https://github.com/user-attachments/assets/70fa7d0a-11e4-4af7-8dca-f593d9d072af" />

- Now created dynamic security group (IT-Dynamic-Team)

<img width="1658" height="489" alt="Dynamic Group Overivew" src="https://github.com/user-attachments/assets/92329105-50a8-4dc1-8227-91b707d46abb" />

- Defined rule based on user attributes (department) i.e. user will automaticaly granted access to IT group if they are in IT deaprtment.

<img width="1634" height="663" alt="Dynamic Group Rule" src="https://github.com/user-attachments/assets/deff5b9b-1ae8-4e60-8863-e580ca2dcfa2" />

- Move one of the non-IT department user (Ruby) from Admin to IT department. Verified automated user assignment to dynamic group.

<img width="1608" height="601" alt="Updated IT Group members" src="https://github.com/user-attachments/assets/789e0d31-7719-46e2-9306-cdb455247eeb" />

## Key Concepts
- Dynamic Groups
- Attribute-Based Access Control (ABAC)
- Identity Automation

## Real-World Relevance
Dynamic groups reduce manual effort and ensure users receive correct access automatically based on their role or department.
