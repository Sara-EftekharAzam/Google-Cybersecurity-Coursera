# Cybersecurity Incident Report:  
## Network Traffic Analysis

### Part 1: Provide a summary of the problem found in the DNS and ICMP traffic log.

**The UDP protocol reveals that:**  
The UDP packets sent from the client’s browser to the DNS server (port 53) were not successfully delivered, indicating an issue with DNS query communication.

**This is based on the results of the network analysis, which show that the ICMP echo reply returned the error message:**  
"udp port 53 unreachable," indicating that the DNS server was not accepting UDP requests on port 53.

**The port noted in the error message is used for:**  
Port 53 is the standard port for DNS services, which resolve domain names (like www.yummyrecipesforme.com) into IP addresses.

**The most likely issue is:**  
The DNS server at 203.0.113.2 is not responding to UDP queries on port 53, causing clients to receive ICMP "destination port unreachable" errors, preventing access to the website.

---

### Part 2: Explain your analysis of the data and provide at least one cause of the incident.

**Time incident occurred:**  
1:24 PM (13:24:32) on the day the incident was reported.

**Explain how the IT team became aware of the incident:**  
Several users of client companies reported that they could not access the website www.yummyrecipesforme.com, receiving the error “destination port unreachable.”

**Explain the actions taken by the IT department to investigate the incident:**  
- Attempted to access the website and reproduced the error.  
- Captured network traffic using tcpdump to analyze DNS queries and responses.  
- Observed UDP packets sent to the DNS server and ICMP error responses indicating the port was unreachable.  

**Note key findings of the IT department's investigation (i.e., details related to the port affected, DNS server, etc.):**  
- DNS queries from clients were sent via UDP to port 53 on the DNS server 203.0.113.2.  
- The DNS server responded with ICMP messages stating "udp port 53 unreachable," indicating no service was listening on the DNS port.  
- Multiple attempts confirmed the persistent nature of the issue.  

**Note a likely cause of the incident:**  
The DNS server for yummyrecipesforme.com was either down, misconfigured, or not running a service on UDP port 53, resulting in DNS resolution failures and ICMP "destination port unreachable" errors for clients.
