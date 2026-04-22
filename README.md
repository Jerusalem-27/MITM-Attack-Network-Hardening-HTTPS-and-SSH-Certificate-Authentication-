##  MITM Attack & HTTPS/SSH Hardening


---

##  Overview

Simulated a Man-in-the-Middle (MITM) attack to show how attackers can capture credentials over insecure HTTP. Secured the environment by enforcing HTTPS and implementing SSH certificate-based authentication to prevent unauthorized access.

---

##  Investigation Evidence  

### 1. Credential Interception via MITM (HTTP)  

<p align="center">
  <img src="./evidence/01 - arp-spoofing-mitm-credential-capture.png" width="800">
</p>

Captured plaintext credentials during a MITM attack, confirming exposure over unencrypted HTTP.

---

### 2. HTTPS Protection Against MITM  

<p align="center">
  <img src="./evidence/02 -  https-encryption-prevents-credential-exposure.png" width="800">
</p>

Re-tested the attack after enabling HTTPS. Credentials were no longer visible, confirming encryption effectiveness.

---

### 3. Nginx Vulnerability Detection  

<p align="center">
  <img src="./evidence/03 - nginx-version-vulnerability-detection.png" width="800">
</p>

Identified an outdated Nginx version, introducing potential security vulnerabilities.

---

### 4. Nginx Patch Verification  

<p align="center">
  <img src="./evidence/04 - nginx-version-upgrade-verification.png" width="800">
</p>

Upgraded Nginx to a secure version, reducing exposure to known vulnerabilities.

---

### 5. Certificate Authority Setup  

<p align="center">
  <img src="./evidence/05 - certificate-authority-x509-details.png" width="800">
</p>

Configured a Certificate Authority (CA) to issue trusted X.509 certificates.

---

### 6. SSH Certificate Validation  

<p align="center">
  <img src="./evidence/06 -  ssh-certificate-principals-and-extensions.png" width="800">
</p>

Verified certificate-based SSH authentication, including principals and access permissions.

---

### 7. Secure SSH Access (Certificate Authentication)  

<p align="center">
  <img src="./evidence/07 - ssh-certificate-authentication-success.png" width="800">
</p>

Successfully authenticated using SSH certificates, eliminating password-based login risks.

---

### 8. Unauthorized Access Blocked  

<p align="center">
  <img src="./evidence/08 - ssh-access-denied-without-certificate.png" width="800">
</p>

Unauthorized login attempts were denied, confirming proper access control enforcement.

---

##  Detection Summary 

This project focuses on identifying insecure communication and weak authentication that can lead to credential compromise. Instead of relying only on alerts, the detection approach simulates real attacker behavior to validate how security controls perform in practice.

Detection logic includes:

- Identifying plaintext credential exposure over HTTP  
- Detecting ARP spoofing activity used for MITM attacks  
- Comparing HTTP vs HTTPS to validate encryption effectiveness  
- Identifying vulnerable service versions (Nginx)  
- Detecting weak SSH authentication (password-based access)  
- Verifying certificate-based authentication enforcement  
- Confirming access control by blocking unauthorized login attempts  

This approach demonstrates how attackers exploit insecure configurations and how proper security controls prevent compromise.

---

##  Attack Scenario  

An attacker places themselves between a user and a server using ARP spoofing to intercept network traffic. Once in position, the attacker can:
- Capture login credentials sent over HTTP  
- Monitor and manipulate network communication  
- Exploit outdated services  
- Attempt unauthorized SSH access  

Without proper security controls, this can lead to credential theft and unauthorized system access.

---

##  Key Findings  

- High: Credentials exposed over HTTP during MITM attack  
- High: Lack of encryption enabled interception and manipulation  
- Medium: Outdated Nginx version introduced security risk  
- Medium: Password-based SSH authentication increased attack surface

---

##  Security Improvements  

- Enforced HTTPS to secure data in transit  
- Eliminated credential exposure in MITM scenarios  
- Upgraded vulnerable services (Nginx)  
- Implemented certificate-based SSH authentication  
- Disabled insecure authentication mechanisms  
- Enforced strict access control policies  

---

##  Detection Focus  

- Insecure communication (HTTP vs HTTPS)  
- MITM attack techniques (ARP spoofing)  
- Credential exposure risks  
- Vulnerable service identification  
- Weak authentication mechanisms  
- Access control enforcement  

---

##  Technologies & Tools

- Ettercap (MITM / ARP Spoofing)  
- Nmap (Network Scanning)  
- Nginx (Web Server)  
- OpenSSH (Secure Access)  
- Step CA (Certificate Authority)  
- Linux CLI & PowerShell  

---

##  Skills Demonstrated  

- Network Security (MITM, ARP Spoofing)  
- Traffic Analysis  
- Web Security (HTTP vs HTTPS)  
- Vulnerability Management  
- Identity & Access Management  
- SSH Hardening & Certificate Authentication  
- Security Control Validation  

---

##  Why This Project Matters  

MITM attacks remain a common technique for intercepting sensitive data in poorly secured environments. This project demonstrates how simple misconfigurations can lead to credential compromise and how implementing encryption and strong authentication effectively prevents these attacks.

---

##  Conclusion  

This project demonstrates both the exploitation and mitigation of MITM attacks. By combining attack simulation with defensive controls, it highlights how organizations can secure communication channels and enforce strong access controls to prevent unauthorized access.

---

##  Disclaimer  

This project was conducted in a controlled environment for defensive security and validation of mitigation techniques.
