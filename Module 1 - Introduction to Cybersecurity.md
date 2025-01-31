
---

### **1.1 Overview of Cybersecurity**

#### **Definition**
Cybersecurity is the practice of protecting computers, servers, mobile devices, electronic systems, networks, and data from malicious attacks, damage, or unauthorized access. It involves the implementation of various measures and controls to ensure that digital assets remain secure.

#### **Importance**
- **Confidentiality:** Ensures that sensitive information is accessible only to those authorized to view it.
- **Integrity:** Maintains the accuracy and completeness of information and systems.
- **Availability:** Ensures that information and resources are available to authorized users when needed.

**Examples:**
- **Confidentiality:** Using encryption to protect sensitive financial data transmitted over the internet.
- **Integrity:** Implementing checksums to verify that software updates have not been tampered with.
- **Availability:** Using redundant power supplies and backup systems to ensure continuous access to critical services.

### **1.2 Key Concepts**

#### **Confidentiality**
- **Definition:** Preventing unauthorized access to sensitive information.
- **Techniques:**
  - **Encryption:** Converting data into a code to prevent unauthorized access.
    - **Example:** Encrypting emails using PGP (Pretty Good Privacy) to protect the content from unauthorized readers.
  - **Access Controls:** Mechanisms to ensure only authorized users can access certain data or systems.
    - **Example:** Implementing multi-factor authentication (MFA) to secure user accounts.
- **Examples:**
  - **Using Encryption:** Secure Socket Layer (SSL) certificates for HTTPS websites to protect data transmitted between the user and the website.
  - **Access Control Lists (ACLs):** Defining user permissions on files and directories in operating systems.

#### **Integrity**
- **Definition:** Ensuring that information remains accurate and unaltered.
- **Techniques:**
  - **Hash Functions:** Generating a unique hash value for data, allowing verification of its integrity.
    - **Example:** Using SHA-256 to generate a hash of a downloaded file to ensure it has not been altered.
  - **Digital Signatures:** Verifying the authenticity and integrity of digital messages or documents.
    - **Example:** Signing software releases with a digital certificate to verify that they come from a trusted source and have not been modified.
- **Examples:**
  - **Checksums:** Comparing the checksum value of a file before and after download to detect any unauthorized changes.
  - **Data Validation Rules:** Implementing validation rules in databases to ensure data entered meets specific criteria and constraints.

#### **Availability**
- **Definition:** Ensuring that data and resources are available to authorized users when needed.
- **Techniques:**
  - **Redundancy:** Implementing backup systems and data replication to ensure continuity.
    - **Example:** Using RAID (Redundant Array of Independent Disks) to protect against data loss due to disk failure.
  - **Disaster Recovery Planning:** Preparing procedures for recovery in case of system failures or data loss.
    - **Example:** Creating and regularly testing a disaster recovery plan that includes backup procedures and recovery steps.
- **Examples:**
  - **Load Balancers:** Distributing network traffic across multiple servers to prevent overloading any single server and ensure high availability.
  - **Backup Systems:** Regularly backing up critical data and storing it in multiple locations to ensure recovery in case of a system failure.

### **1.3 Cyber Threats and Vulnerabilities**

#### **Types of Threats**

- **Malware:**
  - **Definition:** Malicious software designed to harm or exploit systems.
  - **Types:**
    - **Viruses:** Infect other files or systems, spreading as they replicate.
      - **Example:** The ILOVEYOU virus, which spread through email attachments and caused significant damage.
    - **Worms:** Self-replicating malware that spreads across networks without needing a host file.
      - **Example:** The WannaCry ransomware worm, which exploited a vulnerability to encrypt data and demand ransom.
    - **Ransomware:** Encrypts files and demands payment for decryption.
      - **Example:** Cryptolocker ransomware, which encrypts files on a victim's system and demands payment in cryptocurrency for the decryption key.
  
- **Phishing:**
  - **Definition:** Fraudulent attempts to obtain sensitive information by pretending to be a trustworthy entity.
  - **Types:**
    - **Email Phishing:** Sending fraudulent emails to trick individuals into providing personal information.
      - **Example:** An email pretending to be from a bank asking users to click on a link and enter their account details.
    - **Spear Phishing:** Targeted attacks aimed at specific individuals or organizations.
      - **Example:** A spear-phishing email targeting a company’s CFO with a fake request for a wire transfer.

- **Social Engineering:**
  - **Definition:** Manipulating individuals into divulging confidential information or performing actions that compromise security.
  - **Techniques:**
    - **Pretexting:** Creating a fabricated scenario to obtain information.
      - **Example:** Pretending to be an IT support technician to gain access to a user’s account.
    - **Baiting:** Offering something desirable to entice individuals into revealing information or installing malware.
      - **Example:** Leaving an infected USB drive in a public place with a label enticing the finder to plug it into their computer.
- **Examples:**
  - **Pretexting:** A call from someone claiming to be from a legitimate company’s IT department, asking for login credentials.
  - **Baiting:** A USB drive left in a public area, with the label “Employee Salaries” encouraging people to plug it into their systems.

#### **Common Vulnerabilities**

- **CVEs (Common Vulnerabilities and Exposures):**
  - **Definition:** A publicly disclosed list of known security vulnerabilities.
  - **Example:** CVE-2017-0144, known as EternalBlue, a vulnerability exploited by ransomware like WannaCry.
  
- **Zero-Day Exploits:**
  - **Definition:** Vulnerabilities that are unknown to the vendor or public, with no available patch.
  - **Example:** A new vulnerability in an operating system that attackers discover and exploit before the vendor is aware and can release a patch.

### **1.4 Cybersecurity Frameworks**

#### **NIST Cybersecurity Framework**
- **Core Functions:**
  - **Identify:** Develop an understanding of organizational risks and assets.
    - **Example:** Creating an inventory of all hardware and software assets.
  - **Protect:** Implement safeguards to limit the impact of potential security incidents.
    - **Example:** Applying encryption and access control measures.
  - **Detect:** Implement mechanisms to identify and detect cybersecurity events.
    - **Example:** Setting up intrusion detection systems (IDS) and monitoring network traffic.
  - **Respond:** Develop and implement strategies for responding to detected cybersecurity incidents.
    - **Example:** Establishing an incident response team and procedures for handling breaches.
  - **Recover:** Implement processes to restore normal operations after a cybersecurity incident.
    - **Example:** Restoring data from backups and assessing the impact of the incident.

#### **ISO/IEC 27001**
- **Overview:**
  - **Definition:** An international standard for establishing, implementing, maintaining, and improving an Information Security Management System (ISMS).
  - **Key Aspects:**
    - **Risk Management:** Identifying and managing security risks.
    - **Controls and Procedures:** Implementing security controls to protect information.
    - **Continuous Improvement:** Regularly reviewing and improving the ISMS.
- **Example:**
  - A company may use ISO/IEC 27001 to develop and maintain an information security policy, conduct risk assessments, and ensure compliance with security standards.

#### **CIS Controls**
- **Overview:**
  - **Definition:** A set of best practices for securing IT systems and data.
  - **Controls Include:**
    - **Inventory and Control of Hardware Assets:** Keeping track of all hardware devices within the organization.
    - **Secure Configuration for Hardware and Software:** Ensuring that all systems are configured securely.
    - **Continuous Monitoring:** Implementing continuous monitoring to detect and respond to security incidents.
- **Example:**
  - Implementing Control 1: Inventory and Control of Hardware Assets, which involves maintaining an up-to-date inventory of all devices connected to the network to ensure they are properly managed and secured.

---
