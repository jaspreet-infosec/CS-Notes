# 🐉 Kali Linux Installation Guide (VMware & VirtualBox)

## 📌 Introduction
Kali Linux is a Debian-based Linux distribution widely used for **Cybersecurity, Ethical Hacking, VAPT, Digital Forensics, and SOC operations**.  
It comes pre-installed with **600+ security tools** such as Nmap, Metasploit, Burp Suite, and Wireshark.

---

## 💻 System Requirements
**Minimum:**
- RAM: 4 GB (8 GB recommended)
- CPU: Intel/AMD (Virtualization enabled)
- Disk Space: 40–60 GB
- OS: Windows / Linux / macOS
- BIOS: VT-x / AMD-V enabled

---

## 🔧 Virtualization Software
- VMware Workstation Player  
  https://www.vmware.com/products/workstation-player.html

- Oracle VirtualBox  
  https://www.virtualbox.org/wiki/Downloads

---

# 🔽 Kali Linux Download Methods

1. ISO File (Manual Installation)  
2. Pre-Built Virtual Image (Recommended)

---

## 🟢 Method 1: Installing Kali Linux Using ISO File

### 📥 Download Kali Linux ISO
https://www.kali.org/get-kali/#kali-installer

**ISO Options:**
- Installer (Recommended)
- Live
- Everything (Offline)

---

### 🖥️ Installation Steps (VMware & VirtualBox)

1. Create a new Virtual Machine  
2. Select Installer Disc Image (ISO)  
3. OS Type: Linux → Debian (64-bit)  
4. RAM: 4–8 GB | CPU: 2–4 cores  
5. Disk: 40–60 GB (Dynamic)

**Installation Flow:**
- Graphical Install
- Language, Location, Keyboard
- User & Password setup
- Guided disk → Entire disk → One partition
- Install GRUB → Reboot

---

## 🟢 Method 2: Installing Kali Linux Using Virtual Image

### 📥 Download Kali VM Images
https://www.kali.org/get-kali/#kali-virtual-machines

| Platform | File |
|--------|------|
| VMware | .vmx |
| VirtualBox | .ova |

---

### 🖥️ VMware (VMX)
- Extract ZIP
- Open VMware → Open VM
- Select .vmx file
- Start VM

```
Username: kali
Password: kali
```

---

### 🖥️ VirtualBox (OVA)
- File → Import Appliance
- Select .ova
- Import → Start VM

```
Username: kali
Password: kali
```

---

## ⚙️ Post Installation
```bash
sudo apt update && sudo apt upgrade -y
```

(Optional)
```bash
sudo apt install kali-linux-large -y
```

---

## 🛠️ Common Issues

| Issue | Fix |
|-----|-----|
| 64-bit missing | Enable virtualization in BIOS |
| Black screen | Increase VRAM |
| Slow VM | Increase RAM/CPU |
| No internet | Network → NAT |

---

## 🎯 Recommendation
- Workshops / Beginners → Virtual Image
- Academic / Learning → ISO Installer

---

## 📚 References
- https://www.kali.org/
- https://www.kali.org/docs/
