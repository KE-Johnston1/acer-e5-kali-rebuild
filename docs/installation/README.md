# Kali Linux Installation Process (Acer E5‑571)

This section documents the full installation process of Kali Linux 2026 on the Acer Aspire E5‑571‑3952. The installation followed successful BIOS access and USB boot repair.

---

## 1. Preparing the Installation Media

### ✔ Downloaded Kali Linux 2026 ISO
The latest stable ISO was downloaded from the official Kali Linux website.

### ✔ Downloaded Rufus (Windows)
Rufus was used on a separate laptop (HP EliteBook) to create the bootable USB.

### ✔ Created the Bootable USB
Rufus settings used:

- **Partition scheme:** GPT  
- **Target system:** UEFI (non‑CSM)  
- **File system:** FAT32  
- **Volume label:** KALI2026  
- **Write mode:** ISO mode (recommended)

The USB was successfully imaged and verified.

---

## 2. Booting the Acer from USB

After BIOS access was restored:

- Inserted the Kali USB  
- Pressed **F12** repeatedly  
- Selected the USB device from the boot menu  
- Confirmed that Secure Boot was disabled  
- Confirmed USB HDD was first in boot order  

The Acer successfully launched the Kali installer.

---

## 3. Starting the Installer

From the boot menu:

- Selected **Graphical Install**  
- Chose English (UK) as the language  
- Selected United Kingdom as the location  
- Set keyboard layout to UK  

The installer loaded without errors.

---

## 4. Network Configuration

### ✔ Skipped network setup  
Because Wi‑Fi drivers were not available at install time, and Ethernet was not connected.

Installer message:  
**“Network configuration failed — continue without network?”**  
→ Chose **Yes**.

This allowed the installation to proceed offline.

---

## 5. User Account Setup

The following details were entered:

- **Full name:**   
- **Username:** 
- **Password:** 

This created the primary user account.

---

## 6. Disk Partitioning

### ✔ Chose “Guided — use entire disk”  
Because the goal was to wipe Windows 10 completely.

### ✔ Selected the internal HDD  
The Acer’s 1000 GB HDD was chosen.

### ✔ Chose “All files in one partition”  
Simple layout suitable for a single‑user system.

### ✔ Confirmed partition changes  
This erased Windows 10 and prepared the disk for Kali.

---

## 7. Software Selection

During the package selection screen:

### ❌ First attempt  
Selecting multiple desktop environments caused an installation failure.

### ✔ Final successful attempt  
**Unselected everything** to install a minimal Kali system.

This allowed the installation to complete without errors.

---

## 8. GRUB Bootloader Installation

Installer prompt:  
**“Install GRUB to the primary drive?”**

### ✔ Selected: Yes  
### ✔ Target device: `/dev/sda`

This ensured the system would boot into Kali after installation.

---

## 9. Completing the Installation

After GRUB installation:

- Installer completed successfully  
- System rebooted  
- Kali Linux booted into the login screen  
- Logged in as user ** 
- Verified system functionality  

This marked the successful completion of the OS rebuild.

---

## 10. Post‑Install Verification

After first boot:

- Ran `sudo apt update` (after network setup planned for later)  
- Verified disk layout with `lsblk`  
- Checked system info with `lshw -short`  
- Confirmed GRUB was functioning  
- Confirmed the system booted reliably  

The Acer E5‑571 was now fully running Kali Linux 2026.

---

## 🧠 Notes

- Wi‑Fi setup will be added later due to Broadcom chipset issues.  
- Additional tools and configurations are documented in the **post-install** section.  
- This installation was completed in approximately **5 hours**, including troubleshooting.  

