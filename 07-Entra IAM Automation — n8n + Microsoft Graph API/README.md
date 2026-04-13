# Entra IAM Automation — n8n + Microsoft Graph API

Automated user provisioning and RBAC group assignment using n8n workflows and Microsoft Entra ID (Azure AD)

## Overview

This project automates the full identity lifecycle for new employees using **n8n**, **Microsoft Graph API**, and **Microsoft Entra ID**. When a new user is onboarded via a webhook trigger, the workflow automatically:

- Creates the user in Microsoft Entra ID
- Detects their department
- Assigns them to the correct security group (RBAC)
- Creates a new group dynamically if one doesn't exist

## Workflow Architecture


Webhook → Format User Data → Get Token → Create User
       → Department Check → Group Allocation (IF)
            TRUE  → Group Creation → Wait → Resolve Group ID → Assign User to Group
            FALSE → Resolve Group ID → Assign User to Group


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

## Webhook Payload

```json
{
    "firstName": "John",
    "lastName": "Doe",
    "department": "HR"
}
```

---

## Department → Group Mapping

| Department | Group | 
|---|---|
| HR | HR | 
| IT | IT | 
| Sales | Sales | 
| Admin | Admin | 
| Account | Account | 
| Any new dept | Auto-created |


## Nodes Breakdown

### 1. Webhook
Listens for POST requests with user data. Triggers the workflow on new employee onboarding.

### 2. Format User Data (Code Node)
Extracts and sanitizes `firstName`, `lastName`, `department` from the webhook payload. Builds `displayName`, `userPrincipalName`, and `mailNickname`.

### 3. Get Token (HTTP Request)
Authenticates with Microsoft identity platform using OAuth 2.0 client credentials flow. Returns a Bearer token for Graph API calls.

### 4. Create User (HTTP Request)
Posts to `https://graph.microsoft.com/v1.0/users` to create the new Entra ID user with a temporary password.

### 5. Department Check (Code Node)
Maps the department to an existing group ID. If no match found, sets `needsNewGroup: true`.

### 6. Group Allocation (IF Node)
Routes to TRUE branch (create new group) or FALSE branch (use existing group).

### 7. Group Creation (HTTP Request) — TRUE branch only
Creates a new Security group in Entra ID via Graph API.

### 8. Wait Node — TRUE branch only
Waits 10 seconds for Microsoft Graph API to propagate the new group before assigning members.

### 9. Resolve Group ID (Code Node)
Picks the correct group ID — either from the newly created group or the existing group map.

### 10. Assign User to Group (HTTP Request)
Adds the user as a member of the resolved group using `POST /groups/{id}/members/$ref`.

---

## Setup

### Prerequisites
- n8n instance (self-hosted or cloud)
- Microsoft Entra ID tenant
- Azure App Registration with these API permissions:
  - `User.ReadWrite.All`
  - `Group.ReadWrite.All`
  - `Directory.ReadWrite.All`

### Environment Variables
Configure the following in your Get Token node:
```
tenant_id     = YOUR_TENANT_ID
client_id     = YOUR_CLIENT_ID
client_secret = YOUR_CLIENT_SECRET
```

### Graph API Permissions
Grant admin consent for:
- `User.ReadWrite.All`
- `Group.ReadWrite.All`
- `Directory.ReadWrite.All`

---

## Testing

Use Postman to trigger the workflow:

```bash
POST http://localhost:5678/webhook-test/entra-onboard
Content-Type: application/json

{
    "firstName": "Jane",
    "lastName": "Doe",
    "department": "DevOps"
}
```

---

## Results

- User `jane.doe@yourtenant.onmicrosoft.com` created in Entra ID
- DevOps group created (if not exists)
- Jane Doe assigned to DevOps group

---

## Project Structure

```
entra-iam-automation/
├── README.md
├── workflow/
│   └── entra-iam-automation.json    # n8n workflow export
├── screenshots/
│   ├── workflow-canvas.png
│   ├── user-created.png
│   └── group-assigned.png
└── docs/
    └── setup-guide.md
```

---

