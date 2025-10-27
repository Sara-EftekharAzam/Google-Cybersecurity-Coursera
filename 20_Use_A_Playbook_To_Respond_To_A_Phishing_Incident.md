# Ticket

| ID     | Alert Message                                             | Severity | Details                                                                             | Ticket Status |
| ------ | --------------------------------------------------------- | -------- | ----------------------------------------------------------------------------------- | ------------- |
| A-2703 | SERVER-MAIL Phishing attempt possible download of malware | Medium   | The user may have opened a malicious email and opened attachments or clicked links. | **Escalated** |

---

## Ticket Comments

The alert detected that an employee received a phishing email containing a malicious attachment. The sender’s email address, **“76tguyhh6tgftrt7tg.su”**, does not match the sender’s displayed name, **“Def Communications,”** or the name mentioned in the message body, **“Clyde West.”** The email contains **grammatical errors** and a **password-protected executable file** attachment named **“bfsvc.exe.”**

After checking the file hash (**54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b**) in VirusTotal, the file has been **verified as malicious**. Given the **medium alert severity** and confirmed malicious activity, this incident has been **escalated to a level-two SOC analyst** for containment and remediation.

**Reasons for escalation:**

1. The file hash is confirmed to be malicious.
2. The sender’s address and display name are inconsistent, indicating phishing.
3. The email contains poor grammar and a suspicious executable attachment.

---

## Additional Information

**Known malicious file hash:**
`54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`

**Email:**
From: Def Communications `<76tguyhh6tgftrt7tg.su>` `<114.114.114.114>`
Sent: Wednesday, July 20, 2022 09:30:14 AM
To: `<hr@inergy.com>` `<176.157.125.93>`
Subject: Re: Infrastructure Egnieer role

**Body:**

> Dear HR at Ingergy,
> I am writing for to express my interest in the engineer role posted from the website.
> There is attached my resume and cover letter. For privacy, the file is password protected. Use the password **paradise10789** to open.
> Thank you,
> *Clyde West*

**Attachment:**
`filename="bfsvc.exe"`

---
