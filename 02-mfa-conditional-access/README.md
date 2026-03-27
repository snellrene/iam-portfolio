# Policy 01: MFA Enforced Conditional Access 

Company wants to enforce MFA for all users accessing any cloud application. I configured a Conditional Access policy to enforce MFA across all users and cloud applications, aligning with Zero Trust principles (Never Trust, Always Verify). While testing Conditional Access, I encountered a user access issue due to unmet policy conditions and resolved it by reviewing and adjusting the policy.

## Overview
Implemented Conditional Access policy to enforce secure authentication using MFA in Entra ID.

## Policy Implemented
- Require MFA for all users
- Applied to all cloud applications

## Key Concepts
- Conditional Access
- Zero Trust Security
- MFA Enforcement

## Screenshots for MFA enforced conditional access policy

<img width="1913" height="745" alt="CA01 Policy" src="https://github.com/user-attachments/assets/36f80058-743c-41d4-8ca1-a3b3e94b0daa" />

<img width="1903" height="913" alt="CA01 Policy_require MFA for all users" src="https://github.com/user-attachments/assets/640525c3-169f-45c1-9f09-5d22ca58f0d1" />

# Policy 02: Block Risky Access 
Company wants to Block access from unknown locations/netwrok. I configured a Conditional Access policy to enforce blocking access from untrusted network/location.

## Overview
Implemented Conditional Access policy to block access from untrusted network/locations.

## Key Concepts
- Conditional Access
- Zero Trust Security
- Verify Explicitly: Always authenticate based on all available data points (user identity, network, location, device health)

## Screenshots for Block Risky Access policy

<img width="1906" height="695" alt="CA02 Policy" src="https://github.com/user-attachments/assets/d2d6be34-529a-4e0e-a71f-507f27d1247f" />

<img width="1895" height="894" alt="CA02 Policy_block untrusted access" src="https://github.com/user-attachments/assets/f9398347-3196-4030-9539-e91945b36f52" />

## ⚠️ Challenge Faced: Conditional Access Blocking User Access

### Issue
While testing Conditional Access policies, a user account was unable to access applications after successful sign-in.

Error:
"You cannot access this right now. Your sign-in was successful but does not meet the criteria to access this resource."

<img width="518" height="487" alt="sign in blocked by condition access " src="https://github.com/user-attachments/assets/448a9167-6324-4ef9-9902-d1df70a6d3ae" />

### Root Cause
The Conditional Access policy required specific conditions (such as MFA or location), which were not satisfied by the user during login.

### Resolution
- Reviewed the Conditional Access policy configuration
- Identified missing requirements (e.g., MFA or trusted location)
- Updated policy conditions or ensured the user met the required criteria
- Retested access successfully

<img width="848" height="742" alt="MFA implemented" src="https://github.com/user-attachments/assets/0d5dd414-d246-4022-8623-5e09d220c329" />

### Key Learning
- Conditional Access policies must be carefully tested before applying broadly
- Policies can unintentionally block legitimate users if conditions are too strict
- Monitoring and troubleshooting user access is a key IAM responsibility
- Excluding administrative (break-glass) accounts
- Testing policies before full enforcement
- Avoiding complete tenant lockout
- 
### Real-World Relevance
In real organizations, Conditional Access misconfigurations can impact business operations by blocking legitimate users. IAM teams must balance security with usability.
This project demonstrates how organizations enforce security policies to protect user identities and prevent unauthorized access.

