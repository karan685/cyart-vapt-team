# Cybersecurity Advanced Labs – Complete Workflow Documentation

## Overview

This repository contains workflows, procedures, logging formats, reporting requirements, and remediation guidance for advanced cybersecurity practical labs. The labs simulate real-world penetration testing, exploitation, API security testing, privilege escalation, network attacks, mobile application testing, and a complete VAPT engagement.

---

# Tools Used

* Kali Linux
* Metasploit Framework
* Burp Suite
* OpenVAS / Greenbone
* Python
* Ghidra
* sqlmap
* LinPEAS
* PowerSploit
* Responder
* Ettercap
* Wireshark
* MobSF
* Frida
* Drozer
* Google Docs

---

# Folder Structure

```text
Cybersecurity-Labs/
│
├── 01-Advanced-Exploitation-Lab/
├── 02-API-Security-Testing-Lab/
├── 03-Privilege-Escalation-Lab/
├── 04-Network-Protocol-Attacks/
├── 05-Mobile-Application-Testing/
└── 06-Capstone-VAPT-Engagement/
```

---

# 1. Advanced Exploitation Lab

## Objective

Simulate a multi-stage exploitation attack using Metasploit, Python PoCs, and Ghidra.

## Workflow

### Step 1 – Environment Setup

* Start Kali Linux
* Deploy VulnHub VM (Mr. Robot)
* Verify connectivity using ping

### Step 2 – Reconnaissance

* Perform Nmap scan
* Identify WordPress version and plugins
* Enumerate exposed services

### Step 3 – Exploit Chain

* Launch Metasploit Framework
* Search WordPress exploit modules
* Configure exploit settings
* Gain Meterpreter session

### Exploit Log

| Exploit ID | Description      | Target IP     | Status  | Payload     |
| ---------- | ---------------- | ------------- | ------- | ----------- |
| 007        | XSS to RCE Chain | 192.168.1.100 | Success | Meterpreter |

### Step 4 – Custom PoC Development

* Download Python exploit from Exploit-DB
* Modify offsets and payload
* Execute against test target

### PoC Summary

A Python proof-of-concept exploit was modified to trigger a controlled buffer overflow vulnerability. Payload execution and memory offsets were customized to achieve successful remote code execution in a simulated environment.

### Step 5 – ASLR Bypass using ROP

* Analyze binary using Ghidra
* Identify ROP gadgets
* Build ROP chain
* Execute exploit

### ROP Summary

A Return-Oriented Programming chain was developed to bypass ASLR protections in a vulnerable binary. Existing executable code fragments were chained together to redirect program execution and achieve arbitrary code execution.

### Reporting Requirements

Create a Google Docs report:

* Title: Critical WordPress Exploit Chain
* Findings: CVE-2023-12345
* Host: 192.168.1.100
* Remediation:

  * Update vulnerable plugins
  * Enable WAF
  * Restrict administrative access

---

# 2. API Security Testing Lab

## Objective

Assess APIs for OWASP API Top 10 vulnerabilities using Burp Suite, Postman, and sqlmap.

## Workflow

### Step 1 – Setup

* Configure Burp Suite proxy
* Start DVWA/API environment
* Import API collections into Postman

### Step 2 – API Enumeration

* Identify API endpoints
* Analyze request methods
* Map authentication mechanisms

### Step 3 – Vulnerability Testing

Perform:

* BOLA testing
* GraphQL injection testing
* SQL injection testing
* Authentication bypass testing

### API Test Log

| Test ID | Vulnerability     | Severity | Target Endpoint |
| ------- | ----------------- | -------- | --------------- |
| 008     | BOLA              | Critical | /api/users      |
| 009     | GraphQL Injection | High     | /graphql        |

### Step 4 – Manual Testing

* Capture API requests using Burp
* Modify authentication tokens
* Replay requests
* Validate unauthorized access

### Step 5 – sqlmap Testing

* Export request from Burp Suite
* Execute sqlmap against vulnerable parameters
* Validate database injection

### Checklist

* Enumerate API endpoints
* Test for BOLA
* Fuzz GraphQL queries
* Test authentication and authorization
* Perform SQL injection testing

### API Test Summary

The assessment identified critical authorization and input validation weaknesses in exposed API endpoints. Improper access controls and insufficient input sanitization allowed unauthorized access and demonstrated risks including sensitive data exposure and backend compromise.

---

# 3. Privilege Escalation and Persistence Lab

## Objective

Identify privilege escalation vectors and establish persistence mechanisms.

## Workflow

### Step 1 – Enumeration

* Upload LinPEAS
* Execute enumeration scripts
* Identify SUID binaries and kernel vulnerabilities

### Escalation Log

| Task ID | Technique    | Target IP     | Status  | Outcome    |
| ------- | ------------ | ------------- | ------- | ---------- |
| 010     | SUID Exploit | 192.168.1.150 | Success | Root Shell |

### Step 2 – Privilege Escalation

* Exploit vulnerable SUID binaries
* Obtain elevated privileges
* Verify root access

### Step 3 – Persistence

* Configure cron job persistence
* Add reverse shell payload

### Persistence Summary

Persistence was established using a cron job configured to execute a reverse shell payload periodically. This allowed continued access after system reboot and demonstrated attacker persistence techniques commonly used during post-exploitation phases.

### Checklist

* Run LinPEAS
* Identify kernel vulnerabilities
* Exploit SUID binaries
* Establish persistence
* Document findings

---

# 4. Network Protocol Attacks Lab

## Objective

Perform MitM and SMB relay attacks using Responder, Ettercap, and Wireshark.

## Workflow

### Step 1 – Setup

* Start Responder
* Configure attacker interface
* Launch Wireshark packet capture

### SMB Relay Log

| Attack ID | Technique | Target IP     | Status  | Outcome   |
| --------- | --------- | ------------- | ------- | --------- |
| 015       | SMB Relay | 192.168.1.200 | Success | NTLM Hash |

### Step 2 – SMB Relay Attack

* Capture NTLM authentication
* Relay authentication requests
* Validate hash capture

### Step 3 – ARP Spoofing

* Configure Ettercap
* Enable ARP poisoning
* Intercept victim traffic

### Step 4 – Traffic Analysis

* Analyze SMB traffic
* Inspect intercepted packets
* Review DNS spoofing activity

### MitM Summary

ARP spoofing redirected victim traffic through the attacker machine, enabling credential interception and traffic analysis. SMB relay attacks demonstrated the risk of insecure protocol configurations and lack of SMB signing protections.

### Checklist

* Capture NTLM hashes
* Perform DNS spoofing
* Analyze traffic using Wireshark
* Save packet captures

---

# 5. Mobile Application Testing Lab

## Objective

Perform static and dynamic testing of Android applications using MobSF, Frida, and Drozer.

## Workflow

### Step 1 – Static Analysis

* Upload APK to MobSF
* Review permissions
* Identify insecure storage

### Vulnerability Log

| Test ID | Vulnerability    | Severity | Target App |
| ------- | ---------------- | -------- | ---------- |
| 016     | Insecure Storage | High     | test.apk   |

### Step 2 – Dynamic Testing

* Start Frida server
* Hook authentication functions
* Monitor runtime behavior

### Step 3 – IPC Testing

* Use Drozer for component enumeration
* Test exported activities and services
* Analyze IPC exposure

### Dynamic Testing Summary

Frida was used to hook authentication functions and bypass client-side security checks. Dynamic testing revealed insecure runtime protections and demonstrated weaknesses that could allow authentication bypass and sensitive information exposure.

### Checklist

* Run MobSF
* Hook functions using Frida
* Test IPC using Drozer
* Analyze app permissions

---

# 6. Capstone Project – Full VAPT Engagement

## Objective

Conduct a full penetration testing engagement following PTES methodology.

## Workflow

### Step 1 – Reconnaissance

* Run Nmap scans
* Identify services and APIs
* Enumerate exposed applications

### Step 2 – Vulnerability Scanning

* Run OpenVAS scan
* Export findings
* Prioritize vulnerabilities

### Exploitation Log

| Timestamp           | Target IP     | Vulnerability | PTES Phase   |
| ------------------- | ------------- | ------------- | ------------ |
| 2025-08-30 15:00:00 | 192.168.1.200 | VSFTPD RCE    | Exploitation |

### Step 3 – Exploitation

* Launch Metasploit
* Use exploit/unix/ftp/vsftpd_234_backdoor
* Gain shell access
* Validate compromise

### Step 4 – API Testing

* Use Burp Suite
* Test authentication controls
* Validate input handling

### Step 5 – Remediation

Implement:

* Security patches
* Input validation
* Least privilege access
* WAF protections

### Step 6 – Validation

* Rescan using OpenVAS
* Confirm remediation effectiveness

---

# PTES Report Structure

## Executive Summary

Summarize objectives, vulnerabilities discovered, exploitation impact, and business risks.

## Attack Timeline

Document:

* Reconnaissance
* Enumeration
* Exploitation
* Post-exploitation
* Remediation

## Remediation Plan

Include:

* Patch management
* Input validation
* Access control hardening
* Continuous monitoring

---

# Stakeholder Briefing

Prepare a 150-word non-technical summary including:

* Risks identified
* Business impact
* Recommended mitigation steps
* Overall security posture

---

# General Recommendations

* Keep systems updated
* Disable unnecessary services
* Enforce least privilege
* Implement secure coding practices
* Conduct regular vulnerability assessments
* Enable logging and monitoring
* Use multi-factor authentication
* Perform periodic penetration testing

---

# Disclaimer

This project is intended strictly for educational and authorized security testing purposes. All testing must be conducted only on systems owned by you or systems where explicit written permission has been granted.
