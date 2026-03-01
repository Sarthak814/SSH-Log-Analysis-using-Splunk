# SSH-Log-Analysis-using-Splunk

## 📌 Project Overview
This project demonstrates real-world SOC Level 1 skills by analyzing SSH logs using Splunk Enterprise.

#### The objective was to detect:
- Brute force attacks
- Multiple failed authentication attempts
- Successful SSH logins
- Connection attempts without authentication
- Suspicious source IP activity

This project simulates how a Security Operations Center (SOC) monitors and investigates SSH-based attacks.

## 🛠️ Tools Used:
- Splunk Enterprise
- SSH Log Dataset (JSON format)
- SPL (Search Processing Language)

## 📂 Data Source:
SSH log dataset: ssh_logs.json  
Logs ingested into Splunk index: ssh_logs

## 🔎 Detection Queries Used:
### 1️⃣ Count Events by Event Type
index="ssh_logs" source="ssh_logs.json"
| stats count by event_type

### 2️⃣ Failed SSH Login Attempts by Source IP
index="ssh_logs" source="ssh_logs.json" event_type="Failed SSH Login"
| stats count by id.orig_h

### 3️⃣ Multiple Failed Authentication Attempts
index="ssh_logs" source="ssh_logs.json" event_type="Multiple Failed Authentication Attempts"
| stats count by id.orig_h, id.resp_h

### 4️⃣ Successful SSH Logins
index="ssh_logs" source="ssh_logs.json" event_type="Successful SSH Login"
| stats count by id.orig_h, id.resp_h

### 5️⃣ Connection Without Authentication
index="ssh_logs" source="ssh_logs.json" event_type="Connection Without Authentication"
| stats count by id.orig_h

### 6️⃣ Time-Based Analysis
index="ssh_logs" source="ssh_logs.json" event_type="Connection Without Authentication"
| timechart count by id.orig_h

## 📊 Dashboard & Alerting:
Created visualizations (Column Charts).  
Built dashboards using Splunk Dashboard Studio.  
Configured alert for brute force detection.  
Alert type: Per-Result.  
Trigger condition: Based on multiple failed login attempts.  

## 🚨 Attack Detection Logic:
### Brute Force Pattern Identified When:
High number of failed login attempts from a single IP.  
Multiple failed authentication attempts across different hosts.  
Rapid login attempts within a short time window.  

## 🎯 Skills Demonstrated:
- Log Analysis
- SPL Query Writing
- Threat Detection
- Brute Force Identification
- Dashboard Creation
- Alert Configuration
- SOC Investigation Workflow

## 📈 Outcome:
Successfully simulated a SOC monitoring environment and detected suspicious SSH activity using Splunk.  
This project reflects practical SOC Level 1 Analyst skills and real-world SIEM investigation workflow.  

## 👨‍💻 Author
Sarthak Kurude  
Aspiring SOC Analyst | Cybersecurity Enthusiast
