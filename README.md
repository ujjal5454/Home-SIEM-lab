\# Home SIEM Lab — SOC Analyst Portfolio



A home Security Operations Center (SOC) lab built to simulate

real-world attacks and detect them using an Elastic SIEM stack.



\## Lab Architecture



| Component | Role | Tool |

|-----------|------|------|

| Windows 11 (host) | Victim + SIEM platform | Elasticsearch, Kibana, Sysmon, Winlogbeat |

| Kali Linux (VM) | Attacker machine | Nmap, Netcat, Metasploit |

| VirtualBox | Hypervisor | Host-only network adapter |



\*\*Network:\*\*

\- Attacker: 192.168.56.101 (Kali Linux VM)

\- Victim/SIEM: 192.168.56.1 (Windows 11 host)



\## SIEM Stack



| Tool | Version | Purpose |

|------|---------|---------|

| Elasticsearch | 8.17.0 | Log storage and indexing |

| Kibana | 8.17.0 | Dashboard and detection |

| Sysmon | 15.20 | Windows event enrichment |

| Winlogbeat | 9.4.2 | Log shipping to Elastic |



\## Attacks Simulated



| # | Attack | Tool | MITRE Technique | Detected Via |

|---|--------|------|-----------------|--------------|

| 1 | Network reconnaissance | Netcat | T1046 | Sysmon Event ID 3 |

| 2 | SMB brute force | Metasploit smb\_login | T1110.001 | Windows Event ID 4625 |


## Evidence Screenshots

![Kibana Live Dashboard](Screenshot_2026-06-11 120754.png)
*Kibana Discover showing 944 live Windows events*

![Brute Force Failed Logons](Screenshot_2026-06-28 123544.png)
*Event ID 4625 — 6 failed logon attempts from attacker IP*

![Successful Credential Crack](Screenshot_2026-06-28 123454.png)
*Event ID 4624 — successful login after brute force*



\## Incident Reports



\- \[Incident Report #001 — Network Reconnaissance](reports/Incident-Report-001.md)

\- \[Incident Report #002 — Brute Force Credential Attack](reports/Incident-Report-002.md)



\## Key Skills Demonstrated



\- SIEM deployment and configuration (Elastic stack)

\- Attack simulation in isolated lab environment

\- Log analysis and threat hunting in Kibana

\- MITRE ATT\&CK framework mapping

\- Professional incident report writing

\- Network forensics and IOC identification



\## Technical Challenges Solved



\- Resolved Elasticsearch disk watermark issue by relocating

&#x20; data to secondary drive

\- Fixed Kibana node\_modules corruption caused by Windows

&#x20; Defender — added exclusion rules

\- Configured Sysmon custom rules to detect host-only network

&#x20; traffic from attacker VM

\- Troubleshot VirtualBox NAT vs host-only networking to enable

&#x20; attacker-victim communication



\## Tools and Technologies



Elasticsearch · Kibana · Sysmon · Winlogbeat · Metasploit ·

Nmap · Netcat · Kali Linux · VirtualBox · Windows 11 ·

MITRE ATT\&CK · KQL (Kibana Query Language)

