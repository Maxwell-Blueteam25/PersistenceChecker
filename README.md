# 🛡️ Windows Persistence Checker

A PowerShell script to identify common **persistence mechanisms** on Windows endpoints. Useful for incident responders, threat hunters, and blue teamers conducting live response or triage.

## 🔍 What It Checks

This script identifies basic persistence techniques often used by legitimate programs **and** malware:

1. **Registry Run Keys**  
   - `HKLM\...\Run` and `HKCU\...\Run`

2. **Startup Folder Shortcuts**  
   - Current user and all users' Startup folders

3. **Scheduled Tasks**  
   - Non-Microsoft tasks listed via `Get-ScheduledTask`

4. **Auto-start Services (non-Microsoft)**  
   - Auto-starting services with suspicious paths

---

🧠 About the Author
Blue teamer focused on incident response, detection engineering, and defensive automation.
Building practical tools for real-world SOC and DFIR operations.

Feel free to fork, improve, and share.

