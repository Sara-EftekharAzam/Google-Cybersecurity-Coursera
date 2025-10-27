# PASTA Threat Model — Sneaker Marketplace Mobile App

> **Note:** I attempted to open the two Google Slides you provided for reference but both require Google sign-in to view. I couldn’t pull content directly from them because of that sign-in requirement. ([Google Docs][1])
> I used the scenario you gave and standard PASTA practices to create the flows, attack tree, and controls below.

---

## I. Objectives (Stage I — Business Objectives)

* **Enable a trusted buyer–seller marketplace** where users can list, buy, and sell sneakers with clear payment flow and ratings to encourage good behavior.
* **Protect user privacy & payment data** to avoid legal exposure and build customer confidence.
* **Fast, responsive UX**: quick checkout and in-app messaging to increase conversion and retention.

---

## II. Technology scope and prioritization (Stage II)

**Technologies listed:** API, PKI (AES & RSA key exchange), SHA-256, SQL database.

**Which to evaluate first & why (40–60 words):**
I prioritize the **payment processing / data encryption stack (AES + RSA + PKI)** because it directly handles payment card and personal data — high-impact assets under regulatory scrutiny. Weaknesses here (key management, improper encryption usage) lead to high-severity breaches and compliance fines, so cryptography and key lifecycle must be validated first.

---

## III. Decompose application (Stage III — Data flow)

**High-level data flow (text flow diagram)**

```
[User Mobile App]
    ├─(1) Auth / Credentials --> [Auth API / Identity Service]
    ├─(2) Browse / Search ---> [Catalog API] ---> [SQL DB: Listings]
    ├─(3) Messaging ---------> [Messaging Service] ---> [Message DB / Queue]
    └─(4) Checkout ----------> [Payment API] ---> [Payment Gateway / Tokenization]
                                     │
                                 (encrypted)
                                     ↓
                              [Payment Processor]
```

**Notes about protection points**

* Transport: TLS between app ↔ backend (certificate + PKI).
* At rest: AES for stored sensitive data (payment tokens, PII); SHA-256 for password hashing (with salt + stretching).
* DB: SQL server (ensure parameterized queries, least privilege DB accounts).

---

## IV. Threat analysis (Stage IV)

### Internal threats

1. **Malicious or negligent employees** (devops, support) exposing DB credentials or misconfiguring backups — leading to internal data leaks.
2. **Compromised internal logging/monitoring systems** allowing attackers to erase traces or exfiltrate sensitive logs.

### External threats

1. **Payment fraud / payment processor compromise** — attackers intercept or tamper with payment flows.
2. **Account takeover (ATO)** via credential stuffing, weak password storage, or broken authentication flows.

---

## V. Vulnerability analysis (Stage V)

List of plausible exploitable vulnerabilities:

1. **Weak cryptography or improper key management**

   * Examples: RSA used incorrectly (no padding), AES keys hardcoded in config, PKI certificates mismanaged.
   * Impact: Decrypted payment/PII, impersonation, replay.

2. **SQL injection and insecure database access controls**

   * Examples: Unparameterized queries in search or listing endpoints; DB account with excessive privileges; backups stored in unencrypted buckets.
   * Impact: Full data exfiltration, data tampering, privilege escalation.

(Other possible vulnerabilities: Insecure direct object references (IDOR) for listings, insecure mobile storage of tokens, missing rate limiting on auth endpoints.)

---

## VI. Attack modeling — sample attack tree (Stage VI)

```
Goal: Exfiltrate user payment & PII
├─ A. Compromise backend
│   ├─ A1. SQL injection -> dump user table
│   └─ A2. Stolen DB credentials via dev laptop
├─ B. Break payment encryption
│   ├─ B1. Obtain AES key (hardcoded)
│   └─ B2. Break RSA key exchange (misconfigured PKI)
├─ C. Compromise users
│   ├─ C1. Phish support to get backup links
│   └─ C2. Credential stuffing -> access accounts -> purchase history
└─ D. Intercept network traffic
    ├─ D1. Man-in-the-Middle (no strict TLS pinning)
    └─ D2. Compromised CDN / reverse proxy injecting scripts
```

**Example attack path:** A → A1: attacker finds SQLi in search endpoint → extracts users + hashed passwords → performs offline cracking (if weak hashing) → uses credentials to access accounts and payment instruments.

---

## VII. Risk analysis & recommended controls (Stage VII)

Below are **4 prioritized security controls** with short rationale for reducing the specific risks above:

1. **Secure cryptography & key management (HSM / KMS + rotation)**

   * Use a managed Key Management Service (or HSM) for AES keys and RSA private keys. Enforce automated rotation, access auditing, and never store keys in code or plain config. Prevents exfiltration of cleartext payment data.

2. **Strong authentication & account protections**

   * Use salted & iterated password hashing (e.g., Argon2/BCrypt with unique salt), enforce MFA for high-risk actions, implement rate-limiting and monitoring for credential stuffing. Reduces ATO risk.

3. **Secure coding + DB access controls**

   * Enforce parameterized queries / ORM with prepared statements, least-privilege DB accounts, encrypted backups, regular SAST/DAST scanning, and fix OWASP Top 10 issues (esp. SQLi, IDOR). Limits attack surface for data theft.

4. **End-to-end TLS + mobile security hardening**

   * Strict TLS (minimum TLS 1.2/1.3), certificate pinning in app, secure cookies, CSP for admin web UI, and secure mobile storage (use platform keystore). Combined with WAF and monitoring, this prevents MitM and injection via CDN/proxy.

---

## Additional mitigations & operational controls (short list)

* **Payment tokenization**: do not store raw card data; use PCI-compliant processors and tokens.
* **Logging & SIEM**: centralized immutable logs, alerting for anomalous behavior, and retention policies.
* **Periodic threat modeling & red-team drills**: keep the attack tree and DFD current as features change.
* **Least privilege for internal users** and MFA for all admin/devops consoles.

---
