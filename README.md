# active-directory-pentest-lab
Simulated Active Directory compromise using credential attacks, lateral movement, and persistance techniques
🛡️ Active Directory Penetration Testing Lab

📌 Overview

This project demonstrates a full attack lifecycle on an Active Directory environment, including initial access, credential dumping, lateral movement, and persistence.

The objective was to simulate a real-world internal attack scenario and understand how weak authentication mechanisms can lead to domain compromise.

---

🧱 Lab Setup

- Attacker: Kali Linux
- Domain Controller: 192.168.56.10
- Windows Client: 192.168.56.20
- Domain: corp.local

---

⚔️ Attack Chain

1. Initial Access

- SMB enumeration
- NTLM hash authentication (Pass-the-Hash)

---

2. Privilege Escalation

- Administrator-level access confirmed

---

3. Credential Dumping

- SAM hashes extracted
- LSA secrets (Kerberos keys) obtained
- DPAPI keys retrieved

---

4. Lateral Movement

- Subnet scanning using valid credentials
- Access to multiple hosts in network

---

5. Post Exploitation

- User enumeration
- Logged-on user discovery
- Share enumeration

---

6. Persistence

- Created backdoor admin account

---

📸 Screenshots

Step| Description
Initial Access| screenshots/hash_auth.png
Credential Dumping| screenshots/credential_dump.png
Lateral Movement| screenshots/lateral_movement.png
Persistence| screenshots/persistence.png

---

🔥 Key Learnings

- NTLM authentication is highly exploitable
- Credential reuse enables lateral movement
- LSASS memory is a critical target
- Kerberos-based attacks provide deeper access

---

⚠️ Impact

An attacker can achieve:

- Domain-wide administrative control
- Credential theft
- Persistent access

---

🛡️ Mitigations

- Disable NTLM where possible
- Enable Credential Guard
- Monitor LSASS access
- Enforce least privilege

---

📄 Full Report

Detailed report available in "/report" directory.

---
