
**Wapiti** is a web application vulnerability scanner that audits the security of web applications by performing "black-box" testing. It acts like a fuzzer by injecting payloads into the web application to discover potential vulnerabilities. Wapiti does not audit the source code of the web application but looks for security weaknesses from an external viewpoint by interacting with the application.

### **Features of Wapiti**
- **Supported Vulnerabilities**:
  - SQL Injection
  - Cross-Site Scripting (XSS)
  - Local and Remote File Inclusion (LFI/RFI)
  - CRLF Injection
  - Command Execution Detection
  - Directory Traversal
  - CSRF, SSRF, Open Redirect
  
- **Report Generation**: Wapiti generates reports in various formats such as HTML, XML, JSON, and more.

---

### **Installation of Wapiti**

To install Wapiti on your system, follow these steps based on your OS:

#### **Debian/Ubuntu Installation**:
```bash
sudo apt update
sudo apt install wapiti
```

#### **RHEL/CentOS Installation**:
You need to install Wapiti manually using `pip` (Python's package installer):
```bash
sudo yum install python3-pip
pip3 install wapiti3
```

#### **From GitHub Source**:
You can also install Wapiti by cloning the GitHub repository.
```bash
git clone https://github.com/wapiti-scanner/wapiti.git
cd wapiti
pip3 install -r requirements.txt
```

---

### **Basic Usage and Commands**

Once installed, you can use Wapiti to scan web applications by using a variety of commands and options.

#### **Basic Scan**

To perform a basic scan of a web application, use the following command:
```bash
wapiti -u http://www.example.com
```
- **Explanation**:
  - `-u`: Specifies the target URL.
  
This command will scan the target website for vulnerabilities using default settings.

#### **Generate Report**

To generate a report after the scan is completed:
```bash
wapiti -u http://www.example.com -f html -o /path/to/report.html
```
- **Explanation**:
  - `-f`: Format of the report (available formats: html, json, xml, txt).
  - `-o`: Specifies the output path for the report.

#### **Verbose Mode**

To get detailed information while scanning:
```bash
wapiti -u http://www.example.com -v 2
```
- **Explanation**:
  - `-v`: Verbosity level (0 = silent, 1 = normal, 2 = verbose).
  
#### **Attack Modules**

Wapiti allows you to specify which attack modules to run or exclude during the scan.

- **Run specific attack modules**:
  ```bash
  wapiti -u http://www.example.com --attack sql,xss
  ```
  - **Explanation**:
    - `--attack`: Specifies the attack modules to use (comma-separated list). In this example, only SQL Injection and XSS checks will be performed.

- **Exclude specific attack modules**:
  ```bash
  wapiti -u http://www.example.com --skip xss,crlf
  ```
  - **Explanation**:
    - `--skip`: Excludes certain attack modules from the scan (XSS and CRLF injections are skipped).

#### **Session Management (Authentication)**

If the web application requires authentication (e.g., login forms), Wapiti supports session handling:

- **Login using POST data**:
  ```bash
  wapiti -u http://www.example.com --post-login "http://www.example.com/login.php" --data "username=admin&password=admin"
  ```
  - **Explanation**:
    - `--post-login`: URL of the login form.
    - `--data`: Specifies the form data for authentication (in this case, username and password).

#### **Custom Headers**

You can specify custom HTTP headers if needed (for example, adding custom User-Agent or cookies):
```bash
wapiti -u http://www.example.com --header "User-Agent: CustomAgent" --cookie "sessionid=123456"
```
- **Explanation**:
  - `--header`: Adds a custom HTTP header.
  - `--cookie`: Passes a cookie for session management.

#### **Proxy Support**

Wapiti supports scanning through a proxy, which is useful for intercepting traffic or bypassing network restrictions.
```bash
wapiti -u http://www.example.com --proxy http://127.0.0.1:8080
```
- **Explanation**:
  - `--proxy`: Sets the proxy address (in this case, localhost at port 8080).

---

### **Advanced Usage**

#### **Time Delay Between Requests**

You can introduce a delay between each HTTP request to avoid being blocked by the web server:
```bash
wapiti -u http://www.example.com --timeout 5
```
- **Explanation**:
  - `--timeout`: Specifies the delay (in seconds) between requests.

#### **Restricting Scan Scope**

You can limit the scan to certain directories or exclude specific URLs:
```bash
wapiti -u http://www.example.com --scope url --exclude "http://www.example.com/logout"
```
- **Explanation**:
  - `--scope`: Restricts the scan to URLs with the same base URL (hostname).
  - `--exclude`: Excludes the given URL (e.g., the logout page) from the scan.

#### **Setting the Maximum Depth**

By default, Wapiti follows links on the target website. You can control how deep it should go:
```bash
wapiti -u http://www.example.com --max-depth 3
```
- **Explanation**:
  - `--max-depth`: Limits how many levels of links Wapiti will follow (e.g., 3 levels deep).

---

### **Example of Full Scan with Custom Options**

Here’s an example of a full scan with authentication, custom headers, and report generation:
```bash
wapiti -u http://www.example.com --post-login "http://www.example.com/login.php" --data "username=admin&password=admin" \
--header "User-Agent: WapitiScanner" --scope page --timeout 3 --attack sql,xss --format html -o /path/to/report.html
```
- **Explanation**:
  - This command logs into the application, sends custom headers, restricts the scan scope to individual pages, limits the timeout between requests to 3 seconds, runs SQL Injection and XSS tests, and generates an HTML report.

---
