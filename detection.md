# 🛡️ Detection & Mitigation

## 🔍 Detection Opportunities

### 1. Binary Integrity Monitoring

Monitor:

* sethc.exe
* utilman.exe
* osk.exe

---

### 2. Process Behavior

Alert if:

* `AtBroker.exe` → `cmd.exe`
* `sethc.exe` → `conhost.exe`

---

### 3. Suspicious Logons

* LogonType 10 (RDP) from unusual IPs
* Multiple hosts accessed by same IP

---

## 🛠️ Mitigation

* Restore system files:

  ```
  sfc /scannow
  ```
* Investigate pivot host
* Rotate credentials
* Monitor lateral movement

---

## 🔐 Hardening

* Restrict RDP access
* Monitor privileged accounts
* Enable EDR behavioral rules
