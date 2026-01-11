# Security Writeups

This repo stores personal notes/reports I take to document my process in learning cybersecurity related concepts.

## Notes and Reports

This is where I store a digitization of my written notes, restructured into readable reports.

### Industrial Control Systems (ICS)

- **[PERA Model](Notes_And_Reports/ICS/pera.md)** - This report explains how the Purdue Enterprise Reference Architecture (PERA) model works, then maps key vulnerabilities and mitigations at each layer. Additional models, real-life exploits, network access control, and IIoT communication protocols are discussed.

## Lab Reports

This is where I store smaller-scale security labs reports. If they don't require their own repo, they just go here.

### Exploits

#### Linux

- **[Shellshock](Lab_Writeups/Exploits/Linux/Shellshock.pdf)** - SeedLab's Shellshock lab, Vulnerable Bash version achieves RCE
- **[Set UID](Lab_Writeups/Exploits/Linux/Set_UID.pdf)** - Vulnerable C command execve(), SetUID, and manipulating environment variables for RCE

#### Networks

- **[DNS Poisoning](Lab_Writeups/Exploits/Network/DNS_Cache_Poisoning.pdf)** - SeedLab's DNS Spoofing & Poisoning
- **[TCP/IP Attacks](Lab_Writeups/Exploits/Network/TCP_IP_Attacks.pdf)** - Syn Flooding, TCP Resetting, and TCP Session Hijacking

#### Cryptography

- **[Encryption](Lab_Writeups/Exploits/Cryptography/Encryption.pdf)** - OpenSSL, Block Ciphers, Subsitution Ciphers, Known Plaintext using repeated IVs on AES-128-CBC
- **[Hashing](Lab_Writeups/Exploits/Cryptography/MD5_Collision.pdf)** - Brute forcing hashed password, MD5 Collisions

#### Web

- **[SQL Injections](Lab_Writeups/Exploits/Web/SQL_Injections.pdf)** - SeedLab's SQLI Lab.
- **[XSS Attacks](Lab_Writeups/Exploits/Web/XXS_Attack.pdf)** - SeedLab's XSS Attack Lab.

### Forensics

- **[Emotet Trojan on Wireshark](Lab_Writeups/Forensics/Wireshark_Trace_Analysis_Emotet_Trojan.pdf)** - A Wireshark trace of an infected machine was analyzed, parts of the Cyber Kill Chain were identified, and a timeline was developed.
