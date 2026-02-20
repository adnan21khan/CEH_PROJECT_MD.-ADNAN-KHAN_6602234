# 🛡️ Ethical Hacking Project: Simulating Real-World Network Exploitation and Defense

**Author:** MD Adnan Khan  
**Semester:** 6th  
**Section:** CY6

---

## 📘 Project Overview

This project simulates a **real-world penetration test** in an isolated virtual lab environment using tools such as:

- **Nmap** for scanning and reconnaissance  
- **Metasploit** for exploitation  
- **John the Ripper** for password cracking  

It covers a complete ethical hacking lifecycle: scanning, enumeration, exploitation, privilege escalation, password cracking, and remediation.

---

## 📂 Project Contents

- 📄 `CEH_Project_adnan.pdf` — Full report with screenshots and command outputs  
- 🖼️ `Screenshots/` — Real-time evidence of network attacks and defenses  

---

## 🎯 Objectives

- 🔍 Identify system vulnerabilities through simulated cyber-attacks  
- 💡 Practice responsible ethical hacking techniques  
- 🛠️ Learn remediation strategies for discovered weaknesses  

---

## 🧰 Tools & Environment

| Tool              | Purpose                        |
|------------------|--------------------------------|
| Kali Linux        | Attacking machine              |
| Metasploitable     | Vulnerable target machine      |
| Nmap              | Network and port scanning      |
| Metasploit Framework | Exploitation tool             |
| John the Ripper   | Password hash cracking         |

---

## 🔍 Task Breakdown & Key Results

### 🔹 Task 1: Basic Network Scanning
**Command:**
```bash
nmap -v 192.168.1.0/24
```
**Results:**
- `192.168.1.10` → Ports 22 (SSH), 80 (HTTP)
- `192.168.1.15` → Port 21 (FTP)

---

### 🔹 Task 2: Reconnaissance

#### 2.1 Hidden Port Scan
```bash
nmap -v -p- 192.168.1.10
```
**Hidden Ports Found:**
- 8787 (drb), 47436 (mountd), 50918 (java-rmi), 59995 (nlockmgr), 60004 (status)

#### 2.2 Service Version Detection
```bash
nmap -v -sV 192.168.1.10
```
- `21/tcp` → vsftpd 2.3.4  
- `22/tcp` → OpenSSH 4.7p1  

#### 2.3 OS Detection
```bash
nmap -v -O 192.168.1.10
```
- OS: Linux 2.6.9 – 2.6.33

---

### 🔹 Task 3: Enumeration Summary

| Parameter      | Value                         |
|----------------|-------------------------------|
| Target IP      | 192.168.1.10                  |
| MAC Address    | 00:0C:29:5D:FE:0B             |
| Open Ports     | 21 (FTP), 22 (SSH)            |

---

### 🔹 Task 4: Exploitation

- `vsftpd 2.3.4` → Exploited using `exploit/unix/ftp/vsftpd_234_backdoor`  
- `SMB (Samba 3.0.20)` → Exploited using `usermap_script`  
- `R Services` → Access via legacy tools (rexec, rlogin, rsh)  

---

### 🔹 Task 5: Privilege Escalation

**Command Used:**
```bash
adduser swapnil
```

**Results:**

In `/etc/passwd`:
```
swapnil:x:1001:1001:/home/swapnil:/bin/bash
```

In `/etc/shadow`:
```
swapnil:$1$8nWuasXV$pk6ZABfqT9NoHv1pPX8Rj.
```

---

### 🔹 Task 6: Password Hash Cracking

**Tool Used:** John the Ripper  
**Command:**
```bash
john hashes.txt
john hashes.txt --show
```

✅ **Cracked Password:** `hello`

---

### 🔹 Task 7: Remediation Recommendations

| Vulnerability    | Recommendation                        |
|------------------|----------------------------------------|
| vsftpd 2.3.4      | Upgrade to version 3.0.5              |
| OpenSSH 4.7p1     | Upgrade to OpenSSH 9.6                |
| Java RMI          | Disable or restrict via firewall      |
| R Services        | Remove or disable deprecated services |

---

## 🎓 Major Learnings

- Conducted deep network scans using Nmap  
- Performed real-world exploitation with Metasploit  
- Practiced password cracking and privilege escalation  
- Learned Linux system user management and service hardening  

---

## ⚠️ Disclaimer

> This project is strictly for educational purposes. All activities were conducted in a closed virtual environment with no access to external or live systems.

---

## 📜 License

**MIT License** — Free to fork, adapt, or extend for learning and research purposes.

---
