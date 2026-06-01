# Metasploitable 2 - Penetration Testing Lab

## Disclaimer
This lab was conducted in an isolated, legal envvironment on intentionally vulnerable software for educational purposes only.

## Overview
A home penetration testing lab built using
Metasploitable 2 as the target machine and
Kali Linux 2018 as the attack machine. All
testing conducted on an isolated Host-Only
network in VirtualBox.

## Environment
| Machine          | OS          | IP             | Role     |
|------------------|-------------|----------------|----------|
| Kali Linux 2018  | Debian      | 192.168.56.100 | Attacker |
| Metasploitable 2 | Ubuntu      | 192.168.56.101 | Target   |

![VirtualBox Interface](https://github.com/hemanthyadla/2020-Archive/blob/31ee478426abe9c466b577dcdd7932eabf4ef56b/Metasploitable2-lab/Screenshots/Screenshot%20from%202026-05-21%2011-14-05.png)

![kali Linux](https://github.com/hemanthyadla/2020-Archive/blob/afb1f26aa5d747b4b863c0dbe2ff10395097dcb5/Metasploitable2-lab/Screenshots/Screenshot%20from%202026-05-21%2011-16-07.png)

![metasploit](https://github.com/hemanthyadla/2020-Archive/blob/afb1f26aa5d747b4b863c0dbe2ff10395097dcb5/Metasploitable2-lab/Screenshots/Screenshot%20from%202026-05-21%2011-09-37.png)

# Target Machine IP address
![TargetmachineIPAddress](https://github.com/hemanthyadla/2020-Archive/blob/0b2f0f19f17041ac8e4672a6af87e2365dfdccc0/Metasploitable2-lab/Screenshots/Screenshot%20from%202026-05-22%2009-34-54.png)

## Tools Used
| Tool | Purpose |
|------|---------|
| Nmap | Port scanning and service enumeration |
| Metasploit | Exploitation and scanning |
| Hydra | Credential brute forcing |
| enum4linux | Samba enumeration |
| sqlmap | SQL injection automation |
| Netcat | Manual service interaction |
| iptables | Firewall remediation |

## Documented Ports
| Port | Service | Severity | CVE |
|------|---------|----------|-----|
| 21 | vsftpd FTP | Critical | CVE-2011-2523 |
| 22 | SSH | High | CVE-2008-5161 |
| 23 | Telnet | Critical | N/A |
| 25 | SMTP | Medium | N/A |
| 53 | DNS | High | CVE-2008-1447 |
| 80 | HTTP/DVWA | Critical | CVE-2007-6750 |
| 111 | RPC/NFS | Medium | CVE-2010-4170 |
| 139 | Samba | Critical | CVE-2007-2447 |
| 445 | SMB | Critical | CVE-2007-2447 |
| 512 | rexec | Critical | N/A |
| 513 | rlogin | Critical | N/A |
| 514 | rsh | Critical | N/A |
| 1099 | Java RMI | Critical | CVE-2011-3556 |
| 1524 | Bindshell | Critical | N/A |
| 2049 | NFS | Critical | N/A |
| 2121 | ProFTPD | High | CVE-2010-4221 |
| 3306 | MySQL | High | CVE-2008-0226 |
| 5432 | PostgreSQL | High | CVE-2007-3278 |
| 5900 | VNC | Critical | CVE-2008-4770 |
| 6000 | X11 | High | N/A |
| 6667 | UnrealIRCd | Critical | CVE-2010-2075 |
| 8009 | AJP | Critical | CVE-2020-1938 |
| 8180 | Tomcat | High | CVE-2009-3548 |

## Exploitation Summary
| Port | Method Used | Result |
|------|-------------|--------|
| 21 | Metasploit | Root shell |
| 22 | Hydra brute force | System access |
| 23 | Default credentials | System access |
| 25 | User enumeration | Usernames exposed |
| 53 | Zone transfer | Network topology exposed |
| 80 | SQLi, XSS, CMDi | Database dumped |
| 111 | Metasploit scanner | NFS shares exposed |
| 139 | enum4linux | Usernames exposed |
| 512 | Metasploit scanner | Remote execution |
| 513 | Metasploit scanner | Remote login |
| 514 | Metasploit scanner | Remote shell |
| 1099 | Metasploit scanner | RMI exposed |
| 1524 | Netcat | Instant root shell |
| 2049 | Metasploit scanner | Filesystem exposed |
| 2121 | Metasploit scanner | FTP access |
| 3306 | Metasploit scanner | Database access |
| 5432 | Metasploit scanner | Database access |
| 5900 | Metasploit scanner | Desktop access |
| 6000 | Nmap | X11 exposed |
| 6667 | Metasploit | Root shell |
| 8009 | Nmap | AJP exposed |
| 8180 | Metasploit scanner | Manager access |

## Remediation Applied
| Port | Service | Action Taken | Result |
|------|---------|--------------|--------|
| 21 | FTP | Blocked via iptables | Filtered |
| 23 | Telnet | Blocked via iptables | Filtered |

![ports](https://github.com/hemanthyadla/2020-Archive/blob/6333d29bbd74ffe909ab5622a9dbf89e4d58e25d/Metasploitable2-lab/Screenshots/Screenshot%20from%202026-05-28%2012-12-07.png)
![filter](https://github.com/hemanthyadla/2020-Archive/blob/d34efface32498b735de1439c9f93afa342dd8f9/Metasploitable2-lab/Screenshots/Screenshot%20from%202026-05-28%2012-22-27.png)
## Key Learnings
- Default credentials remain the most
  common vulnerability found
- Legacy services such as Telnet, rsh
  and rexec should never run in production
- Unpatched software from 2007 to 2011
  is still exploitable today
- Defence in depth would have prevented
  most of these attacks
- Patch management is critical for
  maintaining security posture
- Regular port auditing can detect
  unauthorised backdoors
