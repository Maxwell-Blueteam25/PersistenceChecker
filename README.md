# 🛡️ Windows Persistence Checker

A PowerShell script to identify common persistence mechanisms on Windows endpoints. Useful for incident responders, threat hunters, and blue teamers conducting live response or triage.

---

## 🔍 What It Checks

This script looks for common persistence techniques often abused by malware or red teams:

- **Registry Run Keys**  
  - `HKLM\Software\Microsoft\Windows\CurrentVersion\Run`  
  - `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`

- **Startup Folder Shortcuts**  
  - Current user and all users' Startup folders

- **Scheduled Tasks**  
  - All non-Microsoft scheduled tasks

- **Auto-Start Services (non-Microsoft)**  
  - Running, automatically starting services that don’t reference Microsoft binaries

---

## 🔄 v1 vs v2: What Changed?

### 🧾 v1: Basic Output
- Printed results to the **console only**
- Good for manual checks but not scalable for investigations or documentation
- No way to track changes over time

### 💡 v2: Logging & Baseline Comparison
- 📝 **Log to file** — You can now specify a path to save the output (great for investigations, ticketing, or audit trails)
- 📊 **Baseline comparison** — Compare the current system state to a known-good baseline and identify **differences**
- 🎯 **Highlighting deltas** — Differences are clearly shown both in the console and in the output file, helping you find changes quickly

---

## 🚀 How to Use v2

### 1️⃣ Generate a Baseline (when system is clean)

.\Run-PersistenceCheck.ps1
Run-PersistenceCheck -LogPath "C:\Logs\baseline.txt"

## 2️⃣ Run Again Later and Compare to the Baseline

Run-PersistenceCheck -LogPath "C:\Logs\current.txt" -BaselinePath "C:\Logs\baseline.txt"

---

Blue teamer focused on incident response, detection engineering, and defensive automation.
Building practical tools for real-world SOC and DFIR operations.

Feel free to fork, improve, and share.

