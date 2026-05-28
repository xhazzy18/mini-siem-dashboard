# Mini SIEM Dashboard

A beginner-friendly cybersecurity project built in Python that analyzes authentication logs and detects suspicious login activity such as brute-force attacks.

---

## Features

* Detects failed login attempts
* Identifies suspicious IP addresses
* Generates brute-force attack alerts
* Parses authentication logs
* Displays suspicious activity reports

---

## Technologies Used

* Python
* Cybersecurity Fundamentals
* Log Analysis
* Threat Detection

---

## Project Structure

```plaintext
mini-siem/
│
├── logs/
├── analyzer.py
├── sample_logs.txt
└── README.md
```

---

## Sample Logs

```txt
192.168.1.10 FAILED_LOGIN
192.168.1.10 FAILED_LOGIN
192.168.1.10 FAILED_LOGIN
192.168.1.10 FAILED_LOGIN
192.168.1.25 SUCCESS_LOGIN
10.0.0.5 FAILED_LOGIN
10.0.0.5 FAILED_LOGIN
172.16.0.2 SUCCESS_LOGIN
```

---

## Python Code

```python
from collections import defaultdict

failed_attempts = defaultdict(int)

with open("sample_logs.txt", "r") as file:
    logs = file.readlines()

for log in logs:
    parts = log.strip().split()

    ip = parts[0]
    action = parts[1]

    if action == "FAILED_LOGIN":
        failed_attempts[ip] += 1

print("\n=== Suspicious Activity Report ===\n")

for ip, count in failed_attempts.items():
    print(f"{ip} -> {count} failed attempts")

    if count >= 3:
        print(f"[ALERT] Possible brute-force attack from {ip}\n")
```

---

## Example Output

```bash
=== Suspicious Activity Report ===

192.168.1.10 -> 4 failed attempts
[ALERT] Possible brute-force attack from 192.168.1.10

10.0.0.5 -> 2 failed attempts
```

---

## Learning Objectives

This project was created to practice:

* SIEM fundamentals
* SOC monitoring concepts
* Authentication log analysis
* Threat detection logic
* Python scripting for cybersecurity

---

## Future Improvements

* Real-time log monitoring
* Severity-based alerts
* CSV report generation
* Dashboard visualization
* Streamlit web interface
* Email alerting system

Abdul Rahim Memon
Cyber Security Student | Python | OWASP | Threat Analysis
