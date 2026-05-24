# SPL Queries — Splunk SIEM Project

All queries used in this project for security log monitoring and threat detection.

---

## Query 1: Show All Logs
```spl
index=security_logs
```
**Purpose:** View all ingested security log events.

---

## Query 2: Failed Requests (404 Errors)
```spl
index=security_logs status=404
```
**Purpose:** Filter only failed HTTP 404 requests. High volume of 404s from one IP can indicate scanning/enumeration.

---

## Query 3: Count Failed Requests
```spl
index=security_logs status=404
| stats count
```
**Purpose:** Get total count of 404 errors for baselining and alerting thresholds.

---

## Query 4: Top Attacker IPs
```spl
index=security_logs status=404
| stats count by clientip
| sort -count
```
**Purpose:** Rank IP addresses by 404 error count. Top IPs are likely scanners or attackers.

---

## Query 5: Timeline Graph
```spl
index=security_logs status=404
| timechart count
```
**Purpose:** Visualize failed requests over time. Spikes indicate potential attack activity.

---

## Bonus Queries (Future Use)

### Failed Login Detection (Windows Logs)
```spl
index=windows_logs EventCode=4625
| stats count by Account_Name, src_ip
| sort -count
```

### Brute Force Detection
```spl
index=windows_logs EventCode=4625
| stats count by src_ip
| where count > 10
```

### Successful Login After Multiple Failures
```spl
index=windows_logs (EventCode=4625 OR EventCode=4624)
| stats count(eval(EventCode=4625)) as failures,
        count(eval(EventCode=4624)) as successes by src_ip
| where failures > 5 AND successes > 0
```
