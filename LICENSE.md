
### Updated `writeup.md`

```markdown
# Logjammer Challenge Write-Up

## Introduction

This write-up details the process of solving the "Logjammer" challenge on Hack The Box using Splunk for log analysis.

## Challenge Breakdown

### Log Files Provided
- The logs were parsed and indexed in Splunk to facilitate analysis.
- The logs were analyzed to identify key events related to user activity, firewall changes, and potential security incidents.

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

This analysis provided a comprehensive understanding of the user's activities and the potential security implications. The use of Splunk allowed for an effective breakdown of the logs, leading to the identification of critical events and the suggested mitigation strategies.

