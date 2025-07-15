Task 2 – Manual Log Analysis & Incident Response

This repository contains my complete work for Task 2 of the Future Interns Cyber Security Internship. In this task, I analyzed Apache web server logs using basic Linux command-line tools (instead of Splunk, due to export restrictions) to simulate SIEM log monitoring and generate an incident response report.

-------------------------------------------------------

🎯 Objective:
Perform security alert monitoring and incident classification based on log analysis of Apache access logs using Linux tools. Document suspicious activity and recommend response actions.

-------------------------------------------------------

🛠️ Tools Used:
- Kali Linux (VirtualBox)
- Apache Access Logs (Sample from Elastic GitHub)
- Linux Commands: grep, awk, cut, uniq, sort, wc
- gnome-screenshot: for capturing terminal results

-------------------------------------------------------

🔍 Log File Source:
Apache access log file downloaded from:
https://github.com/elastic/examples/blob/master/Common%20Data%20Formats/apache_logs/apache_logs

Saved locally as:
~/internship-reports/Task_2/apache_access.log

-------------------------------------------------------

📊 Commands Executed:

1. Total Log Entries:
wc -l apache_access.log

2. Top 5 Requesting IPs:
awk '{print $1}' apache_access.log | sort | uniq -c | sort -nr | head -5

3. Top 5 Requested URLs:
awk -F\" '{print $2}' apache_access.log | awk '{print $2}' | sort | uniq -c | sort -nr | head -5

4. 404 Errors (Path Scanning):
grep " 404 " apache_access.log

5. Suspicious HTTP Methods:
grep -E "PUT|DELETE|HEAD" apache_access.log

-------------------------------------------------------

📌 Key Findings:
- Repeated 404 errors from the same IPs indicate scanning
- Suspicious use of DELETE and HEAD HTTP methods
- Multiple access attempts to paths like /phpmyadmin and /xmlrpc.php

-------------------------------------------------------

🛡️ Recommended Incident Response:
- Block abusive IPs identified from log analysis
- Enable alerts on non-standard HTTP methods
- Apply WAF rules for sensitive paths
- Rate-limit login attempts and high-traffic endpoints

-------------------------------------------------------

📂 Folder Structure:
FUTURE_CS_02/
├── apache_access.log
├── reports/
│   └── task2_manual_log_analysis.txt
│   └── task2_readme.txt
└── screenshots/
    └── task2_log_terminal.png

-------------------------------------------------------

✅ Status:
Task 2 completed using Linux-based SIEM simulation due to region-based restriction on Splunk Cloud. Analysis, screenshots, and reports are included in this repo.

© 2024 by Ethical Hacker – Future Interns Cybersecurity Track
