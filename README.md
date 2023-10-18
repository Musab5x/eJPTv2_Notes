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

## Host Discovering:
```
nmap -sn 1.1.1.0/20 
sudo netdiscover -i ent0 -r 1.1.1.0/20 
```
## Network Maping:
```
-wireshark using arpscan
  sudo arp-scan -I tuno -g 1.1.1.1/20
-fping
  fping -I tun0 -g 1.1.1.0/20 -a  2>/dev/null
```






