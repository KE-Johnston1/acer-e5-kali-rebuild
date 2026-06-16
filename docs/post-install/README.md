# Post‑Install Configuration (Kali Linux 2026)

This section documents the steps taken immediately after the first successful boot into Kali Linux on the Acer Aspire E5‑571‑3952. Because the installation was completed offline (no Wi‑Fi drivers available), the initial configuration focused on system verification, hardware checks, and preparing the machine for future setup.

---

## 1. First Boot Verification

After installation completed and the system rebooted:

- GRUB loaded successfully  
- Kali Linux booted without errors  
- Login screen appeared normally  
- Logged in using the user account created during installation  

This confirmed that the installation was stable and the bootloader was correctly installed.

---

## 2. Basic System Checks

With no network connection available, the following offline checks were performed:

### ✔ Checked disk layout  
lsblk
fdisk -l
Confirmed:
- `/dev/sda1` → EFI partition  
- `/dev/sda2` → main Kali partition  
- Correct partition sizes  
- No leftover Windows partitions  

### ✔ Checked hardware summary  
sudo lshw -short

Verified:
- CPU detected correctly  
- RAM recognised  
- Storage device healthy  
- No critical hardware missing  

### ✔ Checked boot logs  
sudo dmesg | less
sudo journalctl -b
Looked for:
- driver errors  
- filesystem warnings  
- boot delays  
- missing firmware messages  

This helped identify that the Wi‑Fi chipset required additional firmware (to be added later).

---

## 3. Desktop Environment & Usability

Because the installation was minimal (no desktop environment selected):

- The system booted into a lightweight Kali environment  
- No unnecessary packages were installed  
- System performance was stable on legacy hardware  

This minimal setup is ideal for older machines like the E5‑571.

---

## 4. Preparing for Future Network Setup

Since Wi‑Fi was not functional yet, the following steps were planned:

- Identify the Broadcom chipset using:
lspci | grep -i network
- Check for missing firmware in:
dmesg | grep -i firmware
- Plan to install `broadcom-sta-dkms` or `firmware-brcm80211` once network access is available  
- Consider temporary Ethernet connection for package installation  

These steps will be documented in the future **Wi‑Fi Setup** section.

---

## 5. System Update (Deferred)

Normally, the next step would be:
sudo apt update && sudo apt upgrade

However, because the system was offline, updates were postponed until Wi‑Fi or Ethernet connectivity is restored.

---

## 6. Post‑Install Observations

- The system booted reliably after installation  
- No GRUB issues were encountered  
- Performance was acceptable for a 2014‑era laptop  
- The minimal install kept resource usage low  
- All core hardware (CPU, RAM, storage, display) worked correctly  
- Only Wi‑Fi required additional troubleshooting  

---

## 7. Next Steps (Planned)

- Install Wi‑Fi drivers  
- Update the system fully  
- Install essential tools (htop, neofetch, git, etc.)  
- Configure security tools  
- Add screenshots and logs as troubleshooting progresses  
- Begin writing scripts for automation  

These will be added to the repository as the rebuild continues.

## 8. Bringing the System Online (Ethernet)

Because the Acer E5‑571 uses a Broadcom Wi‑Fi chipset that requires additional firmware, the system initially had no wireless connectivity. To continue setup, an Ethernet cable was connected directly to the laptop.

Once connected:
sudo dhclient eth0

This successfully obtained an IP address from the router and brought the system online.

Network connectivity was confirmed with:
ping -c 3 google.com

After confirming internet access, full system updates and package installations were performed.

---

## 9. Updating the System

With Ethernet active, the system was updated:
sudo apt update
sudo apt upgrade -y

This ensured the installation was fully patched and ready for tool installation.

---

## 10. Installing Essential Tools

Once online, the following tools were installed to prepare the system for practical use:

### ✔ System Monitoring & Diagnostics
sudo apt install htop neofetch sysstat -y

### ✔ Networking Tools
sudo apt install nmap net-tools tcpdump traceroute -y

### ✔ Development & Utility Tools
sudo apt install git curl wget build-essential -y

### ✔ Security Tools (Top 10)
sudo apt install kali-tools-top10 -y

### ✔ Desktop Environment (if installed later)
sudo apt install kali-desktop-xfce -y


These tools provided a complete working environment for IT support tasks, troubleshooting, and cybersecurity learning.

---

## 11. Post‑Install Verification (After Updates)

After updates and tool installation:

- Verified system performance  
- Confirmed all installed tools were functional  
- Checked logs for errors  
- Confirmed GRUB still booted correctly  
- Ensured Ethernet remained stable  

The system was now fully operational except for Wi‑Fi, which will be documented in a future update.
