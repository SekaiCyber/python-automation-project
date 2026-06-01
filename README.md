# 4️⃣ Automation Project – Beginner

**Title:** Basic Log Analysis Automation Using Python

---

## 📌 Objective

Build a Python script to:

- Read a log file
- Count failed logins
- Print suspicious IP

---

## 🛠️ Tools & Language

- **Language:** Python 3
- **Module:** `collections.Counter` (built-in)
- **Environment:** Mac Terminal
- **Files:** `security.log`, `log_parser.py`

---

## 💻 Code

```python
from collections import Counter

failed_ips = []

with open("security.log") as file:
    for line in file:
        if "FAILED LOGIN" in line:
            ip = line.split()[-1]
            failed_ips.append(ip)

counts = Counter(failed_ips)

for ip, count in counts.items():
    if count >= 5:
        print(f"Suspicious IP: {ip} - Attempts: {count}")
```

---

## 🧠 Explanation

**Why Counter?**

`Counter` is a built-in Python class from the `collections` module. It automatically counts how many times each unique value appears in a list. Without it, you would need to write a manual loop to track and increment counts yourself. It keeps the code clean and efficient.

**How Parsing Works**

The script reads `security.log` one line at a time. For each line, it checks whether `"FAILED LOGIN"` appears. If it does, `line.split()[-1]` breaks the line into a list of words and selects the last item — the IP address. That IP is added to the `failed_ips` list. This is called **log parsing** — extracting useful data from raw text.

**Threshold Logic**

After counting, the script loops through each IP and its count. The condition `if count >= 5` flags any IP with five or more failed attempts as suspicious. This mirrors how real security tools like **Fail2Ban** work — alerting only when a pattern crosses a defined limit, not on every single failure.

---

## 🖼️ Screenshots

| # | Screenshot | Description |
|---|---|---|
| 1 | *(paste image)* | Project directory created and navigated into |
| 2 | *(paste image)* | `security.log` contents verified |
| 3 | *(paste image)* | Nano editor with code visible |
| 4 | *(paste image)* | Script output – suspicious IP flagged |
| 5 | *(paste image)* | File listing showing both files |

---

## 💡 Improvement Ideas

- **Export to CSV** — Write results to a `.csv` file using Python's `csv` module for easier analysis
- **Send Email Alert** — Use `smtplib` to automatically send an alert when a suspicious IP is detected
- **Add Timestamp Filtering** — Filter log entries by time window to avoid false alerts from old data

---

## ⚠️ Notes

- The IPs used (`192.168.1.10`, `10.0.0.5`) are **private range IPs** — they are not real or traceable
- This is a **simulated environment** for educational purposes only
- All screenshots have been reviewed to remove personal identifying information
