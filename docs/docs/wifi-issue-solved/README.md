# Wi‑Fi Issue Solved

This document records how the Wi‑Fi issue on the Acer Aspire E5‑571‑3952 was ultimately resolved. Although the system initially appeared to have a Broadcom driver problem, the final fix turned out to be much simpler than expected.

---

## What Happened

After completing the Kali Linux installation and initial post‑install setup, the Wi‑Fi interface was not appearing. This suggested a potential Broadcom firmware or driver issue, which is common on older Acer laptops.

Before diving into deeper troubleshooting, I decided to take a step back.

---

## Steps Taken

1. **Shut the laptop down completely**  
   Not a reboot — a full power‑off to reset hardware state.

2. **Disconnected the Ethernet cable**  
   Ensured the system would not default to wired networking.

3. **Walked away and took a short break**  
   Allowed myself to reset mentally and avoid overthinking the issue.

4. **Powered the laptop back on**  
   Logged in normally.

5. **Clicked the Wi‑Fi icon**  
   This time, available networks appeared immediately.

6. **Selected my home network and re‑entered the password**  
   The connection succeeded without errors.

---

## Why This Worked

A full shutdown resets:

- the Wi‑Fi chipset  
- NetworkManager’s connection state  
- cached DHCP information  
- any temporary firmware initialisation issues  

On older hardware, especially Broadcom‑based systems, a cold boot can be enough to trigger proper driver loading.

---

## Outcome

Wi‑Fi is now fully functional with no additional drivers or configuration required.

This confirmed that the system was working correctly and that the issue was related to initial hardware state rather than missing firmware.

---

## Key Takeaway

Sometimes the simplest troubleshooting step is the most effective:

> **Turn it off, disconnect everything, walk away, and turn it back on.**

This experience reinforced the value of stepping back, resetting the system, and approaching the problem with a clear mind.
