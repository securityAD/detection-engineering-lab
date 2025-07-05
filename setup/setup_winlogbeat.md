# Install Winlogbeat on Windows VM

Winlogbeat ships Windows event logs (including Sysmon) to Splunk via TCP/UDP or HTTP.

---

## 1. Download Winlogbeat
- URL: https://www.elastic.co/downloads/beats/winlogbeat
- Extract it to: `C:\Program Files\Winlogbeat`

---

## 2. Configure Winlogbeat (YAML)
Edit `winlogbeat.yml`:

```yaml
winlogbeat.event_logs:
  - name: Microsoft-Windows-Sysmon/Operational
    event_id: "*"

output.logstash:
  hosts: ["<your-host-ip>:5044"]

# Disable Elasticsearch output
output.elasticsearch:
  enabled: false
```
Replace <your-host-ip> with the IP of the host running Splunk.


## 3. Install as a Service
In PowerShell (Admin):

```
.\install-service-winlogbeat.ps1
Start-Service winlogbeat
```

4. Configure Splunk Input (Logstash-compatible)
Inside Splunk:

- Go to Settings > Data Inputs > TCP
- Create a new input on port 5044
- Source type: Winlogbeat
- Index: winlogs
