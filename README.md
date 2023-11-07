# Part 2: Microsoft Sentinel SIEM
![MS Sentinel Workbooks](https://github.com/alexmerelus/Part-2---Microsoft-Sentinel-SIEM-/assets/138509128/0ca726fc-aafd-46ad-8172-dc0526422f2f)

I created four different workbooks within Microsoft Sentinel to display various types of malicious traffic from around the world targeting our resources. Using pre-built JSON templates, I constructed maps for "Windows RDP/SMB Authentication Failures," "Linux SSH Authentication Failures," "MS SQL Server Authentication Failures," and "NSG Allowed Malicious Inbound Flows."

After setting these up, I reviewed the maps to observe any pre-existing malicious traffic, making sure to select an appropriate time-frame of the past 30 days to capture recent activities.

### Imported Sentinel Rules
![13 - Imported Sentinetal Rules](https://github.com/alexmerelus/Part-2---Microsoft-Sentinel-SIEM-/assets/138509128/4fca5f85-bb52-4522-8c4e-1d0c0f329f1c)

I checked my subscription's cost analysis before heading to Azure Sentinel, where I navigated to "Analytics" and then "Active Rules" to manually create a rule named "TEST: Brute Force ATTEMPT - Windows." This rule was designed to detect multiple failed login attempts within the last hour. After crafting and testing the rule, ensuring it could trigger properly, I deleted it.

Continuing with the analytics part, I imported all the necessary Sentinel Analytics Rules and then selected the "CUSTOM: Brute Force SUCCESS - Windows" alert for editing. I copied the query to analyze it within the Log Analytics Workspace. This process was repeated for all the custom analytics rules to ensure I fully understood them.

I noted that in the next steps, I would be generating traffic from "attack-vm" to activate some of these rules, although some might be triggered automatically by live internet traffic. Keeping in mind cost savings, I decided to leave the VMs on to generate more logs.

### Maps of attacks based on previously created Sentinel Workbooks 
![14 - mssql-auth-fail (WorldMap Screenshot) B4](https://github.com/alexmerelus/Part-2---Microsoft-Sentinel-SIEM-/assets/138509128/20c8d014-bb09-4b61-9162-94172772ecd0)
![14 - nsg-malicious-allowed-in (WorldMap SS) B4](https://github.com/alexmerelus/Part-2---Microsoft-Sentinel-SIEM-/assets/138509128/e00bf9d1-e984-41a9-82d9-13e7746043af)
![14 - windows-rdp-auth-fail (WorldMap SS) B4](https://github.com/alexmerelus/Part-2---Microsoft-Sentinel-SIEM-/assets/138509128/dd5cc794-0bd6-4ce6-b97a-68e8612e14bc)
![14 - Linux-ssh-auth-fail (WorldMap SS) B4](https://github.com/alexmerelus/Part-2---Microsoft-Sentinel-SIEM-/assets/138509128/0f75f77e-c0af-4abd-8033-9580c873fbff)

### BEFORE SECURING ENVIRONMENT
| Stage                                         | Value           |
|-----------------------------------------------|------------------|
| Start Time      | 2023-11-03 T 4:08:03.124PM |
| Stop Time        | 2023-11-03 T 4:08:03.124PM |
| Security Events (Windows VMs)                 | 51330            |
| Syslog (Linux VMs)                            | 22054            |
| SecurityAlert (Microsoft Defender for Cloud)  | 35               |
| SecurityIncident (Sentinel Incidents)         | 348              |
| NSG Inbound Malicious Flows Allowed           | 2307             |

