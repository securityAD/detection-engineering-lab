# Install Atomic Red Team on Windows

Simulate adversary behavior using [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team).

---

## 1. Install Prerequisites
- PowerShell 5+
- .NET Framework 4.5+

---

## 2. Clone Atomic Red Team Repo

```powershell
git clone https://github.com/redcanaryco/invoke-atomicredteam.git
cd atomic-red-team
```

## 3. Install Invoke-AtomicRedTeam PowerShell Module

```
Install-Module -Name Invoke-AtomicRedTeam -Force
```

Import and test:

```
Import-Module .\invoke-atomicredteam.psd1
```

## 4. Configure Execution Environment
Atomic Red Team includes a helper script to prepare dependencies:

```
.\Invoke-AtomicTest T1059.001 -GetPrereqs
```

## 5. Run a Test

```
Invoke-AtomicTest T1059.001
```

> This executes a simulated PowerShell command execution (T1059)

Monitor Sysmon logs via Event Viewer or Splunk.
