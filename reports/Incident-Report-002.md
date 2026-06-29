INCIDENT REPORT #002

====================

Date: June 28, 2026

Analyst: Ujjal Basnet

Severity: HIGH



EXECUTIVE SUMMARY

\-----------------

A brute force credential attack was detected originating from

192.168.56.101 targeting Windows host 192.168.56.1 via SMB

port 445. The attacker used Metasploit smb\_login scanner with

a custom wordlist. Password was successfully cracked on the

7th attempt after 6 failed logon attempts.



TIMELINE

\--------

00:53:37 - Brute force attack initiated from 192.168.56.101

00:53:37 - Failed attempt 1 — password: admin

00:53:38 - Failed attempt 2 — password: password

00:53:38 - Failed attempt 3 — password: 123456

00:53:39 - Failed attempt 4 — password: letmein

00:53:39 - Failed attempt 5 — password: welcome

00:53:40 - Failed attempt 6 — password: Password1

00:53:40 - SUCCESS — password cracked: Password123

00:53:40 - Attacker gained SMB access to target system



INDICATORS OF COMPROMISE (IOCs)

\--------------------------------

Attacker IP    : 192.168.56.101

Target IP      : 192.168.56.1

Target Port    : 445 (SMB)

Protocol       : TCP

Target User    : labuser

Cracked Pass   : Password123

Tool used      : Metasploit smb\_login scanner

Attempts made  : 7 (6 failed, 1 success)



MITRE ATT\&CK MAPPING

\---------------------

Tactic    : Credential Access (TA0006)

Technique : T1110.001 - Brute Force: Password Guessing



DETECTION SOURCE

\----------------

Windows Event ID : 4625 (Failed Logon) x6

Windows Event ID : 4624 (Successful Logon) x1

SIEM Platform    : Elastic SIEM (Kibana)

Log shipper      : Winlogbeat 9.4.2



RESPONSE ACTIONS

\----------------

1\. Detected 6 consecutive failed logons from 192.168.56.101

2\. Identified successful credential compromise of "labuser"

3\. Immediately disabled labuser account

4\. Recommended account lockout policy: lock after 5 failures

5\. Recommended blocking 192.168.56.101 at firewall level

6\. Recommended enforcing strong password policy



LESSONS LEARNED

\---------------

\- Weak password "Password123" cracked in 7 attempts

\- No account lockout policy was configured — allowed unlimited

&#x20; attempts without triggering a lockout

\- SMB port 445 exposed to internal network without restriction



CONCLUSION

\----------

Brute force attack successfully detected via Windows Security

Event ID 4625 in Elastic SIEM. Attacker gained valid credentials

after 6 failed attempts. Immediate remediation recommended —

disable compromised account and enforce account lockout policy.

