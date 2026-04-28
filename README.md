# -OWASP-Cryptographic-Failures---Cracking-MD5-Password-Hashes-Setup
This lab demonstrates how attackers exploit weak hashing using dictionary attacks.

**Concept**

Password hashing is meant to protect stored credentials. However, weak algorithms like MD5 are vulnerable to cracking.

This lab demonstrates how attackers exploit weak hashing using dictionary attacks.



**Lab Setup**
Target: Damn Vulnerable Web Application
Environment: Ubuntu (Apache, PHP, MySQL)
DVWA Security Level: Low
Attacker Machine: Kali Linux
Tools:
Hashcat
rockyou.txt


**Objective**

Extract password hashes via SQL Injection and crack them to reveal plaintext passwords.


**Exploitation Steps**
1. Extract Password Hashes

Navigate to DVWA SQL Injection module and input:
1' UNION SELECT user,password FROM users#

This dumps:

usernames
password hashes


2. Identify Hash Type
32-character hexadecimal string


3. Save Hashes
   Hashes.txt

5. Crack Hashes with Hashcat
   hashcat -m 0 -a 0 hashes.txt /usr/share/wordlists/rockyou.txt



**Impact**
Weak hashing allows attackers to recover passwords quickly
Compromised credentials can lead to:
Account takeover
Privilege escalation (e.g., admin access)
Data breaches


**Remediation**

To secure password storage:

Use strong hashing algorithms:
bcrypt
Argon2
Apply:
Unique salts per user
Slow hashing (cost factor)
Password complexity policies
