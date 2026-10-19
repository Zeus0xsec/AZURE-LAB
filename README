# ☁️ Azure & Entra ID Security Lab

[![EN](https://img.shields.io/badge/Language-English-blue.svg)](README.md)
[![PL](https://img.shields.io/badge/Język-Polski-red.svg)](README_PL.md)

## 📌 About the Project
Deployment and configuration of a cloud identity environment based on **Microsoft Azure** and **Microsoft Entra ID** (formerly Azure AD). This project focuses on Identity and Access Management (IAM), cloud cost management, role-based access control (RBAC), and SOC L1 log analysis.

## 🛠️ Technologies Used
- **Cloud Provider:** Microsoft Azure
- **Identity Provider:** Microsoft Entra ID (Entra Admin Center)
- **Security & Compliance:** Azure RBAC, Least Privilege Enforcement, Sign-in Logs Analysis
- **Cost Management:** Azure Cost Management & Budget Alerts

---

## 🏛️ Architecture: Local AD DS vs. Cloud Entra ID

| Feature / Concept | 🏢 On-Premises (Active Directory DS) | ☁️ Cloud (Microsoft Entra ID) |
| :--- | :--- | :--- |
| **Primary Focus** | Local identity & machine management in corporate LAN. | Cloud identity, web app access (M365, SaaS, Azure portal). |
| **Core Server** | Domain Controller (DC). | Fully managed cloud service by Microsoft. |
| **Authentication** | Kerberos, NTLM. | OAuth 2.0, SAML 2.0, OpenID Connect. |
| **Hierarchy** | Organizational Units (OUs) and Forest trees. | Flat structure based on Security and M365 Groups. |
| **Device Management**| Group Policy Objects (GPOs). | Microsoft Intune (MDM / MAM). |
| **Access Example** | Logging into a physical desktop at the office. | MFA-protected login to Outlook web email. |

---

## 🚀 Completed Tasks & Evidence

### 1. Azure Cost Management & Budgeting
Created a strict cloud budget alert to prevent unexpected charges during testing.
- **Budget Amount:** $10.00 USD
- **Threshold Alert:** Automated e-mail notification triggered at 80% ($8.00 USD).

<img width="1000" alt="Azure Budget Configuration" src="budget.png" />

---

### 2. Cloud Identity & Group Management
- Created 5 cloud user accounts with forced password reset requirements on first login.
- Configured security groups (`IT-Helpdesk`, `Sales`) for group-based access control.
- Verified identity lifecycle by performing initial test account sign-ins on `myaccount.microsoft.com`.

<img width="1000" alt="Successful Test Account Sign-in" src="uzytkownik.jpg" />

---

### 3. Principle of Least Privilege (Entra ID Roles)
Tested security boundaries between administrative roles to prevent unauthorized privilege escalation.
- **Assigned Role:** `Helpdesk Administrator` assigned to test user `Jan Kowalski`.
- **Test 1 (Password Reset):** **SUCCESS** — User successfully performed password reset for standard domain user `Adam Drabina`.
- **Test 2 (Role Modification):** **BLOCKED** — Role assignment options were disabled when attempting to edit user roles, enforcing strict boundary controls.

<img width="1000" alt="Role Assignment Helpdesk Admin" src="przypisanie roli.png" />
<img width="1000" alt="Helpdesk Password Reset Success" src="resethaslazkontauzytkownika.png" />
<img width="1000" alt="Access Denied on Role Modification" src="brakuprawnien.png" />

---

### 4. Incident Analysis: Sign-in Logs (Cloud Event ID 4625 Equivalent)
Simulated authentication failures to analyze security telemetry within Entra ID Sign-in Logs.
- **Event Type:** Failed Sign-in (`Failure` status).
- **Target User:** `admin.jan@--------.onmicrosoft.com`
- **Sign-in Error Code:** `50126` (*Invalid credentials / Incorrect password*).
- **Source IP & Location:** `46.205.197.181` (Huba, Malopolskie, PL).
- **Application:** `My Profile` via Windows 10 Web Browser.
- **SOC L1 Triage:** Detected 2 failed password attempts originating from a known domestic IP address. No evidence of distributed Password Spraying or brute-force automation. Ticket closed as user entry error.

<img width="1000" alt="Entra ID Sign-in Logs Failed Entries" src="logowaniefailed.png" />
<img width="1000" alt="Detailed Log Diagnostics Error 50126" src="szczegolydzialan.png" />

---

## 🔮 Next Steps
The next phase involves building a **Hybrid Identity Architecture** — connecting this cloud environment directly with the local Windows Server Active Directory domain using **Entra Connect / Cloud Sync**.
