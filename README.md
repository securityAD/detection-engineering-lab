# 🛡️ Detection Engineering Lab: Atomic Red Team + Splunk + Sigma

This project simulates real-world adversary techniques using [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team) and detects them via [Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) logs ingested into [Splunk Free](https://www.splunk.com/en_us/download/splunk-enterprise.html). Custom Sigma rules are written to map detections to MITRE ATT&CK techniques and validate SOC workflows.

---

## 📌 Goals

- Simulate adversary behavior mapped to MITRE ATT&CK using Atomic Red Team
- Collect and analyze logs with Splunk
- Write custom Sigma rules for each attack technique
- Demonstrate detection capability through dashboards, queries, and rule mapping
- Practice realistic SOC/detection engineering workflows

---

## 🧱 Lab Architecture


|  Windows 10 VM (Target)     |
|-----------------------------|
| - Sysmon (Event Logging)    |
| - Winlogbeat (Log shipper)  |
| - Atomic Red Team (TTPs)    |       
            
|       Splunk Free           |
|-----------------------------|
| - Dashboards                |
| - Detection queries         |
          
|      Sigma Rule Output      |
|-----------------------------|
| - MITRE Mapped              |
| - Reusable YAML format      |

---

## 🛠️ Tools Used

| Tool              | Purpose                            |
|------------------|-------------------------------------|
| Splunk Free       | Log aggregation & detection queries |
| Atomic Red Team   | Simulated adversary behavior        |
| Sysmon            | Windows telemetry collection        |
| Winlogbeat        | Ship logs to Splunk                 |
| Sigma             | Write portable detection rules      |
| MITRE ATT&CK      | Technique mapping & coverage plan   |

---

## 🧪 Simulated Techniques

| Technique ID | Name                            | Description                                |
|--------------|----------------------------------|--------------------------------------------|
| T1059        | Command and Scripting Interpreter | PowerShell execution                       |
| T1547        | Boot or Logon Autostart Execution | Registry run key persistence               |
| T1070.004    | Indicator Removal on Host         | Clearing Windows event logs                |
| T1027        | Obfuscated Files or Information   | Encoded PowerShell commands                |
| T1055        | Process Injection                 | Remote thread injection                    |

Each technique includes:
- Atomic Red Team test
- Associated log data (Sysmon event ID)
- Custom Splunk detection query
- Corresponding Sigma rule
- ATT&CK technique mapping

---

## ⚙️ Setup Instructions

### 1. Clone the repo and prepare your lab environment

```bash
git clone https://github.com/yourusername/detection-lab-sigma.git
````

### 2. Install and configure tools

* [ ] Install **Splunk Free** locally
* [ ] Spin up a **Windows 10 VM**
* [ ] Install **Sysmon** using a recommended config (e.g., SwiftOnSecurity)
* [ ] Install **Winlogbeat** and forward logs to Splunk
* [ ] Install **Atomic Red Team** and test execution

See `/setup/` for detailed guides.

---

## 🔍 Sample Detection

### Technique: PowerShell Execution (T1059)

**Atomic Test:**

```powershell
Invoke-Expression -Command "Get-Process"
```

**Splunk Query:**

```spl
index=winlogs EventCode=4104 Message="Invoke-Expression*" OR ScriptBlockText="*Get-Process*"
```

**Sigma Rule:**
`detections/t1059-powershell-execution.yml`

---

## 📊 Dashboards & Visuals

Screenshots and exported dashboards are available in `/dashboards/` and `/screenshots/`.
Example views:

* Suspicious PowerShell activity over time
* MITRE technique coverage heatmap
* Alert table from Sigma queries

---

## 🗂️ Folder Structure

```
.
├── detections/               # Sigma rules
├── splunk_queries/           # Raw SPL search queries
├── atomic_tests/             # TTP simulation notes
├── dashboards/               # Splunk visual exports
├── screenshots/              # Output for README/docs
├── setup/                    # Install/config guides
└── README.md
```

---

## 🧠 MITRE ATT\&CK Coverage

| Tactic               | Techniques Covered        |
| -------------------- | ------------------------- |
| Execution            | T1059 (PowerShell)        |
| Persistence          | T1547 (Registry Run Keys) |
| Defense Evasion      | T1070.004, T1027          |
| Privilege Escalation | T1055                     |

ATT\&CK Navigator JSON: [`mitre_coverage.json`](dashboards/mitre_coverage.json)

---

## 🧾 License

This project uses only open-source tools. Detection rules and Splunk content are shared under [MIT License](LICENSE).

---

## 🙌 Acknowledgments

* [Red Canary Atomic Red Team](https://github.com/redcanaryco/atomic-red-team)
* [Sigma Project](https://github.com/SigmaHQ/sigma)
* [SwiftOnSecurity Sysmon Config](https://github.com/SwiftOnSecurity/sysmon-config)
* MITRE ATT\&CK

---
