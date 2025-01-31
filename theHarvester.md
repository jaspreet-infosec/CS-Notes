pTheHarvester is a powerful tool for gathering information about a target from public sources (OSINT - Open Source Intelligence). It is often used to find email addresses, subdomains, IP addresses, URLs, and more. Below are the commands and options for using TheHarvester effectively.

### **Basic Command Syntax**
```bash
theHarvester -d <domain> -b <source>
```
- `-d <domain>`: Specifies the target domain to gather information about.
- `-b <source>`: Specifies the data source from which to gather information.

### **Common Usage Examples**

1. **Basic Email and Subdomain Gathering from Google:**
   ```bash
   theHarvester -d example.com -b google
   ```
   - This command searches Google for emails and subdomains related to `example.com`.

2. **Gather Information from Multiple Sources:**
   ```bash
   theHarvester -d example.com -b google,bing,yahoo
   ```
   - This command searches Google, Bing, and Yahoo for information about `example.com`.

3. **Output the Results to an HTML File:**
   ```bash
   theHarvester -d example.com -b google -f report.html
   ```
   - This command gathers information and saves the output in an HTML file named `report.html`.

4. **Output the Results to an XML File:**
   ```bash
   theHarvester -d example.com -b google -f report.xml
   ```
   - This command saves the gathered information in an XML file.

5. **Limit the Number of Results:**
   ```bash
   theHarvester -d example.com -b google -l 500
   ```
   - The `-l` option limits the number of search results to 500.

6. **Use a Specific Virtual Host to Perform Queries:**
   ```bash
   theHarvester -d example.com -b google -v <vhost>
   ```
   - The `-v` option allows you to specify a virtual host for the queries.

7. **Passive DNS Query (using Netcraft):**
   ```bash
   theHarvester -d example.com -b netcraft
   ```
   - This command uses Netcraft to perform passive DNS queries for the target domain.

8. **Perform Active Search Using DNS Brute Force:**
   ```bash
   theHarvester -d example.com -b bing -c
   ```
   - The `-c` flag enables DNS brute forcing.

9. **Search and Save All Results to a JSON File:**
   ```bash
   theHarvester -d example.com -b google -f results.json
   ```
   - Saves the output in JSON format.

10. **Specify DNS Server for DNS Brute Force:**
    ```bash
    theHarvester -d example.com -b google -g dns.server.ip
    ```
    - The `-g` option allows you to specify a particular DNS server.

### **Supported Data Sources**

TheHarvester supports various sources for information gathering:
- `google`
- `bing`
- `yahoo`
- `baidu`
- `duckduckgo`
- `linkedin`
- `twitter`
- `virustotal`
- `netcraft`
- `dnsdumpster`
- `crtsh`
- and more.

### **Advanced Options**

- **Perform DNS Reverse Lookups:**
  ```bash
  theHarvester -d example.com -b google -n
  ```
  - The `-n` flag performs DNS reverse lookups.

- **Perform a DNS TLD Expansion:**
  ```bash
  theHarvester -d example.com -b google -t
  ```
  - The `-t` flag attempts to expand the domain name across multiple TLDs.

- **Use a Specific File Containing a List of Hosts:**
  ```bash
  theHarvester -d example.com -b google -e hosts.txt
  ```
  - The `-e` option allows you to input a file containing a list of hosts.

### **Full Help Menu**
To see all available options and commands, you can run:
```bash
theHarvester -h
```

### **Combining with Other Tools**
TheHarvester can be used in conjunction with other tools like `sublist3r`, `nmap`, or `dnsenum` to extend the reconnaissance phase and provide more comprehensive results.

---

This should give your students a good understanding of how to use TheHarvester for gathering information about a domain. They can experiment with different options and sources to get more detailed results.