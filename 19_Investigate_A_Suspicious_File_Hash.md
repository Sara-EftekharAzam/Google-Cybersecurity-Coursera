**Malicious?** Yes — Based on public intelligence the file belongs to the Flagpro malware family; multiple vendor detections and associated infrastructure confirm maliciousness.

**Pyramid of Pain — Selected IoCs**

- **Hash values**:  
  • 54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b  
  • ba27ae12e6f3c2c87fd2478072dfa2747d368a507c69cd90b653c9e707254a1d  

- **IP addresses**:  
  • 139.162.87.180  

- **Domain names**:  
  • misecure[.]com  

- **Network/host artifacts**:  
  • Executable dropped into startup folder for persistence (flagpro dropper).  

- **Tools**:  
  • Flagpro malware (used by BlackTech)  
  • Use of Windows COM/Internet Explorer for download & execution, built-in APIs.  

- **Tactics, Techniques & Procedures (TTPs)**:  
  • Spearphishing Attachment (T1566.001)  
  • User Execution: Malicious File (T1204.002)  
  • Boot or Logon Initialization Scripts: Startup Items (T1037.005)  
  • Data Encoding: Standard Encoding (T1132.001)  
  • Exfiltration Over C2 Channel (T1041)  
