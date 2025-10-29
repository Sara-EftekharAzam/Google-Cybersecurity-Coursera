# 🧾 **Incident Handler's Journal**

---

## **Date:** October 27, 2025

## **Entry:** 1

### **Description**

This entry documents a **ransomware attack** at a small U.S. healthcare clinic that resulted in complete system shutdown and loss of access to patient data. It summarizes incident details, initial findings, and root causes.
**NIST Phase:** *Detection and Analysis*

---

### **Tool(s) Used**

No cybersecurity tools were used during this initial reporting stage. The data was gathered from employee reports and the ransom note observed on infected computers.

---

### **The 5 W’s**

* **Who caused the incident?**
  A known ransomware group targeting healthcare and transport sectors was responsible for the attack.

* **What happened?**
  Employees received **phishing emails** with malicious attachments. Opening these files triggered ransomware that encrypted all patient data and displayed a ransom note.

* **When did the incident occur?**
  Tuesday morning at approximately **9:00 a.m.**

* **Where did the incident happen?**
  At a **small healthcare clinic in the United States**, affecting all systems on the internal network.

* **Why did the incident happen?**
  Insufficient **phishing awareness** training allowed employees to open a malicious email, leading to malware execution and ransomware infection.

---

### **Additional Notes**

* The incident disrupted patient care and halted operations.
* Data recovery depended on offsite backups.
* Staff awareness and network monitoring need improvement.
* The clinic must report the incident under **HIPAA** regulations.

---

### **Reflections/Notes**

This case emphasizes the importance of **employee cybersecurity training**, **data backup strategies**, and **incident response preparedness**. Investing in proactive defense and awareness could prevent similar breaches.

---

## **Date:** October 28, 2025

## **Entry:** 2

### **Description**

This entry documents the **use of Wireshark** to analyze captured network packets from a suspected phishing attempt. The goal was to identify suspicious traffic patterns and validate packet contents.
**NIST Phase:** *Detection and Analysis*

---

### **Tool(s) Used**

**Wireshark**

* Captured and filtered HTTP and SMTP traffic for packet inspection.
* Revealed that certain packets contained **encoded scripts** typical of phishing links.
* Helped confirm the **source IP address** of the malicious server.

---

### **The 5 W’s** *(applied to the analysis)*

* **Who:** Malicious sender using spoofed company email domain.
* **What:** Suspicious email link redirected to a phishing webpage.
* **When:** Detected during packet capture on October 28, 2025.
* **Where:** Within company network traffic logs.
* **Why:** Attempt to steal user credentials via fake login portal.

---

### **Additional Notes**

Wireshark provided critical packet-level insights that allowed us to **trace the phishing source** and understand payload delivery methods. It demonstrated how deep packet inspection supports rapid detection.

---

### **Reflections/Notes**

Wireshark proved to be an excellent **diagnostic tool** for real-time traffic monitoring and validation. I learned to use **filters and decoding tools** to locate key anomalies efficiently.

---

## **Date:** October 29, 2025

## **Entry:** 3

### **Description**

This entry documents an **incident investigation using VirusTotal** to analyze a **suspicious file hash** reported in a phishing case.
**NIST Phase:** *Detection and Analysis*

---

### **Tool(s) Used**

**VirusTotal**

* Uploaded file hash for verification.
* Detected multiple **antivirus engines** flagging the file as **malicious ransomware**.
* The file matched known samples of **LockBit ransomware** variants.

---

### **The 5 W’s**

* **Who:** Unknown threat actors distributing malicious email attachments.
* **What:** File hash confirmed as a known ransomware executable.
* **When:** Analysis conducted immediately after initial alert.
* **Where:** Through VirusTotal web interface.
* **Why:** Verification was needed to confirm the malware and inform next response steps.

---

### **Additional Notes**

The VirusTotal results validated the malicious nature of the file, enabling the team to **escalate containment** and **initiate eradication**. Sharing the hash with internal detection systems improved future threat prevention.

---

### **Reflections/Notes**

VirusTotal provided rapid confirmation and visibility into malware reputation. It reinforced how **hash intelligence** helps incident responders make faster, evidence-based decisions.

---

## **Date:** October 30, 2025

## **Entry:** 4

### **Description**

This entry describes the **use of Splunk** to search through unstructured log records from Suricata and identify network intrusions.
**NIST Phase:** *Containment, Eradication, and Recovery*

---

### **Tool(s) Used**

**Splunk**

* Queried Suricata logs to identify **unusual outbound connections**.
* Used `search` and `stats` commands to isolate events tied to known malicious IPs.
* Correlated multiple alerts to detect a **C2 (Command and Control)** communication pattern.

---

### **The 5 W’s**

* **Who:** Internal host 192.168.10.45 communicating with known C2 IP.
* **What:** Suspicious outbound traffic detected post-ransomware containment.
* **When:** Logs captured between **October 29–30, 2025**.
* **Where:** From Suricata intrusion detection logs stored in Splunk.
* **Why:** To validate whether lateral movement or exfiltration occurred after the initial ransomware attack.

---

### **Additional Notes**

Splunk’s analytics revealed patterns not visible in raw logs, assisting in verifying the **containment’s effectiveness**. It helped ensure that **no additional infections** persisted.

---

### **Reflections/Notes**

Splunk demonstrated the power of **centralized log analysis** and **search-based incident investigation**. Learning query syntax and correlation commands deepened my understanding of **SIEM operations**.

---

## 🧩 **Course Reflection Summary**

### **Were there any specific activities that were challenging for you? Why or why not?**

The most challenging activities involved analyzing raw packet data in Wireshark. Understanding each protocol layer and filtering relevant packets required practice and close attention to detail.

### **Has your understanding of incident detection and response changed since taking this course?**

Yes. I now understand how each phase of the NIST Incident Response Lifecycle works in practice and how documentation supports accountability, recovery, and organizational learning.

### **Was there a specific tool or concept that you enjoyed the most? Why?**

I enjoyed using **Splunk** because it combines powerful search capabilities with visual dashboards, helping me transform large, complex log data into actionable security insights.

rsion (for your cybersecurity portfolio submission)?
