# Logjammer Splunk Analysis

This repository contains the analysis and solutions for the Hack The Box "Logjammer" Sherlock challenge using Splunk.

## Challenge Overview

You have been presented with the opportunity to work as a junior DFIR consultant for a big consultancy. However, they have provided a technical assessment for you to complete. The consultancy Forela-Security would like to gauge your Windows Event Log Analysis knowledge. We believe the Cyberjunkie user logged in to his computer and may have taken malicious actions. Please analyze the given event logs and report back.
## Tools Used

- **Splunk**: For analyzing and visualizing log data.
- **Python**: For any scripting or additional log parsing.
- **Wireshark**: (if applicable) for network traffic analysis.

## Challenge Questions and Answers

1. **When did the cyberjunkie user first successfully log into his computer? (UTC)**
   - **Answer:** 27/03/2023 14:37:09

2. **The user tampered with firewall settings on the system. Analyze the firewall event logs to find out the Name of the firewall rule added?**
   - **Answer:** Metasploit C2 Bypass

3. **What's the direction of the firewall rule?**
   - **Answer:** Outbound

4. **The user changed the audit policy of the computer. What's the Subcategory of this changed policy?**
   - **Answer:** Other Object Access Events

5. **The user "cyberjunkie" created a scheduled task. What's the name of this task?**
   - **Answer:** HTB-AUTOMATION

6. **What's the full path of the file which was scheduled for the task?**
   - **Answer:** `C:\Users\CyberJunkie\Desktop\Automation-HTB.ps1`

7. **What are the arguments of the command?**
   - **Answer:** `-A cyberjunkie@hackthebox.eu`

8. **The antivirus running on the system identified a threat and performed actions on it. Which tool was identified as malware by the antivirus?**
   - **Answer:** Sharphound

9. **What's the full path of the malware which raised the alert?**
   - **Answer:** `C:\Users\CyberJunkie\Downloads\SharpHound-v1.1.0.zip`

10. **What action was taken by the antivirus?**
    - **Answer:** Quarantine

11. **The user used PowerShell to execute commands. What command was executed by the user?**
    - **Answer:** `Get-FileHash -Algorithm md5 .\Desktop\Automation-HTB.ps1`

12. **We suspect the user deleted some event logs. Which Event log file was cleared?**
    - **Answer:** `Microsoft-Windows-Windows Firewall With Advanced Security/Firewall`

## Steps Taken

### 1. Initial Log Exploration
- Loaded the provided log files into Splunk.
- Conducted initial searches to identify any anomalies or patterns.

### 2. Detailed Analysis
- Focused on specific timestamps and IP addresses that showed suspicious activity.
- Used Splunk queries to drill down into the data.

### 3. Key Findings
- Discovered an attack vector related to X.
- Identified the potential exploit and traced the attacker's steps.

### 4. Mitigation Strategies
- Suggested configurations and monitoring techniques to prevent future attacks.

## Conclusion

This analysis provided insights into the security flaws within the system. The use of Splunk allowed for effective log parsing and identification of critical issues.
