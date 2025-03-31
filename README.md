# Splunk SIEM & Log Analysis Project – Defensive Monitoring for VSI  

## 🔍 Project Overview  

This project focuses on building a real-time **log analysis and alerting system** for Virtual Space Industries (VSI), a company concerned about targeted cyberattacks from a competitor. Our team leveraged **Splunk** to ingest logs from **Windows servers** and **Apache web servers**, detect suspicious activity, and create dashboards, reports, and alerts to monitor system behavior.

We performed baseline analysis of normal activity and compared it with known attack logs, helping uncover brute-force attempts, unusual login spikes, account deletions, and international threat activity.

---

## 🛠️ Core Project Goals  

- Investigate normal and attack activity across Windows and Apache logs  
- Establish thresholds and build reports for login activity, account changes, HTTP methods, and response codes  
- Create visual dashboards to monitor and quickly identify threats  
- Generate and tune alerts to reduce false positives  
- Recommend security improvements based on findings  

---

## ⚙️ Key Components  

- **Splunk SIEM** for log ingestion, search, alerting, and dashboards  
- **Apache Access Logs** for web activity monitoring  
- **Windows Security Logs** for system-level events  
- **IP Geolocation Add-on** to analyze foreign threat origins  
- **Normal & Attack Log Comparison** to identify threat patterns  

---

## 🧠 Key Skills  

- Log analysis and event correlation  
- Alert thresholding and suppression tuning  
- Dashboard and report creation in Splunk  
- HTTP request analysis (GET, POST, 404, 200, etc.)  
- Behavioral baselining and deviation analysis  
- Identifying brute-force attempts and account compromises  
- Visualization of network activity and user behavior  
- Providing actionable mitigation strategies  

---

## 🖼️ Screenshots & Visuals  

*Add screenshots here, including dashboards, charts, reports, and time-based visualizations.*  

---

## 📊 Reports & Dashboards  

### Windows Log Analysis  
- Signature report by event ID  
- Severity level distribution  
- Success vs failure login counts  
- High-severity spikes: “An account was successfully logged on,” “A user account was locked out,” “An attempt was made to reset an account password”  
- Dashboard panels for time-based signature analysis, user behavior, and failed/successful login events  

### Apache Log Analysis  
- HTTP methods (GET, POST, etc.)  
- Referrer domains and URI hits  
- HTTP response codes (200, 404, etc.)  
- Spike in `/VSI_Account_logon.php` suggesting brute-force attack  
- Dashboard panels: method distribution, URI frequency, cluster maps, and POST request alerts  

---

## 🚨 Alerting Strategy  

**Windows Alerts:**  
- Failed login threshold: >10/hour  
- Successful login threshold: >25/hour (recommended lowering to 10/hour based on spike)  
- Account deletion threshold: >22/hour  

**Apache Alerts:**  
- HTTP POST spike threshold: >800 (attack had 1324 POSTs)  
- Suspicious URI access: >50 hits on login page  
- Referring domains exceeding 100 requests  
- International access alert (e.g. Ukraine activity >137/hour)  

---

## 🚧 Sample Attack Indicators  

- 1258 password reset attempts (9 AM)  
- 896 account lockouts (2 AM)  
- 1324 POST requests to login page  
- 679 HTTP 404 responses  
- IP geolocation traced to Kyiv, Ukraine  

---

## 🔐 Summary of Attack Findings  

- Coordinated brute-force attacks and credential stuffing attempts  
- Elevated POST and 404 requests suggest automated web probing  
- Sudden increase in login success from specific user accounts (User_k, User_a)  
- Significant drop in legitimate referrer domains  
- Suspicious URI and spike in login page traffic  
- Foreign IPs involved, primarily from Eastern Europe  

---

## 🔐 Recommendations & Future Mitigation  

- Implement rate-limiting and CAPTCHA on login forms  
- Enforce MFA for all employee accounts  
- Enable geo-blocking for high-risk regions  
- Tune alert thresholds to catch anomalous trends earlier  
- Conduct regular log audits and automate log review  
- Use Splunk correlation searches to tie related events together  
- Educate staff on login hygiene and attack indicators  

