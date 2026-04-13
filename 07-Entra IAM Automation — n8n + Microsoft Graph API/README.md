

# Entra IAM Automation — n8n + Microsoft Graph API

Automated user provisioning and RBAC group assignment using n8n workflows and Microsoft Entra ID (Azure AD)

## Overview

This project automates the full identity lifecycle for new employees using **n8n**, **Microsoft Graph API**, **Postman** and **Microsoft Entra ID**. When a new user is onboarded via a webhook trigger, the workflow automatically:

- Creates the user in Microsoft Entra ID
- Detects their department
- Assigns them to the correct security group (RBAC)
- Creates a new group dynamically if one doesn't exist

## Workflow Architecture

<img width="581" height="97" alt="image" src="https://github.com/user-attachments/assets/50d3401f-75e3-4aa6-a87a-f192d57e0711" />


<img width="1090" height="347" alt="image" src="https://github.com/user-attachments/assets/513785f9-fb16-4696-ab7a-0f8644f77ef3" />


<img width="891" height="1364" alt="image" src="https://github.com/user-attachments/assets/aa3cb62a-dec6-4bbe-8afd-bc2108744567" />


## Tech Stack

| Tool | Purpose |
|---|---|
| **n8n** | Workflow automation engine |
| **Microsoft Graph API** | Entra ID user & group management |
| **Microsoft Entra ID** | Identity provider (Azure AD) |
| **OAuth 2.0 (Client Credentials)** | Token-based authentication |
| **Postman** | Webhook testing |

## Features

- **Auto User Provisioning** — Creates Entra ID users with UPN, display name, mail nickname
- **RBAC Group Assignment** — Maps department field to security group automatically
- **Dynamic Group Creation** — If department group doesn't exist, creates it on the fly
- **Propagation Handling** — Built-in Wait node handles Microsoft Graph API delay for new groups
- **Extensible Mapping** — Department → Group ID map in Code node, easy to extend

## Webhook Payload Sample Input in Postman:

```json
{
    "firstName": "John",
    "lastName": "Doe",
    "department": "HR"
}
```

## Department → Group Mapping

| Department | Group | 
|---|---|
| HR | HR | 
| IT | IT | 
| Sales | Sales | 
| Admin | Admin | 
| Account | Account | 
| Any new dept | Auto-created |


## Testing

## Pre- Automation Status: 

- 12 Users in Entra ID
- 12 groups created
- Account group has only one user assigned i.e. Sue Fong

https://github.com/user-attachments/assets/549e9151-55d2-49a4-b12e-f5893e80b0e5

Use Postman to trigger the workflow:

## Scenarion 1: User created and added to existing group

```bash
POST http://localhost:5678/webhook-test/entra-onboard
Content-Type: application/json

{
    "firstName": "Bela",
    "lastName": "Shah",
    "department": "Account"
}


```

---

## Scenarion 2: User created and added to newly created group

```bash
POST http://localhost:5678/webhook-test/entra-onboard
Content-Type: application/json

{
    "firstName": "Tania",
    "lastName": "Brown",
    "department": "Compliance"
}


```

---

## Post- Automation Status: 

## Scenarion 1 Results:

- User 'Bela Shah' created in Entra ID
- Bela Shah assigned to existing Account group

## Scenarion 2 Results:

- User 'Tania Brown' created in Entra ID
- Compliance group created ( newly created group, not exists)
- Tania Brown assigned to Compliance group



https://github.com/user-attachments/assets/db77559e-480a-4098-a5fd-d9fa6f2b7845


## Learning Outcomes:

- Identity lifecycle automation
- RBAC implementation
- API integration with Microsoft Graph
- Workflow orchestration
