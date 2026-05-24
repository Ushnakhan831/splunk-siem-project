# 🔍 Splunk SIEM Monitoring Project

![SIEM](https://img.shields.io/badge/SIEM-Splunk-orange?style=for-the-badge&logo=splunk)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Beginner-blue?style=for-the-badge)
![Blue Team](https://img.shields.io/badge/Team-Blue%20Team-navy?style=for-the-badge)

## 📌 Project Overview

Created a beginner SIEM monitoring project using **Splunk** to detect failed requests and suspicious IP activity through SPL queries, dashboards, and alerts.

This project simulates a real SOC Analyst workflow — ingesting logs, writing detection queries, building dashboards, and setting up automated alerts for suspicious activity.

---

## 🎯 Objectives

- Ingest and index security logs into Splunk
- Write SPL queries to detect failed HTTP requests (404 errors)
- Identify top attacker/suspicious IPs
- Build a visual dashboard for monitoring
- Set up automated alerts for threshold-based detection

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Splunk Free | SIEM Platform |
| SPL (Search Processing Language) | Log querying and analysis |
| Splunk Dashboards | Data visualization |
| Splunk Alerts | Automated threat detection |

---

## 📂 Project Structure

```
splunk-siem-project/
│
├── README.md               # Project documentation
├── queries/
│   └── spl_queries.md      # All SPL queries used
├── screenshots/
│   ├── dashboard.png       # Main monitoring dashboard
│   ├── failed_requests.png # Failed request search results
│   ├── top_ips.png         # Top attacker IPs
│   └── alerts.png          # Alert configuration
└── sample_data/
    └── sample_logs.csv     # Sample security logs used
```

---

## 🔎 SPL Queries

### 1. Show All Logs
```spl
index=security_logs
```
> Displays all ingested security log events.

---

### 2. Failed Requests (404 Errors)
```spl
index=security_logs status=404
```
> Filters logs to show only failed HTTP 404 requests — common indicator of scanning or enumeration activity.

---

### 3. Count Failed Requests
```spl
index=security_logs status=404
| stats count
```
> Returns total number of 404 errors — useful for baselining and threshold alerting.

---

### 4. Top Attacker IPs
```spl
index=security_logs status=404
| stats count by clientip
| sort -count
```
> Identifies which IP addresses are generating the most 404 errors — helps pinpoint potential attackers or scanners.

---

### 5. Timeline Graph (Timechart)
```spl
index=security_logs status=404
| timechart count
```
> Visualizes failed requests over time — helps detect attack patterns and spikes.

---

## 📊 Dashboard Screenshots

### Main Monitoring Dashboard
![Dashboard](screenshots/dashboard.png)

### Failed Requests Over Time
![Failed Requests](screenshots/failed_requests.png)

### Top Suspicious IPs
![Top IPs](screenshots/top_ips.png)

---

## 🚨 Alerts Configured

| Alert Name | Condition | Trigger |
|-----------|-----------|---------|
| High 404 Activity | 404 count > 50 in 5 min | Real-time |
| Suspicious IP Detected | Single IP > 20 requests | Hourly |

---

## 💡 Key Learnings

- How to ingest and parse logs in Splunk
- Writing SPL queries for threat detection
- Identifying suspicious patterns (high 404s = possible scanner/attacker)
- Building dashboards for SOC monitoring
- Configuring threshold-based alerts

---

## 🔗 Skills Demonstrated

`Splunk` `SIEM` `SPL` `Log Analysis` `Threat Detection` `Dashboard Creation` `Alert Configuration` `Blue Team` `SOC Analyst`

---

## 📈 Future Improvements

- [ ] Add brute force detection queries
- [ ] Ingest Windows Event Logs (failed logins - Event ID 4625)
- [ ] Build correlation rules
- [ ] Integrate with MITRE ATT&CK framework
- [ ] Add malware traffic detection using Wireshark PCAPs

---

## 👩‍💻 Author

**[Tumhara Naam Yahan]**  
Cybersecurity Enthusiast | SOC Analyst (Learning) | Blue Team  
🔗 [LinkedIn Profile Link]  
📧 [Email - Optional]

---

## 📚 References

- [Splunk Documentation](https://docs.splunk.com)
- [TryHackMe - Splunk Room](https://tryhackme.com)
- [Splunk Free Training](https://education.splunk.com)
