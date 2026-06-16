# Rebuild Process Notes

These notes document the real, practical steps taken during the rebuild of the Acer Aspire E5‑571‑3952. They reflect the decisions, challenges, research, and learning that occurred throughout the process. This section is intentionally written in a narrative, chronological style to show the thinking behind each action.

---

## 1. Planning & Preparation (Approx. 2 hours)

Before touching the Acer laptop, I planned the rebuild:

- Assessed the hardware limitations (no TPM, older CPU, legacy BIOS)
- Confirmed Windows 11 was not an option
- Decided to replace Windows 10 entirely due to forgotten password
- Chose Kali Linux because:
  - It runs well on older hardware
  - No TPM requirement
  - Ideal for cybersecurity learning
  - Lightweight and open‑source
- Verified that my HP EliteBook did not have enough disk space for VMs
- Decided to repurpose the Acer as a dedicated Linux machine

This planning stage ensured that every step had a clear purpose.

---

## 2. Downloading Tools & Preparing the USB

On the HP EliteBook:

- Downloaded **Kali Linux 2026 ISO**
- Downloaded **Rufus**
- Prepared a USB flash drive
- Used Rufus with:
  - GPT partition scheme
  - UEFI (non‑CSM)
  - FAT32 filesystem
- Successfully created the bootable USB

This USB would later be used to interrupt the Acer’s fast boot behaviour.

---

## 3. First Attempts to Access BIOS (Failed Attempts)

On the Acer E5‑571:

- Pressed **F2** repeatedly → ignored  
- Pressed **F12** repeatedly → ignored  
- Held F2 while powering on → still booted to Windows login  
- Held F12 while powering on → no change  
- Could not use Windows recovery due to forgotten password  

The laptop was effectively “BIOS‑locked” by fast boot.

---

## 4. Breakthrough: Using the USB to Slow Boot

Inserted the Kali USB and rebooted:

- Pressed **F12** repeatedly  
- System hesitated long enough to show the Acer splash screen  
- BIOS prompt finally appeared  
- Entered BIOS successfully  

This confirmed that the USB forced the firmware to re‑evaluate boot devices.

---

## 5. BIOS Configuration

Inside the InsydeH2O BIOS:

- Enabled **F12 Boot Menu**
- Disabled **Secure Boot**
- Set USB HDD as first boot device
- Saved changes and rebooted

The Acer now recognised the USB and allowed booting into the Kali installer.

---

## 6. Installation Process (Approx. 1 hour)

- Booted from USB
- Selected **Graphical Install**
- Skipped Wi‑Fi setup (no drivers)
- Created user account
- Chose **Guided – use entire disk**
- Wiped Windows 10 completely
- Installed a minimal Kali system (no desktop environment)
- Installed GRUB to `/dev/sda`
- Rebooted into Kali successfully

This completed the OS migration.

---

## 7. First Boot & Offline Checks

Without Wi‑Fi:

- Verified disk layout (`lsblk`, `fdisk -l`)
- Checked hardware (`lshw -short`)
- Reviewed logs (`dmesg`, `journalctl -b`)
- Confirmed GRUB was working
- Identified missing Broadcom Wi‑Fi firmware

System was stable but offline.

---

## 8. Bringing the System Online (Ethernet)

To continue setup:

- Connected Ethernet cable
- Ran `sudo dhclient eth0`
- Confirmed connectivity with `ping google.com`
- Updated the system:
sudo apt update && sudo apt upgrade -y
- Installed essential tools:
- htop, neofetch, sysstat
- nmap, net-tools, tcpdump
- git, curl, wget
- kali-tools-top10

This transformed the system from “fresh install” to “fully functional”.

---

## 9. Using AI & Online Research

Throughout the rebuild:

- Used AI assistance to validate steps
- Looked up BIOS behaviour for Acer E5‑571
- Confirmed Rufus settings for UEFI systems
- Researched Broadcom Wi‑Fi issues
- Verified commands before running them
- Cross‑checked solutions with multiple sources

This ensured accuracy and reduced mistakes.

---

## 10. Time Taken

- **Planning:** ~2 hours  
- **Rebuild process:** ~5 hours  
- **Total:** ~7 hours  

This includes troubleshooting, installation, updates, and documentation.

---

## 11. Skills Demonstrated

- BIOS troubleshooting  
- USB boot repair  
- OS installation  
- Hardware evaluation  
- Network configuration  
- Linux command‑line usage  
- System verification  
- Documentation  
- Research & problem‑solving  
- Using AI as a technical assistant  

These are core skills for IT Support and entry‑level cybersecurity roles.

---

## 12. Lessons Learned

- Legacy hardware requires patience and experimentation  
- Fast Boot can block BIOS access  
- USB boot can be used to interrupt firmware  
- Ethernet is essential when Wi‑Fi drivers are missing  
- Minimal installs are ideal for older machines  
- Documentation helps track progress and learning  
- AI tools accelerate troubleshooting when used correctly  

This rebuild was both a practical exercise and a learning experience.


