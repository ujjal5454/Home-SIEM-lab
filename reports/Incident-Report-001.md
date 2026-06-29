INCIDENT REPORT #001

====================

Date: June 18, 2026

Analyst: Ujjal Basnet

Severity: MEDIUM



EXECUTIVE SUMMARY

\-----------------

A network reconnaissance attack was detected originating from

192.168.56.101 targeting the Windows host at 192.168.56.1.

The attacker probed SMB port 445 indicating potential

pre-attack reconnaissance activity.



TIMELINE

\--------

11:22:03 - Network connection detected to port 445 (SMB)

&#x20;          Source: 192.168.56.101 (Linux VM - Attacker)

&#x20;          Destination: 192.168.56.1 (Windows Host)



INDICATORS OF COMPROMISE (IOCs)

\--------------------------------

Attacker IP : 192.168.56.101

Target IP   : 192.168.56.1

Target Port : 445 (SMB)

Protocol    : TCP

Tool used   : Netcat (nc)



MITRE ATT\&CK MAPPING

\---------------------

Tactic    : Reconnaissance

Technique : T1046 - Network Service Discovery



DETECTION SOURCE

\----------------

Sysmon Event ID : 3 (Network Connection)

SIEM Platform   : Elastic SIEM (Kibana)

Log shipper     : Winlogbeat 9.4.2



RESPONSE ACTIONS

\----------------

1\. Identified source IP 192.168.56.101 as attacker

2\. Confirmed open port 445 on target

3\. Recommended blocking 192.168.56.101 at firewall level

4\. Monitored for further lateral movement attempts



CONCLUSION

\----------

Attack was successfully detected by SIEM. No data exfiltration

observed. Firewall rules recommended to restrict SMB access

from unauthorized hosts.

