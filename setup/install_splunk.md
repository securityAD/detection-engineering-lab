# Install Splunk Free (Local)

This guide helps you install Splunk Enterprise (Free License up to 500MB/day) for local lab testing.

---

## 1. Download Splunk Enterprise
- Go to: https://www.splunk.com/en_us/download/splunk-enterprise.html
- Choose the **Windows** or **Linux** installer (based on your host machine)
- Sign up for a free account if needed

---

## 2. Install Splunk
- Run the installer
- Set an admin username/password
- Accept default ports (8000 for web UI, 8089 for API)

---

## 3. Start Splunk
- Open your browser and go to: `http://localhost:8000`
- Log in with your admin credentials

---

## 4. Configure Splunk Inputs
Later, we will configure **Winlogbeat** to forward Sysmon logs to Splunk on port `5044`. No input needs to be created yet — we’ll handle that from the beats config.

---
