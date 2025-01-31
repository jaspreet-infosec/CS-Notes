**RedHawk** is an all-in-one tool designed for information gathering, vulnerability scanning, and much more. It’s written in PHP and is quite user-friendly, making it an excellent choice for those learning cybersecurity.

### **Installing RedHawk**

Before using RedHawk, you'll need to clone the repository from GitHub and install any required dependencies.

1. **Clone the RedHawk Repository:**
   ```bash
   git clone https://github.com/Tuhinshubhra/RED_HAWK.git
   ```

2. **Navigate to the RedHawk Directory:**
   ```bash
   cd RED_HAWK
   ```

3. **Run RedHawk:**
   ```bash
   php rhawk.php
   ```

### **Using RedHawk**

Once you have RedHawk up and running, you can use it to perform various tasks. Here’s a breakdown of the basic commands and functionalities.

1. **Start RedHawk:**
   - Simply running `php rhawk.php` will start RedHawk, and you will be greeted with the main menu.

2. **Scan a Website:**
   - You’ll first be prompted to enter the website you wish to scan.
   - After entering the URL, you’ll be asked if the site is HTTPS (Y/N).

3. **RedHawk Main Menu Options:**

   - **1) Basic Scan:**
     ```bash
     Basic Info Gathering (WHOIS Lookup, Geo-IP Lookup, DNS Lookup, Subnet Calculator)
     ```
   - **2) Whois Lookup:**
     ```bash
     Performs a WHOIS lookup to gather domain registration information.
     ```
   - **3) Geo-IP Lookup:**
     ```bash
     Provides geographical information about the IP address of the target.
     ```
   - **4) DNS Lookup:**
     ```bash
     Retrieves DNS records of the target domain.
     ```
   - **5) Subnet Calculator:**
     ```bash
     Calculates the subnet based on the IP range.
     ```
   - **6) Reverse IP Lookup & CMS Detection:**
     ```bash
     Performs a reverse IP lookup to find other domains hosted on the same server and attempts to detect the CMS used.
     ```
   - **7) Subdomain Scanner:**
     ```bash
     Scans for subdomains associated with the target domain.
     ```
   - **8) Nmap Port Scan:**
     ```bash
     Integrates with Nmap to perform a port scan.
     ```
   - **9) HTTP Header Grabber:**
     ```bash
     Retrieves the HTTP headers from the target.
     ```
   - **10) Find Admin Panel:**
     ```bash
     Attempts to locate the admin panel of the target website.
     ```
   - **11) PHP Info Grabber:**
     ```bash
     Tries to extract PHP information if accessible.
     ```
   - **12) Extract All Links:**
     ```bash
     Extracts all the links found on the target website.
     ```
   - **13) Google Dorking:**
     ```bash
     Automates Google Dorking to find potential vulnerabilities via search engine queries.
     ```

### **Example Usage**

Here’s an example workflow using RedHawk to gather information and scan a website:

1. **Start RedHawk:**
   ```bash
   php rhawk.php
   ```

2. **Enter the Target Website:**
   ```bash
   Enter Website: example.com
   Is the website HTTPS? (Y/N): N
   ```

3. **Choose an Option from the Menu:**
   - Let’s say you want to perform a basic scan:
     ```bash
     1
     ```
   - RedHawk will then perform the WHOIS Lookup, Geo-IP Lookup, DNS Lookup, and Subnet Calculation.

4. **View Results:**
   - The results will be displayed in the terminal, showing various details about the target.

### **Advanced Features**
- **RedHawk’s Database Feature:**
  - RedHawk can save scan results into a database for later use.
  - When prompted, you can choose to save the results to a database.
  - This feature requires that you have a local or remote MySQL database set up and configured within RedHawk.

### **Conclusion**
RedHawk is a versatile and easy-to-use tool for beginners in cybersecurity. It covers a wide range of tasks from information gathering to vulnerability scanning, making it a great all-in-one tool for students. By using RedHawk, students can learn the basics of web application scanning and information gathering in an efficient and streamlined way.

This documentation provides a solid foundation for using RedHawk, and students can experiment further by exploring each feature in detail.