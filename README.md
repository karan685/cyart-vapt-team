# cyart-vapt-team

Workflow Steps (extract from README.md)
Reconnaissance

Run nmap -sV -p- 192.168.150.129 → identify open ports.

Use Maltego transforms against the IP range.

Query Shodan for historical data.

Vulnerability Scanning

Launch OpenVAS scan against target → generate report.

Perform Nikto web scan: nikto -h http://192.168.150.129.

Record CVSS scores, prioritise critical items.

Exploitation

Exploit vsftpd backdoor with Metasploit.

Brute‑force Tomcat manager (default credentials).

Use sqlmap against DVWA to extract database.

Post‑Exploitation

Escalate to root using chkrootkit exploit.

Dump /etc/shadow and compute SHA256.

Capture screenshots of Meterpreter shell.

Reporting

Compile findings into PTES format (Google Docs → PDF).

Write non‑technical briefing.

Email developers with PoC and remediation.

