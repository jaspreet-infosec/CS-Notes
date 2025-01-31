Sure! Below is detailed documentation for each of the tools: Hashcat, theHarvester, Sublist3r, and Subfinder, including their installation, usage, and key commands.

---

# **1. Hashcat Documentation**

## **Overview**
Hashcat is a powerful password recovery tool that uses a GPU-based cracking technique. It supports numerous hash types and attack modes.

## **Installation**
### **On Linux:**
```bash
sudo apt-get update
sudo apt-get install hashcat
```

### **On Windows:**
1. Download the Hashcat binaries from the [official website](https://hashcat.net/hashcat/).
2. Extract the files and run `hashcat.exe` from the command line.

## **Usage**
### **Basic Syntax:**
```bash
hashcat -m [hash_mode] -a [attack_mode] -o [output_file] [hash_file] [wordlist]
```

### **Key Parameters:**
- `-m`: Specifies the hash type (e.g., `-m 0` for MD5, `-m 1000` for NTLM).
- `-a`: Specifies the attack mode:
  - `0`: Straight (dictionary) attack.
  - `1`: Combination attack.
  - `3`: Brute-force attack.
  - `6`: Hybrid Wordlist + Mask.
- `-o`: Specifies the output file for cracked passwords.
- `[hash_file]`: The file containing hashes to crack.
- `[wordlist]`: The file containing potential passwords (for dictionary attacks).

### **Examples:**
- **MD5 Hash with a Dictionary Attack:**
  ```bash
  hashcat -m 0 -a 0 -o cracked.txt hashes.txt rockyou.txt
  ```
- **NTLM Hash with a Brute-force Attack:**
  ```bash
  hashcat -m 1000 -a 3 -o cracked.txt hashes.txt ?a?a?a?a?a
  ```

### **Useful Commands:**
- **Show cracked passwords:**
  ```bash
  hashcat -m [hash_mode] --show [hash_file]
  ```
- **Benchmarking:**
  ```bash
  hashcat -b
  ```

---

# **2. theHarvester Documentation**

## **Overview**
theHarvester is an OSINT tool used to gather emails, subdomains, IPs, and URLs from different public data sources.

## **Installation**
### **On Linux:**
```bash
sudo apt-get update
sudo apt-get install theharvester
```

### **On Windows:**
1. Clone the repository:
   ```bash
   git clone https://github.com/laramies/theHarvester.git
   ```
2. Navigate to the directory:
   ```bash
   cd theHarvester
   ```
3. Install the dependencies:
   ```bash
   pip3 install -r requirements.txt
   ```

## **Usage**
### **Basic Syntax:**
```bash
theHarvester -d [domain] -b [data_source] -l [limit] -f [output_file]
```

### **Key Parameters:**
- `-d`: Specifies the domain to search.
- `-b`: Specifies the data source (e.g., google, bing, linkedin).
- `-l`: Limits the number of results.
- `-f`: Specifies the output file format (e.g., HTML, XML).

### **Examples:**
- **Gathering Emails from Google:**
  ```bash
  theHarvester -d anshinfotech.org -b google
  ```
- **Finding Subdomains using Bing:**
  ```bash
  theHarvester -d anshinfotech.org -b bing -l 500
  ```

### **Useful Commands:**
- **Search using all sources:**
  ```bash
  theHarvester -d anshinfotech.org -b all
  ```
- **Save results to a file:**
  ```bash
  theHarvester -d anshinfotech.org -b google -f report.html
  ```

---

# **3. Sublist3r Documentation**

## **Overview**
Sublist3r is a Python-based tool designed to enumerate subdomains of websites using OSINT. It helps in enumerating subdomains and domain reconnaissance.

## **Installation**
### **On Linux:**
1. Clone the repository:
   ```bash
   git clone https://github.com/aboul3la/Sublist3r.git
   ```
2. Navigate to the directory:
   ```bash
   cd Sublist3r
   ```
3. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```

### **On Windows:**
Follow the same steps as for Linux using Git Bash or any preferred terminal.

## **Usage**
### **Basic Syntax:**
```bash
python sublist3r.py -d [domain] -o [output_file] -v
```

### **Key Parameters:**
- `-d`: Specifies the domain to search.
- `-o`: Specifies the output file to save the results.
- `-v`: Enables verbose mode to display detailed output.

### **Examples:**
- **Find Subdomains for a Domain:**
  ```bash
  python sublist3r.py -d anshinfotech.org
  ```
- **Save Results to a File:**
  ```bash
  python sublist3r.py -d anshinfotech.org -o subdomains.txt
  ```

### **Useful Commands:**
- **Search with verbose output:**
  ```bash
  python sublist3r.py -d anshinfotech.org -v
  ```
- **Specify a specific search engine:**
  ```bash
  python sublist3r.py -d anshinfotech.org -e google
  ```

---

# **4. Subfinder Documentation**

## **Overview**
Subfinder is a fast and simple subdomain enumeration tool focused on accuracy. It is written in Go and can be used to discover subdomains for a target domain.

## **Installation**
### **On Linux:**
1. Install Go if it is not already installed:
   ```bash
   sudo apt-get install golang
   ```
2. Install Subfinder:
   ```bash
   go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
   ```
3. Add Subfinder to your PATH:
   ```bash
   export PATH=$PATH:~/go/bin
   ```

### **On Windows:**
1. Install Go from the official Go website.
2. Install Subfinder using the same steps as for Linux via the command prompt.

## **Usage**
### **Basic Syntax:**
```bash
subfinder -d [domain] -o [output_file] -v
```

### **Key Parameters:**
- `-d`: Specifies the domain to search.
- `-o`: Specifies the output file to save the results.
- `-v`: Enables verbose mode to display detailed output.

### **Examples:**
- **Find Subdomains for a Domain:**
  ```bash
  subfinder -d anshinfotech.org
  ```
- **Save Results to a File:**
  ```bash
  subfinder -d anshinfotech.org -o subdomains.txt
  ```

### **Useful Commands:**
- **Search with verbose output:**
  ```bash
  subfinder -d anshinfotech.org -v
  ```
- **Use specific sources:**
  ```bash
  subfinder -d anshinfotech.org -sources crtsh,shodan
  ```

---

**Note:** The above tools are powerful and widely used for cybersecurity and penetration testing tasks. Always ensure that you have proper authorization before using these tools on any network or domain. Unauthorized use can result in legal consequences.

If you have any further questions or need additional details, feel free to ask!