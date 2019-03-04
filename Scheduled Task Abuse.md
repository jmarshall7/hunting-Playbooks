# Scheduled Task Abuse

<BR>

## Background
Adversaries targeting MSPs have been known to utilize Scheeduled task utilities to schedule programs or scripts to be eecuted at a date and time on local and remote hosts.An adversary may use task scheduling to execute programs at system startup or on a scheduled basis for persistence, to conduct remote Execution as part of Lateral Movement, to gain SYSTEM privileges, or to run a process under the context of a specified account.

---

## Hypothisis
If Suspicious scheduled tasks are identified. This may suggest that a threat actor has gained access to the network and is attempting to maintain persistence or conduct lateral movement. Additionally, if suspicious remote scheduled tasks are being made this may suggest that a threat actor has gained administrative rights.Scheduling a task on a remote system typically required being a member of the Administrators group on the the remote system.

---

## CB Hunt Query

childproc_name:schtasks.exe AND -digsig_result:Signed AND -process_name:wsqmcons.exe AND -process_name:taskeng.exe

---

## CS Hunting Notes

---


## HUNTER NOTES
* query an environment. once results finish. export to csv and conduct long tail analysis identifying anomolous scheduled tasks creations.  
* further investigate findings determining if it is authorized activity. From there attempt to investigate the anomolies thag have not been identified as authorized by tracing the steps of the actor (what has the user done in addition to the cheduled task creation, does anything else stand out as suspicious? etc.)

---
