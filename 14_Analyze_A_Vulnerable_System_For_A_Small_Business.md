# Vulnerability Assessment Report

### System Description

The system is a **Linux operating system** hosting a **MySQL database management system**.
It is configured with a stable network connection using **IPv4 addresses** and interacts with other servers on the network.
Security measures include **SSL/TLS encrypted connections**.

### Scope

The scope of this vulnerability assessment relates to the **current access controls** of the system.
The assessment covers a period of **three months (June 20XX – August 20XX)**.
**NIST SP 800-30 Rev. 1** is used to guide the risk analysis of the information system.

---

## Purpose

The company’s remote database server is a **critical business asset** that stores customer and sales information essential for e-commerce operations. Securing this data is vital to maintaining **customer trust**, protecting **intellectual property**, and ensuring **compliance** with privacy laws. If the server were disabled or compromised, it could **disrupt operations**, **cause financial loss**, and **damage the company’s reputation**.
This vulnerability assessment identifies the risks associated with the publicly accessible database and recommends actions to **enhance security** and **protect business continuity**.

---

## Risk Assessment

| Threat Source              | Threat Event                                  | Likelihood (1–3) | Severity (1–3) | **Risk (L×S)** |
| -------------------------- | --------------------------------------------- | ---------------- | -------------- | -------------- |
| Hacker / Outsider          | Obtain sensitive information via exfiltration | 3                | 3              | **9**          |
| Competitor                 | Conduct Denial of Service (DoS) attack        | 2                | 3              | **6**          |
| Privileged User (Employee) | Alter/Delete critical information             | 2                | 2              | **4**          |

---

## Approach

This qualitative risk assessment focuses on **the confidentiality, integrity, and availability** of the company’s remote database.
The threats were selected based on their **relevance to a publicly accessible system** and their **potential impact on business operations**.
Unauthorized access by external attackers poses a **high risk of data theft**, while denial-of-service attacks could **disrupt sales and customer interactions**.
Accidental or malicious insider actions also present **moderate risks** to data integrity.
These threats represent the most significant and realistic risks to the company’s e-commerce operations.

---

## Remediation Strategy

To mitigate these vulnerabilities, the company should **restrict public access** to the database by implementing **firewall rules and IP allow-listing** to corporate networks only.
Introduce **multi-factor authentication (MFA)** and **role-based access controls (RBAC)** to enforce the **principle of least privilege**.
Encrypt data both **in transit (TLS 1.3)** and **at rest**, and enable **audit logging** to detect and respond to suspicious activity.
Additionally, deploy a **web application firewall (WAF)** and **intrusion detection system (IDS)** to monitor and block malicious traffic, ensuring a **defense-in-depth** security posture.
