🛡️ Active Directory Attack Lab: Red Team Simulation

«⚠️ Disclaimer: This project was conducted in a strictly controlled, isolated, and authorized laboratory environment. The techniques documented here are for educational purposes, defensive analysis, and security research only. Do not attempt these techniques on systems you do not own or have explicit permission to test.»

---

📌 Overview

This project demonstrates a complete Active Directory compromise within a custom-built lab environment. The attack simulates a real-world internal threat scenario using credential-based techniques such as Pass-the-Hash (PtH), credential dumping, and lateral movement to achieve full domain compromise.

---

🧠 Attack Narrative

The attack demonstrates how a single compromised credential can lead to full domain compromise. By exploiting NTLM-based authentication weaknesses and credential reuse across systems, the attacker escalates privileges, extracts sensitive authentication material, and moves laterally across the network.

The lack of credential isolation and reliance on reusable authentication mechanisms enabled domain-wide compromise without exploiting software vulnerabilities.

---

🚨 Key Outcomes

- ✔ Domain Administrator access achieved
- ✔ NTLM hashes, SAM, LSA secrets, and Kerberos keys extracted
- ✔ Lateral movement across multiple domain-joined systems
- ✔ Persistent administrative backdoor established

---

🧱 Lab Architecture

Role| System| IP Address| Description
Attacker| Kali Linux| 192.168.56.102| Attack machine
Domain Controller| DC01| 192.168.56.10| Active Directory server
Client Machine| WIN10| 192.168.56.20| Domain-joined endpoint
Domain| corp.local| -| Target environment

---

🧰 Tools & Purpose

Tool| Purpose
NetExec| SMB enumeration, authentication, lateral movement
Impacket| Credential dumping and remote execution
Mimikatz| Credential extraction from memory

---

⚔️ Attack Chain

1. Initial Access

- Identified SMB services on target systems
- Authenticated using NTLM hash (Pass-the-Hash)

---

2. Privilege Escalation

- Achieved administrative access on compromised systems
- Verified privileges via remote command execution

---

3. Credential Dumping

- Extracted local account hashes from SAM database
- Dumped LSA secrets including Kerberos encryption keys
- Retrieved DPAPI keys for potential credential decryption

---

4. Lateral Movement

- Performed subnet-wide authentication using valid credentials
- Reused administrative access across multiple hosts
- Executed commands remotely to expand control

---

5. Post-Exploitation

- Enumerated users and system configuration
- Identified logged-in users (credential targets)
- Analyzed available network shares

---

6. Persistence

- Established persistence by creating a secondary administrative account
- Ensured continued access even after credential changes or reboot

---

📸 Proof of Exploitation

✔ Pass-the-Hash Authentication

"Hash Auth" (screenshots/hash_auth.png)

✔ Credential Dumping

"Credential Dump" (screenshots/credential_dump.png)

✔ Lateral Movement

"Lateral Movement" (screenshots/lateral_movement.png)

✔ Persistence

"Persistence" (screenshots/persistence.png)

---

🧠 Skills Demonstrated

- Active Directory Enumeration
- SMB Exploitation
- Pass-the-Hash Attack
- Credential Dumping (SAM, LSA, DPAPI)
- Lateral Movement Techniques
- Persistence Mechanisms
- Windows Authentication Internals (NTLM & Kerberos)

---

⚠️ Security Impact & Risk

This attack chain demonstrates a worst-case scenario where an attacker achieves full domain compromise. With Domain Administrator privileges, the attacker can:

- Control all systems and user accounts within the domain
- Access sensitive organizational data and credentials
- Deploy malware or ransomware across the network
- Maintain persistent and stealthy access even after remediation attempts

This results in a complete loss of confidentiality, integrity, and availability.

---

🔍 Detection Opportunities

- Unusual NTLM authentication attempts across multiple hosts
- Repeated administrative access from a single source
- LSASS memory access or dumping activity
- Creation of new privileged user accounts
- Lateral movement patterns using SMB

---

🛡️ Mitigation Strategies

- Disable or restrict NTLM authentication
- Enable Credential Guard to protect LSASS
- Enforce least privilege access (e.g., LAPS)
- Monitor authentication anomalies and lateral movement
- Implement network segmentation
- Enforce strong password and rotation policies

---

🎯 Key Takeaway

This project highlights how credential-based attacks remain one of the most effective methods for compromising Active Directory environments. Even without exploiting software vulnerabilities, weak authentication practices and credential reuse can lead to complete domain takeover.

Understanding these attack paths is critical for both offensive security professionals and defenders.

---

📄 Documentation

A detailed penetration testing report is available in the ""/report"" (./report) directory.

---