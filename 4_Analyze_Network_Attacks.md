# **Cybersecurity Incident Report**

## **Section 1: Identify the type of attack that may have caused this network interruption**

One potential explanation for the website's connection timeout error message is:
A **TCP SYN flood attack**, which is a type of **Denial-of-Service (DoS)** attack that targets the server’s ability to handle connection requests.

The logs show that:

* The source IP address `203.0.113.0` sent a **large volume of TCP SYN packets** to the destination IP `192.0.2.1` (the company’s web server) on port 443.
* These SYN packets did **not complete the TCP three-way handshake**, as no ACK responses were received from the attacker’s side.
* The server continued to send SYN-ACK responses, eventually filling its connection queue with **half-open connections**.
* After this, the server began returning **“destination port unreachable”** and **504 Gateway Timeout** errors, indicating it was overwhelmed and unable to accept new connections.

This event could be:
A **TCP SYN flood DoS attack**, where the attacker floods the server with incomplete connection requests to exhaust system resources, causing legitimate users to experience connection failures and timeouts.

---

## **Section 2: Explain how the attack is causing the website to malfunction**

When website visitors try to establish a connection with the web server, a **three-way handshake** occurs using the **TCP protocol**.
The three steps of the handshake are:

1. **SYN (Synchronize):** The client sends a TCP SYN packet to the server to request a new connection.
2. **SYN-ACK (Synchronize-Acknowledge):** The server responds with a SYN-ACK packet, acknowledging the client’s request and offering to establish a connection.
3. **ACK (Acknowledge):** The client sends back an ACK packet, confirming the connection. At this point, communication between client and server begins.

---

**Explain what happens when a malicious actor sends a large number of SYN packets all at once:**
When an attacker sends thousands of SYN packets simultaneously — often with **spoofed IP addresses** — the server replies with SYN-ACK packets and waits for the final ACK that never arrives. Each pending (half-open) connection uses up server memory and processing power. Eventually, the server’s connection table becomes full, meaning it cannot handle new, legitimate requests.

---

**Explain what the logs indicate and how that affects the server:**
The logs indicate that the web server was receiving **continuous SYN packets** from a single or multiple sources without corresponding ACKs. As a result, the server’s resources became exhausted while waiting for handshake completions that never occurred. This caused **legitimate users to be denied service**, leading to connection timeouts and error messages such as “destination port unreachable.”

This network interruption occurred because the server was effectively **overloaded and unresponsive** due to the SYN flood, making the company website unavailable to both customers and employees.

