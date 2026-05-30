# Metasploitable 2 - Penetration Testing Lab

## Disclaimer
This lab was conducted in an isolated, legal envvironment on intentionally vulnerable software for educational purposes only.

## Environment
### |   Machine      |    OS      |    Role     |
   
   |Kali Linux 2018 |   Debian   |   Attacker  |
   |Metasploitable2 |   Ubuntu   |   Target    |

## Tools Used
- Nmap
- Metasploit Framework
- Hydra
- enum4linux
- Netcat
- iptables

## Documented Ports
### Port    Service        Severity    Method Used
    21     vfstpd FTP     Critical    Metasploit
    22     SSH            High        Brute force
    23     Telnet         Critical    Default Credentials
    25     SMTP           Medium      User enumeration
    53     DNS            Medium      Zone transfer
    80     HTTP           Critical    SQLi, XSS, CMDi
    111    RPC            High        Metasploit Scanner
    139    Samba          High        enum4linux
    512    rexec          Critical    Metasploit
    513    rlogin         Critical    Metasploit
    514    rsh            Critical    Metasploit
    1099   Java RMI       Critical    Metasploit scanner
    1524   Bindshell      Critical    Netcat
    2049   NFS            Critical    Metasploit Scanner
    2121   ProFTPD        High        Metasploit
    3306   MySQL          Critical    Metasploit
    5432   PostgreSQL     Critical    Metasploit
    5900   VNC            Critical    Metasploit Scanner
    6000   X11            High        Nmap
    6667   IRC            Critical    Metasploit
    8009   AJP13          High        Nmap
    8180   Tomcat         Critical    Metasploit

## Remediation
### Port       Service       Action Taken
     21      FTP        Blocked via iptables
     23      Telnet     Blocked via iptables
