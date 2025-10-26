# Parking lot USB exercise

## Contents

The USB contains a mix of personal photos and family documents alongside work files such as a new-hire letter and employee shift schedules. Several documents likely include personally identifiable information (names, roles, contact details) and operational data, so storing personal and business files together increases exposure and risk.

## Attacker mindset

An attacker could use PII from Jorge’s files to craft targeted phishing or social-engineering attacks against him, his colleagues, or relatives, increasing the chance of credential theft. Work documents like schedules or HR letters could reveal internal processes and personnel information that an adversary could exploit to gain unauthorized access or impersonate staff.

## Risk analysis

USBs can harbor malware such as autorun trojans, ransomware, or firmware-level implants that execute when mounted; if another employee opened the drive on a non-isolated machine, the network could be compromised and data exfiltrated. Sensitive PII and HR documents on the device could enable identity theft or targeted attacks. Mitigations include strict USB usage policies, endpoint protection with device control, employee training on baiting, and routine scanning of found media in isolated virtual environments.
