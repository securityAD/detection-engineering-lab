# Install Sysmon on Windows VM

[Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) provides deep telemetry about Windows behavior.

---

## 1. Download Sysmon & Sysinternals
- URL: https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon
- Extract it to `C:\Tools\Sysmon`

---

## 2. Download a Recommended Config
Use SwiftOnSecurity's maintained Sysmon config:

```powershell
Invoke-WebRequest -Uri https://raw.githubusercontent.com/SwiftOnSecurity/sysmon-config/master/sysmonconfig-export.xml -OutFile sysmonconfig.xml
```

## 3. Install Sysmon with Config

```
sysmon64.exe -accepteula -i sysmonconfig.xml
```
You should see:

> Sysmon installed and driver loaded

## 4. Confirm It’s Working
Check the Windows Event Viewer under:

- Applications and Services Logs > Microsoft > Windows > Sysmon > Operational

You should see logs starting with Event ID 1, 3, 10, etc.
