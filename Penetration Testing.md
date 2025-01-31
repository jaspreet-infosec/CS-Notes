
---

## **Phases of Website Penetration Testing**

### **1. Reconnaissance**

The first step is gathering information about the target website, such as its domain, IP addresses, subdomains, and technologies in use.

#### **Recommended Tools and Steps**

1. **Nmap** (Network Mapper)
    
    - **Description:** Scans for open ports and services running on the target.
    - **Command Example:**
        
        ```bash
        nmap -sC -sV -oN scan_results.txt target.com
        ```
        
    - **Steps:**
        1. Install Nmap: [Nmap Download](https://nmap.org/download.html)
        2. Run the command with `-sC` (default scripts) and `-sV` (service version detection).
2. **Amass** (Subdomain enumeration)
    
    - **Description:** Identifies subdomains associated with the target domain.
    - **Command Example:**
        
        ```bash
        amass enum -d target.com
        ```
        
    - **Steps:**
        1. Install: [Amass GitHub](https://github.com/owasp/amass)
        2. Run the command to collect subdomains.
3. **WhatWeb** (Technology identification)
    
    - **Description:** Detects CMS, programming languages, frameworks, etc.
    - **Command Example:**
        
        ```bash
        whatweb target.com
        ```
        
    - **Steps:**
        1. Install: [WhatWeb GitHub](https://github.com/urbanadventurer/WhatWeb)
        2. Run the tool to enumerate website technologies.

---

### **2. Scanning**

This phase involves identifying vulnerabilities in the web application.

#### **Recommended Tools and Steps**

1. **OWASP ZAP** (Zed Attack Proxy)
    
    - **Description:** A proxy tool for automated vulnerability scanning.
    - **Steps:**
        1. Install: [OWASP ZAP Download](https://www.zaproxy.org/download/)
        2. Configure your browser to use ZAP as a proxy.
        3. Perform an active scan by navigating to `Tools > Active Scan`.
2. **Nikto** (Web server scanner)
    
    - **Description:** Scans for common web server misconfigurations and vulnerabilities.
    - **Command Example:**
        
        ```bash
        nikto -h target.com
        ```
        
    - **Steps:**
        1. Install: [Nikto GitHub](https://github.com/sullo/nikto)
        2. Use the command to scan for known issues.
3. **Burp Suite** (Professional and Community Edition)
    
    - **Description:** A powerful web application vulnerability scanner.
    - **Steps:**
        1. Install: [Burp Suite](https://portswigger.net/burp)
        2. Configure your browser proxy settings.
        3. Use the scanner to test for SQLi, XSS, and other vulnerabilities.

---

### **3. Exploitation**

In this phase, attempt to exploit identified vulnerabilities to demonstrate the risk.

#### **Recommended Tools and Steps**

1. **SQLmap** (Automated SQL Injection tool)
    
    - **Description:** Tests for and exploits SQL injection vulnerabilities.
    - **Command Example:**
        
        ```bash
        sqlmap -u "http://target.com/page?id=1" --dbs
        ```
        
    - **Steps:**
        1. Install: [SQLmap GitHub](https://github.com/sqlmapproject/sqlmap)
        2. Run the command with the vulnerable URL to enumerate databases.
2. **XSStrike** (XSS testing tool)
    
    - **Description:** Detects and exploits XSS vulnerabilities.
    - **Command Example:**
        
        ```bash
        python3 xsstrike.py -u "http://target.com"
        ```
        
    - **Steps:**
        1. Install: [XSStrike GitHub](https://github.com/s0md3v/XSStrike)
        2. Run the tool with the target URL.
3. **Metasploit** (Framework for exploiting vulnerabilities)
    
    - **Description:** Leverages known vulnerabilities to test exploitation possibilities.
    - **Steps:**
        1. Install: [Metasploit Download](https://www.metasploit.com/)
        2. Use:
            
            ```bash
            msfconsole
            ```
            
            Search for and use appropriate exploit modules.

---

### **4. Post-Exploitation**

Assess the impact of the vulnerabilities you exploited and maintain access if necessary.

#### **Recommended Tools and Steps**

1. **Mimikatz** (Credential harvesting on Windows servers)
    
    - **Description:** Extracts credentials after exploiting a Windows machine.
    - **Steps:**
        1. Install: [Mimikatz GitHub](https://github.com/gentilkiwi/mimikatz)
        2. Use after gaining access to the server.
2. **Empire** (Post-exploitation framework)
    
    - **Description:** Maintains access to compromised systems.
    - **Steps:**
        1. Install: [Empire GitHub](https://github.com/EmpireProject/Empire)
        2. Use for lateral movement and maintaining persistence.

---

### **5. Reporting**

Document findings, impacts, evidence, and recommendations.

#### **Tools for Reporting**

1. **Dradis Framework**
    
    - **Description:** Organizes pentest findings into a professional report.
    - **Install:** [Dradis GitHub](https://github.com/dradis/dradis-ce)
2. **MS Word/Excel**
    
    - Structure findings, including:
        - Vulnerability Name
        - Description
        - Risk Rating
        - Proof of Concept
        - Recommendations

---

## **General Recommendations**

- Always get written permission before conducting a penetration test.
- Follow legal and ethical guidelines.
- Ensure tools are used responsibly and within the scope of the agreement.

This workflow provides a comprehensive overview of how to approach website penetration testing with effective tools. Let me know if you need more details on any specific tool or phase!