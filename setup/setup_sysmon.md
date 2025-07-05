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
