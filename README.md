# 🛡️ Windows Persistence Checker

## 🔍 What It Checks  
This script inspects several areas where persistence is commonly established — whether by legitimate software or malicious actors:

### Registry Run Keys
- `HKLM\Software\Microsoft\Windows\CurrentVersion\Run`  
- `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`

### Startup Folder Shortcuts
- Startup folders for the current user and all users

### Scheduled Tasks
- All non-Microsoft tasks using `Get-ScheduledTask`

### Auto-Start Services (Non-Microsoft)
- Running services set to auto-start that don’t reference Microsoft binaries

---

## 🔄 v1 vs v2: What Changed?

### 🧾 Version 1 – Basic Output
- ✅ Printed persistence data to the terminal  
- ❌ No file output or structured format  
- ❌ Couldn’t detect changes over time  
- ✔️ Good for one-off checks

### 💡 Version 2 – Logging, JSON, and Baseline Comparison
- 📝 **Output to text file**  
  Save results to any file path you choose — great for investigations, ticketing, or long-term triage notes.

- 🧮 **Export to JSON (NEW)**  
  Add the `-Json` flag to export results in structured JSON format for parsing, correlation, or ingestion into SIEM/logging pipelines.

- 📊 **Baseline comparison**  
  Create a “known-good” snapshot of a clean system, then compare new persistence entries against it.

- 🎯 **Delta highlighting**  
  Console + log output shows exactly what changed — potential quick wins when investigating lateral movement or stealthy malware.

---

## 🚀 How to Use (v2)

### 🔹 Step 1: Generate a Clean Baseline  
When the system is in a known-good state:


`.\Run-PersistenceCheck.ps1
Run-PersistenceCheck -LogPath "C:\Logs\baseline.txt"`

🔹 Step 2: Compare Later Against the Baseline
On the same (or similar) system:

`Run-PersistenceCheck -LogPath "C:\Logs\current.txt" -BaselinePath "C:\Logs\baseline.txt"`

🔹 (Optional) Export to JSON for SIEM/Automation
If you want a structured output:

`Run-PersistenceCheck -LogPath "C:\Logs\current.txt" -JsonOutputPath "C:\Logs\current.json`
This will create current.txt as a JSON file that tools or analysts can easily parse.

🔧 Future Ideas
Want to help expand this tool?

Integration with logging pipelines (ELK, Sentinel, etc.)

Delta alerting (e.g. email or webhook on new persistence)

Scheduled scanning or detection-as-code workflows

👤 About the Author
Blue teamer focused on incident response, detection engineering, and defensive automation.
Building practical tools for real-world SOC and DFIR operations.

