# 🕵️‍♂️ Forensic Analysis Report: The Case of the Unstable Inspiron

**Status:** ✅ Case Closed (Root Cause Identified - Hardware Incompatibility/Fault)  
**Investigator:** Tahoora Kazi                                                                   
**System:** Dell Inspiron 7586 (Core i7 8th Gen)  
**Duration:** Multi-day diagnostic operation  

---

## 📖 Executive Summary
A Dell Inspiron 7586 exhibited critical instability, preventing reliable use of a USB Wi-Fi adapter.  
A full-scale digital and physical investigation was launched.  

The inquiry successfully rectified OS corruption and missing core drivers but ultimately determined the **root cause** to be a fundamental hardware-level incompatibility/fault between the host machine and the peripheral device, **beyond software remediation**.

---

## 🔬 Investigation Phases

### Phase 1: Peripheral Driver Acquisition and Deployment
- **Action:** Attempted installation of every available driver variant for the Realtek RTL8812BU chipset:
  - Official Realtek portal drivers  
  - Cudy manufacturer-specific drivers  
  - Community-vetted drivers from `morrownr` and `brektrou` GitHub repos
- **Result:** Consistent failure with errors:  
  `"Not connected"` → `"Unsupported OS"` → `"Forbidden by system policy"`

---

### Phase 2: Systemic Corruption & The Clean Slate
- **Action:** Executed advanced system utilities:
  - `chkdsk /f /r` → Found and repaired bad sectors  
  - `netsh winsock reset` & `ipconfig /flushdns` → Network stack repair attempts  
  - **Nuclear Option:** Windows 10 Reset (`Remove everything`)
- **Result:** File system instability fixed. Clean OS baseline established.

---

### Phase 3: The Hardware Autopsy
- **Action:** Physical inspection & model verification
  - Discovered loose SATA HDD caddy (not root cause)  
  - Identified true model via regulatory codes (`P76F001`) → Dell Inspiron 7586  
  - Inspected internal Wi-Fi card slot & antenna connectors
- **Result:** No visible physical damage. Correct machine identification achieved.

---

### Phase 4: Foundational Repair
- **Action:** Installed correct OEM drivers:
  - **Intel Chipset Device Software** → Fixed `PCI Device` & `SM Bus Controller` errors  
  - **Intel Rapid Storage Tech Driver** → Fixed `PCI Data Acquisition` errors  
  - **Killer Wi-Fi Driver** → Attempted internal Wi-Fi resolution
- **Result:** Cleared all yellow warning flags in Device Manager. System stable.

---

### Phase 5: Final Isolation & Conclusion
- **Action:** Cross-tested peripheral on a different machine
- **Result:** USB Wi-Fi adapter worked perfectly elsewhere  
- **Conclusion:** Root cause isolated to **hardware-level incompatibility/fault in host’s USB controller subsystem**.  

---

## 🧾 Evidence Table

| Hypothesis          | Test Performed | Result                           | Conclusion                   |
|---------------------|----------------|----------------------------------|------------------------------|
| Faulty Driver       | Multiple driver versions | Worked elsewhere, failed on host | ❌ Driver ruled out |
| OS Corruption       | `chkdsk`, Reset | Errors fixed, clean slate | ❌ OS instability ruled out |
| System Policy       | Disabled Driver Signature Enforcement | No change | ❌ Policy block ruled out |
| Incorrect Model     | Identified true model | Allowed correct drivers | ✅ Critical discovery |
| **Host Hardware Fault** | Cross-test on other PC | Adapter worked fine | ✅ ROOT CAUSE |

---

## 📚 Lessons Learned
1. **The 5 Whys is Law** → Digging deeper revealed hardware fault, not Wi-Fi driver.  
2. **Cross-Testing is Crucial** → Fastest way to isolate host-based issues.  
3. **Persistence Pays** → Driver repo hunting, registry tweaks, hardware inspection.  
4. **Knowing When to Stop** → Sometimes the answer is “replace hardware.”  

---

## ✅ Conclusion
The investigation was successful:  
- OS + driver corruption remediated  
- Root cause identified as **hardware-level incompatibility**  

**Recommendation:** Replace or bypass host USB controller; continue using adapter on alternate hardware.

---

## 📂 Project Notes
- 📸 *Screenshots Folder:* Insert Device Manager before/after screenshots  
- 📜 *Report:* This Markdown file (portfolio-ready)  
- 🛠️ *Tools Used:* `chkdsk`, `netsh`, `ipconfig`, Driver Store Explorer, OEM Drivers, GitHub Repos

---

**Tags:** `#DigitalForensics #HardwareDiagnostics #IncidentResponse #RootCauseAnalysis #ITOps`

---
