
# Logjammer Splunk Analysis

This repository contains the analysis and solutions for the Hack The Box "Logjammer" Sherlock challenge using Splunk.

## Challenge Overview

You have been presented with the opportunity to work as a junior DFIR consultant for a big consultancy. However, they have provided a technical assessment for you to complete. The consultancy Forela-Security would like to gauge your Windows Event Log Analysis knowledge. We believe the Cyberjunkie user logged in to his computer and may have taken malicious actions. Please analyze the given event logs and report back.

- **Splunk**: For analyzing and visualizing log data.


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

### Analysis Steps
1. **Loading Logs into Splunk**
   - Logs were loaded into Splunk, and initial searches were conducted to identify potential security events.
   - The challenge required identifying specific actions performed by the "cyberjunkie" user.

2. **Investigating Anomalies**
   - A successful login event for the user "cyberjunkie" was identified on 27/03/2023 at 14:37:09 UTC.
   - Firewall logs were analyzed to identify the addition of a new rule named "Metasploit C2 Bypass" with an outbound direction.
   - The audit policy change was traced to the "Other Object Access Events" subcategory.
   - A scheduled task named "HTB-AUTOMATION" was created by the user, pointing to the script `C:\Users\CyberJunkie\Desktop\Automation-HTB.ps1`.

3. **Identifying the Exploit**
   - The scheduled task was set to run a PowerShell script with the arguments `-A cyberjunkie@hackthebox.eu`.
   - The antivirus logs indicated that "Sharphound" was detected as malware and quarantined from the path `C:\Users\CyberJunkie\Downloads\SharpHound-v1.1.0.zip`.
   - The PowerShell command executed by the user was `Get-FileHash -Algorithm md5 .\Desktop\Automation-HTB.ps1`.
   - It was also discovered that the user cleared the event log `Microsoft-Windows-Windows Firewall With Advanced Security/Firewall`.

4. **Mitigation**
   - Suggested measures include regular monitoring of audit policies, scheduled tasks, and frequent reviews of firewall rules.
   - Ensuring antivirus software is up-to-date and regularly reviewing detected threats and actions taken.

## Conclusion

This analysis provided insights into the security flaws within the system. The use of Splunk allowed for effective log parsing and identification of critical issues.
