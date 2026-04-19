# ⏱️ Incident Timeline

| Time     | Event                                       |
| -------- | ------------------------------------------- |
| 00:24:31 | Network logon detected                      |
| 00:24:36 | RemoteInteractive (RDP) session established |
| 00:28:32 | `AtBroker.exe` executed                     |
| 00:28:32 | `sethc.exe` triggered (modified)            |
| 00:28:32 | `cmd.exe` executed (via masquerading)       |
| 00:28:32 | `conhost.exe` spawned                       |
| 00:28:32 | Defender detects and terminates activity    |

---

## 🌐 Context

* Source IP: **REDACTED_INTERNAL_IP**
* Execution context: SYSTEM
