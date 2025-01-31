Nikto is an open-source web server scanner that tests web servers for potentially dangerous files, outdated software, and configuration issues. It performs comprehensive tests against web servers, checking for over 6,700 potentially dangerous files/programs, outdated versions, and version-specific problems on more than 1,250 servers.

Here is a detailed documentation on how to install, configure, and use Nikto:

---

## **Nikto Tool Documentation**

### **1. Installation**

#### **a. Prerequisites:**
- Perl (Nikto is written in Perl and requires it to run).

#### **b. Installation Steps:**
1. **Install Perl (if not already installed):**
   - **On Debian/Ubuntu:**
     ```bash
     sudo apt-get update
     sudo apt-get install perl
     ```
   - **On Red Hat/CentOS:**
     ```bash
     sudo yum install perl
     ```

2. **Clone the Nikto repository:**
   ```bash
   git clone https://github.com/sullo/nikto.git
   ```

3. **Navigate to the Nikto directory:**
   ```bash
   cd nikto/program
   ```

4. **Make the `nikto.pl` script executable (optional):**
   ```bash
   chmod +x nikto.pl
   ```

5. **Install any additional Perl modules if required (usually done automatically):**
   ```bash
   cpan install <module_name>
   ```

### **2. Basic Usage**

Nikto can be used to scan web servers for vulnerabilities and issues. The basic command syntax is:

```bash
perl nikto.pl -h <target>
```

#### **Example:**
```bash
perl nikto.pl -h http://anshinfotech.org
```

### **3. Command-Line Options**

- **`-h <target>`**: Specify the target to scan. The target can be an IP address, hostname, or a URL.

- **`-port <port_number>`**: Specify the port to scan. The default is port 80 (HTTP).
  - Example: `-port 8080`

- **`-ssl`**: Force SSL mode (HTTPS) if the target does not use standard HTTPS ports (443).
  - Example: `perl nikto.pl -h https://anshinfotech.org -ssl`

- **`-output <filename>`**: Save the scan results to a specified file.
  - Example: `-output nikto_scan.txt`

- **`-Format <output_format>`**: Define the format for the output file (`txt`, `html`, `csv`, `xml`).
  - Example: `-output scan.html -Format html`

- **`-Cgidirs <directory>`**: Scan specified CGI directories. The default is `/cgi-bin/`.
  - Example: `-Cgidirs /cgi/`

- **`-mutate <test_type>`**: Enable mutation techniques for testing (like directory brute-forcing).
  - Example: `-mutate 2`

- **`-Tuning <tuning_option>`**: Control the type of checks performed. Tuning options allow you to specify categories of tests (e.g., file checks, injection, XSS, etc.).
  - Example: `-Tuning 123`

- **`-evasion <evasion_technique>`**: Use evasion techniques to avoid detection by WAFs or IDS.
  - Example: `-evasion 1`

- **`-update`**: Update the Nikto database with the latest vulnerability checks.
  - Example: `perl nikto.pl -update`

- **`-vhost <hostname>`**: Scan a virtual host.
  - Example: `-vhost vhost.anshinfotech.org`

- **`-Plugins <plugin_name>`**: Specify the plugin(s) to use during the scan.
  - Example: `-Plugins all`

- **`-list-plugins`**: List all available plugins.
  - Example: `perl nikto.pl -list-plugins`

### **4. Advanced Usage**

- **Scan Multiple Targets:**
  You can specify multiple targets in a text file and instruct Nikto to scan them all.
  ```bash
  perl nikto.pl -h targets.txt
  ```
  - The `targets.txt` file should contain one target per line.

- **Verbose Output:**
  To see detailed output during the scan, use the `-Display V` option.
  ```bash
  perl nikto.pl -h anshinfotech.org -Display V
  ```

- **Scan a Specific Web Application:**
  If you need to scan a particular path (e.g., a web application), specify it in the URL.
  ```bash
  perl nikto.pl -h http://anshinfotech.org/webapp/
  ```

### **5. Output Interpretation**

Nikto provides a variety of information in its output, including:

- **Vulnerabilities:** It lists known vulnerabilities and issues, such as outdated software, misconfigurations, or potentially dangerous files.
- **Severity:** Each issue is categorized by its severity (e.g., informational, warning, high risk).
- **Potential Exploits:** If applicable, Nikto may suggest known exploits related to the detected vulnerability.

### **6. Best Practices**

- **Run Regular Updates:** Keep Nikto’s database updated to ensure it detects the latest vulnerabilities.
  ```bash
  perl nikto.pl -update
  ```

- **Combine with Other Tools:** While Nikto is powerful, it’s recommended to use it alongside other web application security tools (like Burp Suite, OWASP ZAP) for more comprehensive testing.

- **Run Non-Intrusive Scans:** Be cautious when scanning production servers. Start with non-intrusive scans to avoid disruptions.

- **Check Logs:** Always review web server logs after running Nikto to see if the scan caused any issues or if it triggered any alerts.

### **7. Additional Resources**

- **Official GitHub Repository:** [Nikto on GitHub](https://github.com/sullo/nikto)
- **Nikto Documentation:** Detailed help and configuration options can be accessed using:
  ```bash
  perl nikto.pl -Help
  ```

- **Community Forums:** Engage with other users or seek help on forums like Reddit or specialized security forums.

---

This documentation should help you effectively use Nikto to scan web servers for vulnerabilities and issues.