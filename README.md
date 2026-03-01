# SSH-Log-Analysis-using-Splunk

## 📌 Project Overview
This project demonstrates real-world SOC Level 1 skills by analyzing SSH logs using Splunk Enterprise.<img width="1918" height="900" alt="1 login" src="https://github.com/user-attachments/assets/f5898654-61ee-4250-b015-38ac3e56c43a" />


#### The objective was to detect:
- Brute force attacks
- Multiple failed authentication attempts
- Successful SSH logins
- Connection attempts without authentication
- Suspicious source IP activity

This project simulates how a Security Operations Center (SOC) monitors and investigates SSH-based attacks.<img width="1902" height="912" alt="3 raw logs" src="https://github.com/user-attachments/assets/ae9ef9a4-c016-4a64-a319-14cf8563d9e7" />


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
| stats count by event_type<img width="1913" height="701" alt="4 event type" src="https://github.com/user-attachments/assets/8f30d4be-aaf2-40e3-aef9-8f0d7ae40054" />


### 2️⃣ Failed SSH Login Attempts by Source IP
index="ssh_logs" source="ssh_logs.json" event_type="Failed SSH Login"
| stats count by id.orig_h<img width="1900" height="899" alt="5 failed login status" src="https://github.com/user-attachments/assets/b4481922-11ca-4bf4-892a-fb065e6cb33b" />


### 3️⃣ Multiple Failed Authentication Attempts
index="ssh_logs" source="ssh_logs.json" event_type="Multiple Failed Authentication Attempts"
| stats count by id.orig_h, id.resp_h<img width="1892" height="911" alt="7 multiple failed stats" src="https://github.com/user-attachments/assets/caa60c36-6854-46b5-8c19-4c05e1ee03f2" />


### 4️⃣ Successful SSH Logins
index="ssh_logs" source="ssh_logs.json" event_type="Successful SSH Login"
| stats count by id.orig_h, id.resp_h<img width="1884" height="901" alt="9 successful login stats" src="https://github.com/user-attachments/assets/8c2f3223-eb52-4573-98ed-4e2cbf8dc707" />


### 5️⃣ Connection Without Authentication
index="ssh_logs" source="ssh_logs.json" event_type="Connection Without Authentication"
| stats count by id.orig_h<img width="1899" height="918" alt="11 connection without auth stats" src="https://github.com/user-attachments/assets/ee140508-1ef1-47d4-a33d-8bb6a77eb2ff" />


### 6️⃣ Time-Based Analysis
index="ssh_logs" source="ssh_logs.json" event_type="Connection Without Authentication"
| timechart count by id.orig_h<img width="1917" height="500" alt="12 timechart" src="https://github.com/user-attachments/assets/f752e605-10b6-41aa-be42-9212658e51a1" />


## 📊 Dashboard & Alerting:
Created visualizations (Column Charts). <img width="1901" height="847" alt="6 failed login chart" src="https://github.com/user-attachments/assets/04090aa1-c07d-4c76-a412-f0edfaa2ec4a" />
 
Built dashboards using Splunk Dashboard Studio.  <img width="1900" height="909" alt="10 dashboard" src="https://github.com/user-attachments/assets/e3a218cc-87bc-4612-b560-bfdf482f07f0" />

Configured alert for brute force detection.  
Alert type: Per-Result.  
Trigger condition: Based on multiple failed login attempts.<img width="1900" height="909" alt="10 dashboard" src="https://github.com/user-attachments/assets/b9d2a5eb-338c-4a5c-9ec0-2fafffbd4dc2" />
  

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
