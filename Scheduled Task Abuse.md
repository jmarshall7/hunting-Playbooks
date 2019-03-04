# Scheduled Task Abuse

<BR>

## Background
Adversaries targeting MSPs have been known to utilize Scheeduled task utilities to schedule programs or scripts to be eecuted at a date and time on local and remote hosts.An adversary may use task scheduling to execute programs at system startup or on a scheduled basis for persistence, to conduct remote Execution as part of Lateral Movement, to gain SYSTEM privileges, or to run a process under the context of a specified account.

---

## Hypothisis
If Suspicious scheduled tasks are identified. This may suggest that a threat actor has gained access to the network and is attempting to maintain persistence or conduct lateral movement. Additionally, if suspicious remote scheduled tasks are being made this may suggest that a threat actor has gained administrative rights.Scheduling a task on a remote system typically required being a member of the Administrators group on the the remote system.

---

## CB Hunting Notes

---

## CS Hunting Notes

---


## HUNTER NOTES
* Analyze network data for unusual amounts of data to/from endpoints.
* Processes making network connections that do not normally have network communication or have never been seen before. Long-   tail analysis may be best approach here. 
* Analyze packet contents to detect communications that do not follow the expected protocol behavior for the port that is     being used. 

---
