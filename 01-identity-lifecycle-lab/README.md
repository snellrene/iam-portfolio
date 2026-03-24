# Identity Lifecycle Management Lab (Joiner-Mover-Leaver)

This project simulates real-world IAM lifecycle processes used in enterprises. I implemented end-to-end IAM lifecycle management using Entra ID, including RBAC, MFA, and secure offboarding.

## Objective

Demonstrate Joiner, Mover, Leaver process using Microsoft Entra ID.

## Tools Used

* Microsoft Entra ID

## Scenario 1: Joiner (User Onboarding)

(Created a new employees and assigned access respective to their Group/Role)

“I onboarded below users in Entra ID and assigned access using security groups aligned to their roles (RBAC).”

<img width="408" height="121" alt="User Onboarding" src="https://github.com/user-attachments/assets/eb30d590-32ec-491a-81ca-753bf2042060" />

## Screenshots: Joiner

<img width="1916" height="818" alt="Users" src="https://github.com/user-attachments/assets/ce30f59c-6c53-4820-a0bc-8b1fdb9cc354" />

<img width="1917" height="643" alt="Groups" src="https://github.com/user-attachments/assets/7365e2bf-ff45-4f31-a649-5c3ad1070159" />

<img width="1914" height="681" alt="Account Group" src="https://github.com/user-attachments/assets/f342a92d-4501-43a3-93fa-80b218b9a495" />

<img width="1904" height="644" alt="IT Group" src="https://github.com/user-attachments/assets/a5cce4fa-208b-4840-af03-ae32db8b73a9" />

<img width="1914" height="470" alt="IT Group Member" src="https://github.com/user-attachments/assets/9d9be557-80fb-4183-af2d-6e814bc3ac5d" />


<img width="1916" height="818" alt="image" src="https://github.com/user-attachments/assets/e0b1ab06-4b4d-44cb-b8e3-b67687bf8e66" />

<img width="1917" height="643" alt="image" src="https://github.com/user-attachments/assets/a5500526-ed3a-42f0-a65e-66ac0419a0a8" />

<img width="1914" height="681" alt="image" src="https://github.com/user-attachments/assets/b4e6882c-8041-4f2b-8dc8-03a249959382" />

<img width="1904" height="644" alt="image" src="https://github.com/user-attachments/assets/1653f383-a7bc-475a-98a3-fd397e26f0b0" />

<img width="1914" height="470" alt="image" src="https://github.com/user-attachments/assets/35e00a8b-156f-48ef-9bdb-0331ac6f4964" />

## Scenario 2: Mover

(I handled a mover (Rob) scenario by removing outdated sales access and reassigning role-based access for IT using group membership and thus eliminate security risks.)

## Screenshots: Mover

<img width="1908" height="475" alt="Mover User 1" src="https://github.com/user-attachments/assets/a9ffe03d-aeb6-4f8f-af26-aec4d4086799" />

<img width="1910" height="444" alt="Mover User 2" src="https://github.com/user-attachments/assets/813bc307-0cd9-423a-a081-814c775a5f7a" />

<img width="1908" height="475" alt="image" src="https://github.com/user-attachments/assets/b91b2b13-5299-4a83-86f0-70407cc8a6ac" />

<img width="1910" height="444" alt="image" src="https://github.com/user-attachments/assets/21e57452-ec54-490e-b522-18b29f6e241c" />

## Scenario 3: Leaver (User Offboarding)

(I performed secure offboarding for Sumit_IT by blocking sign-in and removing all group-based access to ensure no residual permissions remained.)

## Screenshots: Leaver

<img width="1905" height="762" alt="Leaver User" src="https://github.com/user-attachments/assets/ed4b3308-af69-48c6-ac2d-724b20cd1428" />

<img width="1907" height="423" alt="IT Group Member V1" src="https://github.com/user-attachments/assets/0263f87f-c2bb-4036-aa2a-a8ebe65d1ca2" />

<img width="1896" height="563" alt="Users V1" src="https://github.com/user-attachments/assets/8c1fcb3b-faf3-4e09-af89-1431966fd530" />


<img width="1907" height="423" alt="image" src="https://github.com/user-attachments/assets/d6d513e2-f766-43d4-bf51-0c6fa9752576" />

<img width="1905" height="762" alt="image" src="https://github.com/user-attachments/assets/f3a4b4fa-2d0f-46a0-bd77-bad360500aac" />

<img width="1896" height="563" alt="image" src="https://github.com/user-attachments/assets/3e0b73b5-3196-4a56-9a2a-202851dfed8a" />

Sumit_IT is now: Blocked from signing in, Not in any group and his account deleted. This prevents Data theft, Unauthorized access and Insider threats.

## Multi-Factor Authenticator (MFA)

To enhance identity therft security I add extra protection to users by enabling MFA (Multi-Factor Authentication). Now even user password compromise user needs second verdification as per enterprise preferences and policies. The following additional forms of verification can be used with Microsoft Entra multifactor authentication:

- Microsoft Authenticator
- Windows Hello for Business
- Passkey (FIDO2)
- Passkey in Microsoft Authenticator
- QR code
- SMS
- Voice call

  <img width="1903" height="629" alt="MFA enables" src="https://github.com/user-attachments/assets/9116351d-614b-40b9-9c9e-e53abb74a54e" />

  <img width="1216" height="484" alt="Alice_HR MFA" src="https://github.com/user-attachments/assets/475bb317-798d-4468-9306-78f9ba9f8bb9" />

  <img width="1903" height="629" alt="image" src="https://github.com/user-attachments/assets/6a6fc1e6-91aa-4067-9f40-f22fbb8ea6f8" />

  <img width="1893" height="699" alt="image" src="https://github.com/user-attachments/assets/13cfb225-4a30-4be5-b01b-8d4f10895ad8" />

## Real-World Impact: 

This project simulates real IAM operations performed in organizations to manage user access securely and reduce security risks.













