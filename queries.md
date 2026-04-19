# 🔍 Defender Advanced Hunting Queries

## 🎯 1. Identify RDP Logins (LogonType 10)

```kql
DeviceLogonEvents
| where DeviceName == "REDACTED_HOSTNAME"
| where Timestamp between (datetime(2026-04-19 00:20:00) .. datetime(2026-04-19 00:30:00))
| where LogonType == "RemoteInteractive"
| project Timestamp, AccountName, RemoteIP
| order by Timestamp asc
```

---

## 🌐 2. Trace Activity from Suspicious IP

```kql
DeviceLogonEvents
| where RemoteIP == "REDACTED_INTERNAL_IP"
| project Timestamp, DeviceName, AccountName, LogonType
| order by Timestamp asc
```

---

## 🧠 3. Identify Host Associated with IP

```kql
DeviceNetworkEvents
| where RemoteIP == "REDACTED_INTERNAL_IP"
| distinct DeviceName
```

---

## 🔥 4. Process Execution on Pivot Host

```kql
DeviceProcessEvents
| where DeviceName == "REDACTED_HOSTNAME"
| where Timestamp between (datetime(2026-04-18 23:30:00) .. datetime(2026-04-19 01:00:00))
| project Timestamp, FileName, ProcessCommandLine, AccountName
| order by Timestamp asc
```

---

## 🌍 5. Network Connections from Pivot Host

```kql
DeviceNetworkEvents
| where DeviceName == "REDACTED_HOSTNAME"
| summarize count() by RemoteIP
| order by count_ desc
```

---

## 🧬 6. File Modifications (Persistence Detection)

```kql
DeviceFileEvents
| where DeviceName == "REDACTED_HOSTNAME"
| where ActionType in ("FileCreated","FileModified","FileRenamed")
| project Timestamp, FileName, FolderPath, InitiatingProcessFileName
| order by Timestamp asc
```

---

## 🔐 7. Privileged Account Activity

```kql
DeviceLogonEvents
| where AccountName contains "admin"
| project Timestamp, DeviceName, AccountName, RemoteIP
```
