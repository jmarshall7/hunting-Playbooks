# Scheduled Task Creations

<BR>

## Purpose/Hypothesis

Adversaries targeting MSPs have been known to utilize Scheduled task utilities to schedule programs or scripts to be executed at a date and time on local and remote hosts. An adversary may use task scheduling to execute programs at system startup or on a scheduled basis for persistence, to conduct remote Execution as part of Lateral Movement, to gain SYSTEM privileges, or to run a process under the context of a specified account. If Suspicious scheduled tasks are identified. This may suggest that a threat actor has gained access to the network and is attempting to maintain persistence or conduct lateral movement. Additionally, if suspicious remote scheduled tasks are being made this may suggest that a threat actor has gained administrative rights. Scheduling a task on a remote system typically required being a member of the Administrators group on the the remote system.

**Data time frame**: 2 weeks or more

**MITRE techniques**: [T1053 - Scheduled Tasks](https://attack.mitre.org/techniques/T1053/)

### Retrieve all newly created scheduled tasks

__Query: Carbon Black Response__
```
(process_name:schtasks.exe AND cmdline:"schtasks\ /create\ /tn")
```
**CbR caveat**: use API tools such as [cbinterface.py](https://github.ibm.com/MSS-MDR/cbinterface) or Red Canary's [process-util.py](https://github.ibm.com/MSS-MDR/redcanary-response-utils) when the number of results exceeds 1000 (Cb Response UI only support exporting the top 1000 process results as CSV). Group by process ID to keep the number or results down.

### Prepare and analyse data

1. To quickly sort and analyze results the recommendation would be to export to csv for grouping and long-tail analysis to identify anomolies. Pivot tables are an efficient resource for this. this would allow you to group command line outputs with the hostname as well as username.

2. Outliers and suspicious task creations will need further investigation with the client in determining if it is authorized activity. 

3. For identified anomolies that have not been deemed authorized; further investigation of the task creation will need to be conducted. Trace the process tree in attempts to determine what activity occured shortly before the task creation. attempt to search out any additional suspicious activity from the user account that creat the scheduled task. Attempt to identify any additional TTPs that may further support the hypothisis that an unauthorized actor is present on the network.

## Report contents

- Hosts that now have malware persistence
- Usernames that have been compromised
- Possible root cause of the activity

## Followup hunts

--TBD--

## References

+ [MITRE ATT&CK Scheduled Tasks](https://attack.mitre.org/techniques/T1053/)
+ [Your Practical Guide to Threat Hunting](https://sqrrl.com/media/Your-Practical-Guide-to-Threat-Hunting.pdf)
