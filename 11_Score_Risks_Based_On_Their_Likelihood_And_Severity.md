# **Risk Register**

## **Operational Environment**

The bank is located in a **coastal area with low crime rates**. It employs **100 on-premises staff and 20 remote workers**, handling data for **2,000 individual and 200 commercial accounts**. The bank’s reputation is tied to **local businesses and a professional sports team**, requiring high trust and reliability. Strict **financial regulations** demand daily liquidity compliance with **Federal Reserve** standards and strong **data protection** to secure customer funds.

---

| **Asset** | **Risk(s)**                   | **Description**                                                                          | **Likelihood (1–3)** | **Severity (1–3)** | **Priority (L × S)** |
| --------- | ----------------------------- | ---------------------------------------------------------------------------------------- | -------------------- | ------------------ | -------------------- |
| **Funds** | **Business email compromise** | An employee is tricked into sharing confidential banking or login information.           | 2                    | 3                  | **6**                |
| **Funds** | **Compromised user database** | Customer data is poorly encrypted, exposing sensitive account details.                   | 3                    | 3                  | **9**                |
| **Funds** | **Financial records leak**    | A database server containing backed-up data is publicly accessible.                      | 2                    | 3                  | **6**                |
| **Funds** | **Theft**                     | The bank’s safe is left unlocked, allowing unauthorized physical access.                 | 1                    | 2                  | **2**                |
| **Funds** | **Supply chain disruption**   | Delivery delays due to coastal storms or natural disasters interrupt cash replenishment. | 1                    | 2                  | **2**                |

---

## **Notes**

Security events are possible because the bank manages large volumes of sensitive financial data and customer records, handled by both on-premises and remote employees. **Human error and phishing** increase the risk of business email compromise, while **poor encryption and misconfigured backups** could expose customer and financial data. The **coastal environment** poses occasional natural risks that could disrupt physical supply chains or power availability, affecting banking operations and regulatory compliance.

---

### **Summary**

* **Highest priority risk:** Compromised user database (Score: 9)
* **Moderate priority risks:** Business email compromise and financial records leak (Score: 6 each)
* **Low priority risks:** Theft and supply chain disruption (Score: 2 each)

These results suggest the bank should **focus first on strengthening data encryption, access controls, and employee security awareness**, while **maintaining physical and environmental safeguards** to reduce lower-impact risks.
