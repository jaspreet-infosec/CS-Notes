___

### **3.1 Introduction to Linux**

#### **What is Linux?**
- **Definition:** Linux is an open-source, Unix-like operating system kernel that serves as the foundation for a variety of operating systems known as distributions (distros). It is used in a wide range of devices, from personal computers to servers and embedded systems.
- **Kernel:** The core part of the OS that interacts directly with hardware and manages system resources.
- **Distributions (Distros):** Different versions of Linux that package the kernel with various software and utilities to suit different needs.

#### **Popular Linux Distributions**
- **Ubuntu:**
  - **Overview:** User-friendly, popular for desktops and servers.
  - **Features:** Large community support, extensive documentation, frequent updates.
  - **Example:** Ubuntu Desktop is widely used for general-purpose computing, while Ubuntu Server is used in data centers and cloud environments.

- **CentOS:**
  - **Overview:** Free and open-source, derived from Red Hat Enterprise Linux (RHEL).
  - **Features:** Stability and long-term support, suitable for enterprise environments.
  - **Example:** CentOS is often used in web hosting and enterprise server setups.

- **Debian:**
  - **Overview:** Known for its stability and extensive package repository.
  - **Features:** Conservative approach to package updates, used as a base for many other distros.
  - **Example:** Debian is used for servers and as a base for other distributions like Ubuntu.

- **Kali Linux:**
  - **Overview:** Specialized in penetration testing and security research.
  - **Features:** Pre-installed tools for security analysis and ethical hacking.
  - **Example:** Kali Linux is used by security professionals to perform vulnerability assessments and penetration tests.

#### **Linux Architecture**
- **Kernel:**
  - **Function:** Manages hardware resources, including CPU, memory, and I/O devices.
  - **Components:** Includes process management, memory management, device drivers, and system calls.
  - **Example:** The Linux kernel handles the execution of processes, memory allocation, and communication between hardware and software.

- **Shell:**
  - **Definition:** A command-line interface (CLI) that allows users to interact with the operating system.
  - **Common Shells:**
    - **Bash (Bourne Again Shell):** Default shell for many Linux distributions.
    - **Zsh (Z Shell):** Known for advanced features and customization.
  - **Example:** Using Bash to run commands and scripts, such as `ls` to list directory contents and `cd` to change directories.

- **File System:**
  - **Definition:** Organizes and manages files and directories on disk.
  - **Hierarchy:** Root directory (`/`) is the starting point of the file system hierarchy.
  - **Example:** The `/etc` directory contains configuration files for the system, while `/home` contains user directories.

- **Applications:**
  - **Definition:** Software programs that run on the Linux OS, including utilities, servers, and graphical applications.
  - **Example:** Web servers like Apache and file editors like `nano` are applications that run on Linux.

### **3.2 Linux Basics**

#### **Linux File System Structure**
- **Root Directory (`/`):**
  - **Description:** The top-level directory in the Linux file system hierarchy.
  - **Example:** All other directories are subdirectories of the root directory.

- **Important Directories:**
  - **`/home`:** Contains user home directories.
    - **Example:** `/home/user1` is the home directory for `user1`, where personal files and settings are stored.
  - **`/etc`:** Stores system-wide configuration files.
    - **Example:** `/etc/passwd` contains user account information.
  - **`/var`:** Contains variable data files such as logs and databases.
    - **Example:** `/var/log/syslog` contains system log messages.
  - **`/tmp`:** Used for temporary files.
    - **Example:** `/tmp` is often cleared on reboot, so it’s suitable for temporary storage.
  - **`/usr`:** Contains user utilities and applications.
    - **Example:** `/usr/bin` contains executable files for user commands.

#### **Basic Commands**

- **Navigating Directories:**
  - **`pwd`** (Print Working Directory): Shows the current directory path.
    - **Example:** `pwd` might output `/home/user` indicating that you are in the `user` directory.
  - **`ls`** (List): Lists files and directories.
    - **Example:** `ls -l` provides detailed information about files, including permissions, owner, size, and modification date.
  - **`cd`** (Change Directory): Changes the current directory.
    - **Example:** `cd /etc` changes to the `/etc` directory. `cd ..` moves up one directory level.

- **File and Directory Operations:**
  - **`cp`** (Copy): Copies files or directories.
    - **Example:** `cp file.txt /backup/` copies `file.txt` to the `/backup` directory.
  - **`mv`** (Move): Moves or renames files or directories.
    - **Example:** `mv oldname.txt newname.txt` renames `oldname.txt` to `newname.txt`.
  - **`rm`** (Remove): Deletes files or directories.
    - **Example:** `rm file.txt` deletes `file.txt`. Use `rm -r` to remove directories recursively.

- **File Permissions:**
  - **`chmod`** (Change Mode): Modifies file permissions.
    - **Example:** `chmod 755 script.sh` sets the permissions to read, write, and execute for the owner, and read and execute for others.
  - **`chown`** (Change Owner): Changes file ownership.
    - **Example:** `chown user:group file.txt` changes the owner of `file.txt` to `user` and the group to `group`.

#### **Text Editors**

- **`vi`/`vim` (Vi Improved):**
  - **Modes:**
    - **Command Mode:** Default mode where you can navigate and manipulate text.
    - **Insert Mode:** For editing text. Entered by pressing `i`.
  - **Basic Commands:**
    - **`i`**: Enter insert mode.
    - **`Esc`**: Return to command mode.
    - **`:wq`**: Save and exit.
    - **`:q!`**: Quit without saving.
  - **Example:** Open a file with `vi file.txt`, press `i` to enter insert mode, type text, press `Esc`, and save with `:wq`.

- **`nano`:**
  - **Overview:** A user-friendly text editor with a simpler interface compared to `vi`.
  - **Basic Commands:**
    - **`Ctrl+O`**: Write (save) the file.
    - **`Ctrl+X`**: Exit the editor.
    - **`Ctrl+K`**: Cut text.
  - **Example:** Open a file with `nano file.txt`, edit the file, and save it with `Ctrl+O` followed by `Ctrl+X` to exit.

### **3.3 Linux System Administration**

#### **User and Group Management**

- **Creating and Managing Users:**
  - **`useradd`**: Adds a new user.
    - **Example:** `useradd student` creates a new user named `student`.
  - **`passwd`**: Sets or changes user passwords.
    - **Example:** `passwd student` prompts for a new password for the `student` user.

- **Creating and Managing Groups:**
  - **`groupadd`**: Adds a new group.
    - **Example:** `groupadd students` creates a new group named `students`.
  - **`usermod`**: Modifies user account properties.
    - **Example:** `usermod -aG students student` adds the `student` user to the `students` group.

- **Listing Users and Groups:**
  - **`cat /etc/passwd`**: Lists user accounts.
    - **Example:** Shows user details such as username, UID, GID, home directory, and shell.
  - **`cat /etc/group`**: Lists groups.
    - **Example:** Shows group names, GIDs, and member usernames.

#### **Process Management**

- **Viewing Processes:**
  - **`ps`** (Process Status): Displays information about running processes.
    - **Example:** `ps aux` shows all processes with detailed information including user, PID, CPU and memory usage.
  - **`top`**: Provides a real-time view of system processes and resource usage.
    - **Example:** `top` displays CPU, memory usage, and running processes.

- **Managing Processes:**
  - **`kill`**: Terminates processes.
    - **Example:** `kill 1234` sends the SIGTERM signal to process ID `1234`. Use `kill -9 1234` to forcefully terminate the process.
  - **`pkill`**: Sends signals to processes based on their name.
    - **Example:** `pkill firefox` terminates all processes named `firefox`.

#### **Package Management**

- **Debian-Based Systems (e.g., Ubuntu):**
  - **`apt-get`**: Command-line tool for managing packages.
    - **Example:** `apt-get install

 nginx` installs the `nginx` package. `apt-get update` updates the package index.

- **Red Hat-Based Systems (e.g., CentOS):**
  - **`yum`**: Package management tool.
    - **Example:** `yum install httpd` installs the `httpd` package. `yum update` updates all installed packages.

### **3.4 Linux Networking Basics**

#### **Network Configuration and Tools**

- **`ifconfig`**: Configures and displays network interfaces (deprecated in favor of `ip`).
  - **Example:** `ifconfig -a` shows all network interfaces, including those that are inactive.

- **`ip`**: A more modern tool for managing network interfaces.
  - **Example:** `ip addr show` displays IP addresses and other details for network interfaces.

- **`ping`**: Tests network connectivity.
  - **Example:** `ping google.com` sends ICMP echo requests to `google.com` and displays responses, indicating whether the host is reachable.

- **`netstat`**: Displays network connections, routing tables, and interface statistics.
  - **Example:** `netstat -tuln` shows active TCP and UDP connections with their listening ports.

#### **Network Configuration Files**
- **`/etc/network/interfaces` (Debian-based systems):**
  - **Description:** Configuration file for network interfaces.
  - **Example:** Configuring a static IP address:
    ```bash
    auto eth0
    iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        gateway 192.168.1.1
    ```

- **`/etc/sysconfig/network-scripts/ifcfg-eth0` (Red Hat-based systems):**
  - **Description:** Configuration file for network interfaces.
  - **Example:** Configuring a static IP address:
    ```bash
    DEVICE=eth0
    BOOTPROTO=static
    IPADDR=192.168.1.100
    NETMASK=255.255.255.0
    GATEWAY=192.168.1.1
    ONBOOT=yes
    ```

### **3.5 Linux Security Basics**

#### **File and Directory Permissions**

- **Understanding Permissions:**
  - **Read (`r`):** Allows viewing the file contents.
  - **Write (`w`):** Allows modifying or deleting the file.
  - **Execute (`x`):** Allows running the file as a program.

- **Setting Permissions:**
  - **Numeric Mode:** Uses three digits to set permissions (owner, group, others).
    - **Example:** `chmod 755 script.sh` sets the permissions to `rwxr-xr-x`.
  - **Symbolic Mode:** Uses letters to set permissions.
    - **Example:** `chmod u+x file.txt` adds execute permission for the owner.

#### **Basic Security Practices**
- **Keep Software Updated:** Regular updates to the system and applications patch known vulnerabilities.
  - **Command:** `apt-get update && apt-get upgrade` (Debian-based) or `yum update` (Red Hat-based).

- **Configure Firewalls:**
  - **`iptables`:** Advanced firewall tool for configuring network traffic rules.
    - **Example:** `iptables -A INPUT -p tcp --dport 22 -j ACCEPT` allows incoming SSH traffic.
  - **`ufw` (Uncomplicated Firewall):** Simplified firewall configuration tool.
    - **Example:** `ufw allow 22/tcp` allows SSH traffic.

- **Use Strong Passwords:** Implement strong password policies and consider using tools like `passwd` for managing passwords.
  - **Command:** `passwd` to set or change a user password.

### **3.6 Practical Exercises**

#### **Exercise 1: Basic Navigation and File Operations**
- **Objective:** Practice navigating the file system and performing file operations.
- **Instructions:**
  - Navigate to the `/home` directory: `cd /home`.
  - Create a new directory named `testdir`: `mkdir testdir`.
  - Navigate into `testdir`: `cd testdir`.
  - Create a new file named `testfile.txt`: `touch testfile.txt`.
  - Edit the file using `nano testfile.txt`, add some text, and save.
  - Change the file’s permissions to be readable and writable only by the owner: `chmod 600 testfile.txt`.

#### **Exercise 2: User and Group Management**
- **Objective:** Practice creating and managing users and groups.
- **Instructions:**
  - Create a new user named `student`: `useradd student`.
  - Set a password for the `student` user: `passwd student`.
  - Create a new group named `students`: `groupadd students`.
  - Add the `student` user to the `students` group: `usermod -aG students student`.
  - Verify the user and group configurations by checking `/etc/passwd` and `/etc/group`.

#### **Exercise 3: Network Configuration**
- **Objective:** Practice configuring network settings and testing connectivity.
- **Instructions:**
  - Configure a static IP address on a virtual machine by editing `/etc/network/interfaces` or `/etc/sysconfig/network-scripts/ifcfg-eth0` depending on your distribution.
  - Restart the network service to apply changes: `systemctl restart networking` (Debian-based) or `systemctl restart network` (Red Hat-based).
  - Test network connectivity using `ping`: `ping google.com`.
  - Check network interface configurations with `ip addr show`.

---

## **Linux Commands** 
### **1. `ls`**
- **Description:** Lists files and directories in the current directory.
- **Example:** `ls -l` (Long format with permissions, ownership, and timestamps).

### **2. `cd`**
- **Description:** Changes the current directory.
- **Example:** `cd /home/user/Documents` (Changes to the Documents directory).

### **3. `pwd`**
- **Description:** Prints the current working directory.
- **Example:** `pwd` (Outputs something like `/home/user`).

### **4. `cp`**
- **Description:** Copies files or directories.
- **Example:** `cp file.txt /backup/` (Copies `file.txt` to the `/backup` directory).

### **5. `mv`**
- **Description:** Moves or renames files or directories.
- **Example:** `mv oldname.txt newname.txt` (Renames `oldname.txt` to `newname.txt`).

### **6. `rm`**
- **Description:** Removes files or directories.
- **Example:** `rm file.txt` (Deletes `file.txt`). Use `rm -r directory/` to remove a directory recursively.

### **7. `touch`**
- **Description:** Creates an empty file or updates the timestamp of an existing file.
- **Example:** `touch newfile.txt` (Creates `newfile.txt` if it doesn’t exist).

### **8. `mkdir`**
- **Description:** Creates a new directory.
- **Example:** `mkdir newdir` (Creates a directory named `newdir`).

### **9. `rmdir`**
- **Description:** Removes an empty directory.
- **Example:** `rmdir emptydir` (Removes the directory `emptydir` if it’s empty).

### **10. `cat`**
- **Description:** Concatenates and displays file contents.
- **Example:** `cat file.txt` (Displays the content of `file.txt`).

### **11. `more`**
- **Description:** Views the content of a file one screen at a time.
- **Example:** `more file.txt` (Displays `file.txt` one screen at a time).

### **12. `less`**
- **Description:** Views file contents with navigation options.
- **Example:** `less file.txt` (Displays `file.txt` with navigation features).

### **13. `head`**
- **Description:** Displays the first few lines of a file.
- **Example:** `head -n 10 file.txt` (Displays the first 10 lines of `file.txt`).

### **14. `tail`**
- **Description:** Displays the last few lines of a file.
- **Example:** `tail -n 10 file.txt` (Displays the last 10 lines of `file.txt`).

### **15. `find`**
- **Description:** Searches for files and directories.
- **Example:** `find /home/user -name "*.txt"` (Finds all `.txt` files in `/home/user`).

### **16. `grep`**
- **Description:** Searches for text within files.
- **Example:** `grep "search_term" file.txt` (Finds `search_term` in `file.txt`).

### **17. `chmod`**
- **Description:** Changes file permissions.
- **Example:** `chmod 755 script.sh` (Sets permissions to `rwxr-xr-x` for `script.sh`).

### **18. `chown`**
- **Description:** Changes file owner and group.
- **Example:** `chown user:group file.txt` (Changes the owner to `user` and the group to `group`).

### **19. `ps`**
- **Description:** Displays information about running processes.
- **Example:** `ps aux` (Shows detailed information about all running processes).

### **20. `top`**
- **Description:** Displays real-time system processes and resource usage.
- **Example:** `top` (Shows a live view of system processes and their resource consumption).

### **21. `kill`**
- **Description:** Sends signals to processes, usually to terminate them.
- **Example:** `kill 1234` (Sends the default `SIGTERM` signal to process with PID `1234`).

### **22. `pkill`**
- **Description:** Sends signals to processes by name.
- **Example:** `pkill firefox` (Terminates all processes with the name `firefox`).

### **23. `ifconfig`**
- **Description:** Configures network interfaces (deprecated in favor of `ip`).
- **Example:** `ifconfig eth0` (Displays information about the `eth0` network interface).

### **24. `ip`**
- **Description:** Shows and manipulates routing, devices, policy routing, and tunnels.
- **Example:** `ip addr show` (Displays IP addresses for all network interfaces).

### **25. `ping`**
- **Description:** Tests network connectivity.
- **Example:** `ping google.com` (Sends ICMP echo requests to `google.com`).

### **26. `netstat`**
- **Description:** Displays network connections, routing tables, and interface statistics.
- **Example:** `netstat -tuln` (Shows TCP and UDP connections with listening ports).

### **27. `wget`**
- **Description:** Downloads files from the web.
- **Example:** `wget http://example.com/file.txt` (Downloads `file.txt` from `example.com`).

### **28. `curl`**
- **Description:** Transfers data from or to a server.
- **Example:** `curl -O http://example.com/file.txt` (Downloads `file.txt` from `example.com`).

### **29. `tar`**
- **Description:** Archives files and directories.
- **Example:** `tar -czvf archive.tar.gz folder/` (Creates a compressed archive of `folder`).

### **30. `gzip`**
- **Description:** Compresses files.
- **Example:** `gzip file.txt` (Compresses `file.txt` to `file.txt.gz`).

---


