The **Social-Engineer Toolkit (SET)** is an open-source penetration testing framework designed for social engineering. SET is primarily used for phishing attacks, spear-phishing, and other forms of social engineering by creating convincing attack vectors to exploit human vulnerabilities. Below is a detailed documentation of how to install, configure, and use SET.

### **Installation of SET**

#### **1. Install Prerequisites**
Before installing SET, ensure your system has the required dependencies.

For Debian/Ubuntu-based systems:
```bash
sudo apt-get update
sudo apt-get install git python3-pip -y
```

For RedHat/CentOS-based systems:
```bash
sudo yum update
sudo yum install git python3-pip -y
```

#### **2. Clone the SET Repository**
You can clone the SET repository from GitHub to your local machine.

```bash
git clone https://github.com/trustedsec/social-engineer-toolkit.git
```

#### **3. Navigate to the SET Directory**
Change to the SET directory that you just cloned.

```bash
cd social-engineer-toolkit
```

#### **4. Install SET**
To install SET, you simply need to run the setup script.

```bash
sudo python3 setup.py
```

### **Running the Social-Engineer Toolkit**

To start SET, navigate to the directory where SET was installed and run the following command:

```bash
sudo setoolkit
```

### **SET Main Menu Options**

Once you start SET, you’ll be presented with a main menu that offers various attack vectors. Below is a breakdown of the options and how they can be used.

1. **Social-Engineering Attacks:**
   - **1) Spear-Phishing Attack Vectors:** 
     - **Method:** This option is used to craft and send phishing emails.
     - **Usage:** You can send emails with malicious attachments or links to exploit vulnerabilities in email clients.
   - **2) Website Attack Vectors:** 
     - **Method:** Clone websites or create malicious web pages to steal credentials or inject malicious code.
     - **Usage:** Useful for creating fake login pages or browsers' exploitation via drive-by downloads.
   - **3) Infectious Media Generator:** 
     - **Method:** Generate payloads to be placed on USB drives or CDs.
     - **Usage:** Social engineering via physical media—great for targeted attacks in closed environments.
   - **4) Create a Payload and Listener:** 
     - **Method:** Create backdoors and listener scripts.
     - **Usage:** Used in conjunction with the phishing attacks or infected media for gaining control over systems.
   - **5) Mass Mailer Attack:** 
     - **Method:** Send mass emails.
     - **Usage:** For large-scale phishing campaigns.
   - **6) Arduino-Based Attack Vector:** 
     - **Method:** Use Arduino-based boards for keystroke injection.
     - **Usage:** Used for hardware-based social engineering attacks.
   - **7) Wireless Access Point Attack Vector:** 
     - **Method:** Create rogue access points to capture credentials.
     - **Usage:** Effective in environments with unsecured wireless networks.
   - **8) QRCode Generator Attack Vector:** 
     - **Method:** Generate QR codes with embedded malicious URLs or payloads.
     - **Usage:** Used to trick targets into scanning malicious QR codes.
   - **9) Powershell Attack Vectors:** 
     - **Method:** Exploit targets via PowerShell scripts.
     - **Usage:** Used for post-exploitation or direct exploitation on systems with PowerShell enabled.
   - **10) SMS Spoofing Attack Vector:** 
     - **Method:** Spoof SMS messages.
     - **Usage:** Effective for impersonation and scamming via SMS.
   - **11) Third Party Modules:** 
     - **Method:** Extend SET’s functionality with additional modules.
     - **Usage:** Depends on the third-party module being used.

### **Example Attack: Phishing with a Website Attack Vector**

One of the most common uses of SET is to clone a website and use it for phishing purposes. Below is a step-by-step guide:

#### **1. Start SET**
```bash
sudo setoolkit
```

#### **2. Select "Social-Engineering Attacks"**
Choose option `1` from the main menu to start social-engineering attacks.

#### **3. Select "Website Attack Vectors"**
Choose option `2` from the social-engineering attacks menu.

#### **4. Select "Credential Harvester Attack Method"**
Choose option `3` from the website attack vectors menu.

#### **5. Select "Site Cloner"**
Choose option `2` from the credential harvester attack method menu.

#### **6. Enter the URL of the Website to Clone**
You will be prompted to enter the URL of the website you wish to clone, e.g., `http://example.com`.

#### **7. Set Up the Listener**
SET will ask if you want to use a predefined template or write your own. For simplicity, use the predefined template.

#### **8. Phishing Page is Live**
SET will clone the website and host it on your machine. You will be given a URL (usually your machine’s IP address) to send to your target. When the target enters credentials, they will be captured by SET and displayed in your terminal.

### **Reporting and Logging**

SET automatically logs all activities during the attack. You can find these logs in the `logs` directory within the SET folder. These logs can be used for reporting and analysis.

### **Ethical Considerations**

While SET is a powerful tool for social engineering, it's important to stress ethical usage. Ensure that you have explicit permission from the target organization before conducting any tests. Unauthorized use of SET can lead to legal consequences.

