# 🚨 Sticky Keys Privilege Escalation – Incident Analysis (DFIR Case Study)

## 📌 Overview

This repository documents a real-world incident involving **privilege escalation and lateral movement** through abuse of Windows accessibility features.

The attacker leveraged a **Living Off The Land (LOLBIN)** technique by replacing a legitimate system binary (`sethc.exe`) with `cmd.exe`, enabling SYSTEM-level command execution from the login screen.

---

## 🧠 Key Findings

* `sethc.exe` was replaced with `cmd.exe`
* Execution triggered via accessibility mechanism
* SYSTEM-level shell obtained
* Activity originated from internal host: **REDACTED_INTERNAL_IP**
* Remote access confirmed via **RDP (LogonType 10)**
* Detected by Microsoft Defender:

  * `Behavior:Win32/AccessibilityEscalation.AF`

---

## 🔬 Attack Flow

```text
[REDACTED_SOURCE]
   ↓
REDACTED_INTERNAL_IP
   ↓ (RDP)
REDACTED_PIVOT_HOST
   ↓
Sticky Keys Backdoor (sethc.exe → cmd.exe)
   ↓
SYSTEM Shell (conhost.exe)
```

---

## 🎯 MITRE ATT&CK Mapping

* T1546.008 – Accessibility Features
* T1036 – Masquerading

---

## 🚨 Impact

* Authentication bypass
* SYSTEM privilege execution
* Confirmed lateral movement
* Potential credential compromise

---

## 📂 Contents

* `timeline.md` → Event reconstruction
* `analysis.md` → Technical breakdown
* `detection.md` → Detection & mitigation
* `queries.md` → Defender KQL queries used

---

## ⚠️ Disclaimer

All sensitive information (IPs, hostnames, usernames) has been anonymized.

---

## 👨‍💻 Author

Blue Team / SOC Analyst (Aspiring DFIR Specialist)
