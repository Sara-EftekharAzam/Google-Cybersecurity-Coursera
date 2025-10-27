# File Analysis

* **Artifact SHA256:** `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b`
* **Malicious?** **Yes** — The file is confirmed malicious based on public threat-intel.

  * It is documented as part of the Flagpro malware family used by the BlackTech (aka “Palmerworm”) espionage group. ([Infocon][1])
  * The sample’s submission to sandbox/analysis services marks it as malicious with associated C2 infrastructure and multiple vendor detections. ([Joe Sandbox][2])
  * Given the scenario (password-protected email attachment, follow-up execution of payloads, creation of unauthorized executables) and the contextual match with known Flagpro TTPs (spear-phishing with password-protected macro file) the file aligns with confirmed malicious behaviour. ([Trellix Thrive][3])

**Reasoning summary:** The file hash matches a known malicious payload (Flagpro) that is actively used in targeted attacks; the delivery vector (password-protected spreadsheet attachment) and follow-on behaviour align with research on the threat actor; hence the verdict is malicious.

---

# Pyramid of Pain — Indicators of Compromise (IoCs)

Here are three distinct IoCs associated with the file and mapped into the relevant Pyramid-of-Pain categories:

| Pyramid Level                   | Indicator Type        | Indicator                                                          | Notes / Source                                                                                            |
| ------------------------------- | --------------------- | ------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------- |
| Hash Values (easy for defence)  | File hash             | `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b` | This is the original artifact hash.                                                                       |
|                                 | File hash (alternate) | `ba27ae12e6f3c2c87fd2478072dfa2747d368a507c69cd90b653c9e707254a1d` | Alternate variant of Flagpro dropper seen in the same campaign. ([CISO MAG | Cyber Security Magazine][4]) |
| Domain Names (moderate pain)    | Malicious domain      | `misecure[.]com`                                                   | Known C2 / malicious domain used by this campaign. ([CISO MAG | Cyber Security Magazine][4])              |
| IP Addresses (moderate-to-hard) | Malicious IP address  | `139.162.87.180`                                                   | One of the infrastructure IP addresses linked to the malware’s C2. ([orkl.eu][5])                         |

## Additional mapping to full six categories (for completeness):

* **Hash values**: as above, both the primary SHA256 and an alternate SHA256 variant.
* **IP addresses**: 139.162.87.180 (C2 server)
* **Domain names**: misecure.com (malicious domain)
* **Network/Host artifacts**: The malware creates an executable in the startup folder (persistent via startup items). Example: Executable dropped into startup directory. ([Trellix Thrive][3])
* **Tools**: The malware uses the tool “Flagpro” itself, or uses built-in Windows APIs and modules (e.g., via COM or Internet Explorer) as part of its toolset. ([Infocon][1])
* **Tactics, Techniques & Procedures (TTPs)**:

  * T1566.001 Spearphishing Attachment (delivery of password-protected archive) ([Picus Security][6])
  * T1204.002 User Execution: Malicious File (user opens the attachment) ([Picus Security][6])
  * T1037.005 Boot or Logon Initialization Scripts: Startup Items for persistence. ([Trellix Thrive][3])
  * T1132.001 Data Encoding: Standard Encoding (Base64) for communications. ([Picus Security][6])
  * T1041 Exfiltration Over C2 Channel (data sent back to C2 server) ([Picus Security][6])


[1]: https://infocon.org/mirrors/vx%20underground%20-%202025%20June/Papers/Malware%20Defense/Malware%20Analysis/2021/2021-12-28%20-%20Flagpro-%20The%20new%20malware%20used%20by%20BlackTech.pdf?utm_source=chatgpt.com "Flagpro: The new malware used by BlackTech"
[2]: https://www.joesandbox.com/analysis/914055?utm_source=chatgpt.com "Automated Malware Analysis - Joe Sandbox Cloud Basic"
[3]: https://thrive.trellix.com/s/article/KB95754?language=en_US&utm_source=chatgpt.com "Trellix Insights: Flagpro malware"
[4]: https://cisomag.com/flagpro-malware/amp/?utm_source=chatgpt.com "Chinese Linked Cyberespionage APT Spreads Flagpro Malware"
[5]: https://orkl.eu/libraryEntry/268560dd-8910-4a56-8082-e84da65ffaa3?utm_source=chatgpt.com "ORKL"
[6]: https://www.picussecurity.com/resource/blog/flagpro-malware-of-blacktech-group?utm_source=chatgpt.com "Picus Threat Library Is Updated for Flagpro Malware of ..."
