# USB Boot Repair (Acer E5‑571)

This section documents the troubleshooting steps taken to repair USB boot functionality on the Acer Aspire E5‑571‑3952. The laptop initially refused to boot from USB due to BIOS settings, fast boot behaviour, and Secure Boot restrictions.

---

## 1. Initial Problem

Before repair, the Acer E5‑571:

- Ignored USB devices during startup  
- Skipped the Acer splash screen  
- Booted straight into the Windows 10 login screen  
- Did not respond to **F12** (Boot Menu)  
- Did not respond to **F2** (BIOS Setup)  
- Showed no indication that the USB was detected  

This made USB boot impossible.

---

## 2. Verifying the USB Installer

The USB was created on another machine (HP EliteBook) using Rufus with:

- **ISO:** Kali Linux 2026  
- **Partition scheme:** GPT  
- **Target system:** UEFI (non‑CSM)  
- **File system:** FAT32  
- **Write mode:** ISO mode  

The USB was confirmed to be valid and bootable.

---

## 3. First Attempts to Boot from USB (Failed)

On the Acer:

- Inserted USB → system ignored it  
- Pressed **F12** repeatedly → no boot menu  
- Pressed **F2** repeatedly → no BIOS access  
- Held F12 while powering on → still booted to Windows  
- Tried different USB ports → no change  

The system was locked into a fast‑boot loop.

---

## 4. Breakthrough: USB Slows Down Firmware

Inserting the bootable USB caused the firmware to:

- Pause briefly  
- Display the Acer splash screen  
- Show the **F2** and **F12** prompts  

This was the first time BIOS access became possible.

This behaviour is common on older Acer laptops — a bootable USB forces the firmware to re‑evaluate boot devices, slowing the boot process enough to allow key interrupts.

---

## 5. Accessing the Boot Menu

Once the splash screen appeared:

- Pressed **F12** repeatedly  
- Boot menu appeared  
- USB device was listed as **USB HDD**  
- Selected **USB HDD**  
- System attempted to boot from USB  

However, Secure Boot blocked the unsigned Kali installer.

---

## 6. Fixing BIOS Settings

Entered BIOS using **F2** and changed the following:

### ✔ Enabled F12 Boot Menu  
**Main → F12 Boot Menu → Enabled**

### ✔ Disabled Secure Boot  
**Boot → Secure Boot → Disabled**

If Secure Boot was greyed out:

- Set a temporary Supervisor Password  
- Returned to Boot tab  
- Secure Boot became editable  

### ✔ Changed Boot Order  
**Boot → Boot Priority Order**

Moved:

1. **USB HDD** (Kali USB)  
2. HDD / Windows Boot Manager  
3. Everything else  

Saved changes with **F10**.

---

## 7. Successful USB Boot

After BIOS repair:

- Rebooted  
- Pressed **F12**  
- Selected **USB HDD**  
- Kali Linux installer loaded successfully  
- Chose **Graphical Install**  

This confirmed that USB boot functionality was fully restored.

---

## 8. Why USB Boot Failed Originally

The Acer E5‑571 has several quirks:

- **Fast Boot** skips USB checks  
- **Secure Boot** blocks unsigned installers  
- **F12 Boot Menu** is disabled by default  
- BIOS interrupt window is extremely short  
- Windows Boot Manager takes priority  

These combined to prevent USB boot until BIOS settings were corrected.

---

## 9. Outcome

After repairing USB boot:

- The Acer successfully launched the Kali installer  
- Windows 10 was wiped  
- Kali Linux 2026 was installed  
- The system now boots reliably from GRUB  
- USB boot remains functional for future maintenance  

This step was essential to recovering and repurposing the laptop.
