# FUTURE_CS_03
# Incident response 

Incident Response Report – Denial-of-Service (DoS) Attack
Overview
This repository contains an incident response report documenting the analysis, mitigation, and prevention strategies for a simulated Denial-of-Service (DoS) attack on a web server hosted in an Oracle VM VirtualBox environment. The attack was executed using the Slowloris tool, and Wireshark was employed to capture and analyze network traffic.

Contents
Incident_Response_Report.pdf – Detailed documentation of the attack scenario, root cause analysis, mitigation steps, and recommendations.
Evidence Files (if applicable):
Before_Attack.png – Screenshot of the website before the attack.
Slowloris_Output.txt – Output logs from the Slowloris tool during the attack.
Wireshark_Capture.pcap – Network packet logs capturing attack patterns.
After_Attack.png – Screenshot showing website buffering post-attack.
Incident Details
Target: Web server running on port 80 (HTTP) inside Metasploitable 2.
Attack Type: Denial-of-Service (DoS) using Slowloris.
Threat Actor: Simulated attacker sending numerous incomplete HTTP GET requests.
Root Cause
The attack exploited the web server’s lack of timeout mechanisms for idle connections, allowing Slowloris to overwhelm the connection pool and degrade performance.

Mitigation Steps
Immediate Response:
Terminated the attacker's connection.
Restarted the web server to restore normal operations.
Temporary Countermeasures:
Blocked the attacker’s IP address using a firewall.
Enabled rate limiting to prevent similar attacks.
Network Hardening:
Implemented timeout settings for idle connections.
Deployed a Web Application Firewall (WAF) for attack detection.

Configured iptables to restrict excessive SYN requests:
iptables -A INPUT -p tcp --dport 80 --syn -m limit --limit 10/s --limit-burst 20 -j ACCEPT

Recommendations
Technical Measures
Enable rate limiting to restrict excessive connection requests.
Deploy a reverse proxy (e.g., Nginx) to filter malicious traffic.
Use load balancing to distribute traffic across multiple servers.
Continuously monitor network traffic with Wireshark, Splunk, or Kibana.
Administrative Measures
Establish a formal incident response plan.
Conduct regular security training for IT staff.
Perform periodic penetration testing to identify vulnerabilities.
Keep all software updated and patched to mitigate exploits.
Conclusion
This report highlights the risk of Slowloris DoS attacks and outlines mitigation steps to enhance server resilience. By implementing technical defenses and security best practices, organizations can minimize the risk of similar cyber threats.

