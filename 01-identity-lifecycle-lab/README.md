# Identity Lifecycle Management Lab (Joiner-Mover-Leaver)

This project simulates real-world IAM lifecycle processes used in enterprises. I implemented end-to-end IAM lifecycle management using Entra ID, including RBAC, MFA, and secure offboarding.

## Objective

Demonstrate Joiner, Mover, Leaver process using Microsoft Entra ID.

## Tools Used

* Microsoft Entra ID

## Scenario 1: Joiner (User Onboarding)

(Created a new employees and assigned access respective to their Group/Role)

“I onboarded below users in Entra ID and assigned access using security groups aligned to their roles (RBAC).”

<img width="408" height="121" alt="image" src="https://github.com/user-attachments/assets/a2bd2c70-32ea-4647-bd69-41bf17f726c2" />

## Screenshots: Joiner

<img width="1916" height="818" alt="image" src="https://github.com/user-attachments/assets/e0b1ab06-4b4d-44cb-b8e3-b67687bf8e66" />

<img width="1917" height="643" alt="image" src="https://github.com/user-attachments/assets/a5500526-ed3a-42f0-a65e-66ac0419a0a8" />

<img width="1914" height="681" alt="image" src="https://github.com/user-attachments/assets/b4e6882c-8041-4f2b-8dc8-03a249959382" />

<img width="1904" height="644" alt="image" src="https://github.com/user-attachments/assets/1653f383-a7bc-475a-98a3-fd397e26f0b0" />

<img width="1914" height="470" alt="image" src="https://github.com/user-attachments/assets/35e00a8b-156f-48ef-9bdb-0331ac6f4964" />

## Scenario 2: Mover

(I handled a mover (Rob) scenario by removing outdated sales access and reassigning role-based access for IT using group membership and thus eliminate security risks.)

## Screenshots: Mover

<img width="1908" height="475" alt="image" src="https://github.com/user-attachments/assets/b91b2b13-5299-4a83-86f0-70407cc8a6ac" />

<img width="1910" height="444" alt="image" src="https://github.com/user-attachments/assets/21e57452-ec54-490e-b522-18b29f6e241c" />

## Scenario 3: Leaver (User Offboarding)

(I performed secure offboarding for Sumit_IT by blocking sign-in and removing all group-based access to ensure no residual permissions remained.)

## Screenshots: Leaver

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

  <img width="1903" height="629" alt="image" src="https://github.com/user-attachments/assets/6a6fc1e6-91aa-4067-9f40-f22fbb8ea6f8" />

  <img width="1893" height="699" alt="image" src="https://github.com/user-attachments/assets/13cfb225-4a30-4be5-b01b-8d4f10895ad8" />













