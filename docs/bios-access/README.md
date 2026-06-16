# BIOS Access Troubleshooting (Acer E5‑571)

This section documents the full process taken to access the BIOS on the Acer Aspire E5‑571‑3952 after being locked out of Windows 10. The laptop repeatedly booted straight into the Windows login screen, preventing normal BIOS entry.

1. Initial Problem
The Acer E5‑571 was:

Locked out of Windows 10 (password forgotten)

Booting directly to the Windows login screen

Ignoring BIOS hotkeys (F2, F12, ESC, DEL)

Not showing the Acer splash screen long enough to interrupt boot

This made normal BIOS access impossible.

2. Preparation Steps Taken
Before attempting BIOS access, the following were prepared:

✔ Downloaded Kali Linux 2026.1 ISO
From the official Kali Linux website.

✔ Downloaded Rufus 4.x
To create a bootable USB installer.

✔ Prepared a USB flash drive
Formatted and ready for imaging.

These steps were done on your HP EliteBook, because the Acer was inaccessible.

3. Creating the Bootable USB (Rufus)
Using Rufus:

Selected the Kali ISO

Set Partition scheme: GPT

Set Target system: UEFI (non‑CSM)

Set File system: FAT32

Clicked Start

Waited for the USB to finish imaging

This USB would later be used to force the Acer to boot into BIOS/UEFI.

4. First Attempts to Access BIOS
On the Acer E5‑571:

❌ Attempt 1 — Pressing F2 repeatedly
No response. Windows login appeared instantly.

❌ Attempt 2 — Pressing F12 repeatedly
Still no boot menu.

❌ Attempt 3 — Holding F2 while powering on
Still booted to Windows login.

❌ Attempt 4 — Holding F12 while powering on
No change.

❌ Attempt 5 — Using Shift + Restart (Windows recovery)
Not possible — locked out of Windows.

The system was effectively “BIOS‑locked” by fast boot behaviour.

5. Breakthrough: Using the USB to Interrupt Boot
Once the Kali USB was inserted:

✔ Powered off the Acer
✔ Inserted the USB
✔ Pressed F12 repeatedly
This time, the system hesitated long enough to show:

“Preparing Automatic Repair”  
→ then
“Please wait…”  
→ then
Acer logo with F2/F12 options

This was the first time the BIOS prompt appeared.

6. Accessing BIOS Successfully
With the USB inserted and timing improved:

Pressed F2 at the Acer splash screen

Successfully entered the InsydeH2O BIOS

Navigated to the Boot tab

Enabled F12 Boot Menu

Disabled Secure Boot

Moved USB HDD to the top of the boot order

This allowed the system to boot from the Kali USB installer.

7. Why This Worked
The Acer E5‑571 has:

Fast Boot enabled by default

A tendency to skip BIOS checks when Windows is present

A very short BIOS interrupt window

Legacy firmware behaviour (pre‑TPM era)

Inserting a bootable USB forces the firmware to re‑evaluate boot devices, slowing the boot process just enough to allow BIOS entry.

This is a known quirk of older Acer laptops.

8. Outcome
After adjusting BIOS settings:

F12 boot menu worked normally

USB boot was reliable

Kali Linux installer launched successfully

Windows 10 was wiped

The rebuild process continued without further BIOS issues

This step was essential to recovering the machine.
