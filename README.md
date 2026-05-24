# 🔍 Splunk SIEM Monitoring Project

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

## 💡 Key Learnings

- How to ingest and parse logs in Splunk
- Writing SPL queries for threat detection
- Identifying suspicious patterns (high 404s = possible scanner/attacker)
- Building dashboards for SOC monitoring
- Configuring threshold-based alerts

---

## 🔗 Skills Demonstrated

`Splunk` `SIEM` `SPL` `Log Analysis` `Threat Detection` `Dashboard Creation` `Alert Configuration` `Blue Team` `SOC Analyst`
