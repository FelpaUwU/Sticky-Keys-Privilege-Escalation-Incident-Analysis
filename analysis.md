# 🔬 Technical Analysis

## 🧩 Root Cause

The binary:

C:\Windows\System32\sethc.exe

was replaced with:

cmd.exe

This enabled execution of a SYSTEM shell via the Sticky Keys feature.

---

## ⚙️ Execution Flow

```text
winlogon.exe
   ↓
AtBroker.exe
   ↓
sethc.exe (modified → cmd.exe)
   ↓
conhost.exe
```

---

## 🔎 Key Observations

* `sethc.exe` hash matched `cmd.exe`
* Execution triggered with:

  ```
  sethc.exe /AccessibilitySoundAgent
  ```
* Interactive shell confirmed via `conhost.exe`
* Process executed under:

  * `NT AUTHORITY\SYSTEM`

---

## 🌐 Lateral Movement Evidence

* Remote IP observed: **REDACTED_INTERNAL_IP**
* Logon types observed:

  * Network (3)
  * RemoteInteractive (10)
* Indicates:

  * authentication + RDP session

---

## 🧠 Attack Interpretation

1. Attacker accessed pivot host via RDP
2. Used valid credentials
3. Executed commands to modify system binary
4. Established persistence via Sticky Keys
5. Attempted privileged execution (blocked by Defender)

---

## 🚨 Risk Assessment

Severity: **CRITICAL**

Capabilities gained:

* SYSTEM-level execution
* Authentication bypass
* Internal lateral movement
