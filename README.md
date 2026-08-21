# microsoft-sc900-zero-trust-blueprint
A comprehensive Zero Trust security architecture case study (Financial Services / Hybrid Workplace) and quick reference guide for Microsoft Security, Compliance, and Identity Fundamentals (SC-900).

![Microsoft Azure](https://img.shields.io/badge/Microsoft_Azure-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![Certification](https://img.shields.io/badge/SC--900-Preparing-yellow?style=for-the-badge)
![Security Architecture](https://img.shields.io/badge/Architecture-Zero_Trust-blue?style=for-the-badge)

Professional reference repository for **Microsoft Security, Compliance, and Identity**. It contains a **Practical Zero Trust Architecture Case Study** for a financial organization and a **Quick Reference Guide (Cheat Sheet)** based on the skills measured in the **SC-900** exam.

---

## PART 1: Security Architecture Case Study

### Project Context
A financial services company is transitioning to a permanent hybrid work model. They need to secure employee access from any location, protect sensitive financial data (like credit card numbers and banking records) from leaking, and monitor their endpoints for advanced threats. The architecture strictly follows the **Zero Trust** principle: "Trust no one, verify everything."

### Solution Architecture Diagram (Zero Trust Flow)

```text
                       [ REMOTE USERS / EMPLOYEES ]
                                    │ (Access Request)
                                    ▼
                      [ Microsoft Entra ID ] (The Bouncer)
                       ├── Authentication (MFA / Passwordless)
                       └── Conditional Access (Checks Risk & Device)
                                    │
               ┌────────────────────┴────────────────────┐
               ▼                                         ▼
[ Microsoft Defender XDR ] (The CCTV & Guards)   [ Microsoft Purview ] (The Vault Manager)
 │                                                │
 ├── Defender for Endpoint (Secures Laptops)      ├── Sensitivity Labels (Tags data)
 ├── Defender for Office 365 (Scans Emails)       ├── DLP Policies (Blocks data leaks)
 └── Defender for Cloud Apps (Secures SaaS)       └── Insider Risk (Monitors behavior)
               │                                         │
               └────────────────────┬────────────────────┘
                                    ▼
                         [ CORPORATE RESOURCES ]
                   (M365, Cloud Apps, Financial Data)
```

### Services Breakdown & The "Why" (Guts of the Solution)

| Component | Selected Service | The "Why" & How it works (ELI5) |
| :--- | :--- | :--- |
| **Identity / Access** | **Microsoft Entra ID** | **The Bouncer:** It checks your ID before letting you in. Uses **Conditional Access** to say "You can only access the finance app if you use MFA and a company laptop." |
| **Admin Protection** | **Privileged Identity Management (PIM)** | **The Temporary VIP Pass:** Instead of giving admins permanent keys to the kingdom, they must request access *only* when needed, and it expires after a few hours. |
| **Threat Protection** | **Defender for Endpoint** | **The On-Site Guards:** An AI-powered guard that lives on every laptop and phone, watching for malicious behavior and stopping malware in its tracks. |
| **Email Security** | **Defender for Office 365** | **The Mail Inspector:** Scans all incoming emails in a safe "sandbox" to catch phishing links and malicious attachments before they reach the inbox. |
| **Data Security** | **Purview Information Protection** | **The Sticky Stamp:** Classifies and labels documents (e.g., "Highly Confidential"). This label travels with the file everywhere, applying encryption if needed. |
| **Data Loss Prevention** | **Purview DLP** | **The Exit Checkpoint:** If an employee tries to email a list of credit card numbers to a personal Gmail account, DLP detects the pattern and blocks the action. |

---

## PART 2: SC-900 Fundamentals & Cheat Sheet

### 1. Key Security Concepts
* **Zero Trust:** Assume breach. Verify explicitly, use least privileged access. The perimeter is no longer the network; it's the **Identity**.
* **Shared Responsibility Model:** In the cloud (SaaS/PaaS/IaaS), you always own your **Data, Identities, and Endpoints**.
* **Defense in Depth:** Using multiple overlapping layers of security (Physical, Network, Compute, App, Data) so if one fails, the next one stops the attacker.

### 2. The Microsoft Security Ecosystem
* **Microsoft Entra:** "Who are you?" (Identity, Access, Governance, B2B/B2C).
* **Microsoft Defender:** "Is someone attacking us?" (XDR, Threat Intelligence, Endpoint, Email, Cloud security).
* **Microsoft Purview:** "Is our data safe and compliant?" (DLP, Retention, eDiscovery, Insider Risk).

### 3. Authentication vs. Authorization
* **Authentication (AuthN):** Proving *who* you are (e.g., MFA, Passkeys, Windows Hello).
* **Authorization (AuthZ):** Determining *what* you can do once inside (e.g., RBAC, Least Privilege).

---

## Official Certification
* **Exam:** SC-900: Microsoft Security, Compliance, and Identity Fundamentals
* * **Date Achieved:** 21st August
* **Status:** ✅ Passed / Officially Certified
