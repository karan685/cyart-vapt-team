# cyart-vapt-team

Workflow Steps
1.	Reconnaissance
o	Run nmap -sV -p- 192.168.150.129 → identify open ports.
o	Use Maltego transforms against the IP range.
o	Query Shodan for historical data.
2.	Vulnerability Scanning
o	Launch OpenVAS scan against target → generate report.
o	Perform Nikto web scan: nikto -h http://192.168.150.129.
o	Record CVSS scores, prioritise critical items.
3.	Exploitation
o	Exploit vsftpd backdoor with Metasploit.
o	Brute force Tomcat manager (default credentials).
o	Use sqlmap against DVWA to extract database.
4.	Post Exploitation
o	Escalate to root using chkrootkit exploit.
o	Dump /etc/shadow and compute SHA256.
o	Capture screenshots of Meterpreter shell.
5.	Reporting
o	Compile findings into PTES format (Google Docs → PDF).
o	Write non technical briefing.
o	Email developers with PoC and remediation.


