# **Incident Report Analysis**

## **Summary**

A **Distributed Denial of Service (DDoS)** attack targeted the company’s internal network, causing a **two-hour service outage**. The attack was initiated through a flood of **ICMP (ping) packets**, overwhelming the network and making it impossible for legitimate traffic to access resources.

The root cause was an **unconfigured firewall** that allowed unrestricted ICMP packets from external sources. The incident management team mitigated the attack by **blocking incoming ICMP packets**, **taking non-critical services offline**, and restoring critical network services.

Subsequent investigation revealed the attacker exploited the firewall misconfiguration, enabling massive ICMP traffic to disrupt network performance. Immediate corrective measures were applied, including **firewall rule updates**, **source IP verification**, **network monitoring**, and **intrusion detection and prevention systems (IDS/IPS)**.

---

## **Identify**

* **Type of Attack:** Distributed Denial of Service (DDoS) using ICMP flood
* **Cause:** Firewall misconfiguration that allowed unrestricted incoming ICMP traffic
* **Affected Systems:** Internal servers, routers, switches, and all connected client systems relying on internal services
* **Business Impact:** Two-hour downtime; interruption of internal operations and external client communications
* **Vulnerability:** Lack of rate-limiting and source verification in firewall configuration
* **People Affected:** Network administrators, IT staff, and clients relying on the company’s hosted services

**Key Risks Identified:**

* Unsecured perimeter defenses
* Lack of proactive firewall configuration management
* Insufficient continuous network monitoring

---

## **Protect**

* **Firewall Configuration:** Implement strict ICMP rate-limiting rules and disallow unnecessary external pings.
* **Access Control:** Restrict administrative access to firewall and network devices to authorized personnel only.
* **Security Awareness Training:** Educate IT staff on identifying and preventing DDoS attack patterns.
* **Data Security:** Ensure that no sensitive client data is transmitted or exposed through ICMP traffic.
* **Maintenance and Patch Management:** Regularly update and audit firewall and router firmware for vulnerabilities.
* **Protective Technology:** Maintain redundant firewalls and load balancers to absorb and distribute network traffic during peak or attack periods.

---

## **Detect**

* **Network Monitoring:** Deploy real-time monitoring tools (e.g., SolarWinds, Nagios, or PRTG) to analyze ICMP traffic volume.
* **Intrusion Detection System (IDS):** Utilize IDS/IPS to detect anomalies, including abnormal ICMP packet rates.
* **SIEM Implementation:** Use a Security Information and Event Management (SIEM) system such as Splunk or Azure Sentinel to aggregate logs and generate alerts on suspicious activity.
* **Continuous Monitoring:** Schedule 24/7 monitoring and anomaly detection to quickly identify traffic spikes or spoofed IP sources.
* **Detection Process:** Implement threshold-based alerts to flag when incoming ICMP traffic exceeds normal operational patterns.

---

## **Respond**

* **Response Planning:** Develop a formal **DDoS Response Procedure** detailing containment, escalation, and mitigation steps.
* **Containment:** Immediately block or throttle incoming ICMP packets from non-trusted or spoofed sources.
* **Communication:** Notify IT staff and key stakeholders immediately; update affected teams on containment progress.
* **Analysis:** Review firewall and network logs to determine attack origin, affected systems, and attack duration.
* **Mitigation:** Re-route legitimate traffic, apply blackhole routing for malicious IPs, and validate all firewall rules.
* **Improvements:** Conduct post-incident review and update playbooks to include ICMP flood scenarios.

---

## **Recover**

* **Recovery Planning:** Gradually restore non-critical network services after verifying traffic stability and no ongoing attack signs.
* **System Restoration:** Validate and re-enable all affected internal systems and ensure backups are intact.
* **Improvements:** Conduct a **lessons-learned session** to identify gaps in incident response and recovery processes.
* **Testing:** Perform penetration tests and simulated DDoS drills to ensure defenses are effective.
* **Communication:** Notify stakeholders, clients, and employees once network services are fully operational and secure.
* **Documentation:** Update disaster recovery and incident response documentation with newly learned best practices.

---

## **Reflections / Notes**

This incident emphasizes the importance of **proper firewall configuration**, **continuous monitoring**, and **proactive defense strategies**. Applying the **NIST CSF** ensured a structured approach to identifying, protecting, detecting, responding to, and recovering from cybersecurity incidents. Regular audits, employee training, and continuous system updates are critical for maintaining network resilience and minimizing downtime in future attacks.

---
