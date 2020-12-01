# network-traffic
&nbsp;

# Good Articles

How to check open ports in Linux using the CLI
https://www.cyberciti.biz/faq/how-to-check-open-ports-in-linux-using-the-cli/

Linux Find Out Which Process Is Listening Upon a Port
https://www.cyberciti.biz/faq/what-process-has-open-linux-port/

SpeedGuide.net Port 2222 Details
https://www.speedguide.net/port.php?port=2222

Wikipedia List_of_TCP_and_UDP_port_numbers Ports 2222-2226 ESET Remote administrator
https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers

Netcat - How to listen on a TCP port using IPv6 address? example port 2222
https://unix.stackexchange.com/questions/457670/netcat-how-to-listen-on-a-tcp-port-using-ipv6-address

Recommends using ncat 
https://packages.debian.org/buster/ncat

But really prefers using socat
https://packages.debian.org/stretch/socat

ESET Bratislava, Slovak Republic Handles communication with agents, collecting and storing application data.
https://www.eset.com/int/business/remote-administrator/



# Listening on port 2222
```bash
sudo lsof -T | grep 2222

netstat -tulpn
```

### sudo lsof -T | grep 2222
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo lsof -T | grep 2222
sshd        95                      root    3u     IPv4               2712       0t0     TCP *:2222
sshd        95                      root    4u     IPv6               2720       0t0     TCP *:2222
sshd       212                      root    3u     IPv4               6211       0t0     TCP penguin.lxd:2222->100.115.92.25:43998
sshd       221                connorstom    3u     IPv4               6211       0t0     TCP penguin.lxd:2222->100.115.92.25:43998
```

### netstat -tulpn
```bash
connorstom@penguin:~/aprojects/br-build-site$ netstat -tulpn
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN      -                   
tcp6       0      0 :::2222                 :::*                    LISTEN      -                   
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -    
```

### sudo netstat -atupen
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo netstat -atupen
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode      PID/Program name    
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN      0          3856       96/sshd             
tcp        0      0 127.0.0.1:42451         0.0.0.0:*               LISTEN      1000       15581      515/code            
tcp        0      0 100.115.92.195:44960    151.101.116.133:443     ESTABLISHED 1000       22243      379/code --type=uti 
tcp        0      0 100.115.92.195:44962    151.101.116.133:443     ESTABLISHED 1000       22244      379/code --type=uti 
tcp        0      0 100.115.92.195:40324    40.71.11.167:443        ESTABLISHED 1000       23274      379/code --type=uti 
tcp        0      0 100.115.92.195:44958    151.101.116.133:443     ESTABLISHED 1000       22242      379/code --type=uti 
tcp        0      0 100.115.92.195:2222     100.115.92.25:34294     ESTABLISHED 0          6570       243/sshd: connorsto 
tcp6       0      0 :::2222                 :::*                    LISTEN      0          3865       96/sshd             
udp        0      0 0.0.0.0:68              0.0.0.0:*                           0          2345       69/dhclient         
```

### sudo netstat -atupen | grep EST
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo netstat -atupen | grep EST
tcp        0      0 100.115.92.195:44960    151.101.116.133:443     ESTABLISHED 1000       22243      379/code --type=uti 
tcp        0      0 100.115.92.195:44962    151.101.116.133:443     ESTABLISHED 1000       22244      379/code --type=uti 
tcp        0      0 100.115.92.195:40324    40.71.11.167:443        ESTABLISHED 1000       23274      379/code --type=uti 
tcp        0      0 100.115.92.195:44958    151.101.116.133:443     ESTABLISHED 1000       22242      379/code --type=uti 
tcp        0      0 100.115.92.195:2222     100.115.92.25:34294     ESTABLISHED 0          6570       243/sshd: connorsto 
```

### sudo apt-get install whois
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo apt-get install whois
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  whois
0 upgraded, 1 newly installed, 0 to remove and 32 not upgraded.
Need to get 77.8 kB of archives.
After this operation, 364 kB of additional disk space will be used.
Get:1 https://deb.debian.org/debian buster/main amd64 whois amd64 5.4.3 [77.8 kB]
Fetched 77.8 kB in 1s (135 kB/s)
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package whois.
(Reading database ... 40051 files and directories currently installed.)
Preparing to unpack .../archives/whois_5.4.3_amd64.deb ...
Unpacking whois (5.4.3) ...
Setting up whois (5.4.3) ...
Processing triggers for man-db (2.8.5-2) ...
```

### whois 100.115.92.25
```bash
connorstom@penguin:~/aprojects/br-build-site$ whois 100.115.92.25 

NetRange:       100.64.0.0 - 100.127.255.255
CIDR:           100.64.0.0/10
NetName:        SHARED-ADDRESS-SPACE-RFCTBD-IANA-RESERVED
NetHandle:      NET-100-64-0-0-1
Parent:         NET100 (NET-100-0-0-0-0)
NetType:        IANA Special Use
OriginAS:       
Organization:   Internet Assigned Numbers Authority (IANA)
RegDate:        2012-03-13
Updated:        2016-04-11
Comment:        This block is used as Shared Address Space. Traffic from these addresses does not come from IANA. IANA has simply reserved these numbers in its database and does not use or operate them. We are not the source of activity you may see on logs or in e-mail records. Please refer to http://www.iana.org/abuse/ 
Comment:        
Comment:        Shared Address Space can only be used in Service Provider networks or on routing equipment that is able to do address translation across router interfaces when addresses are identical on two different interfaces. 
Comment:        
Comment:        This block was assigned by the IETF in the Best Current Practice document, 
Comment:        RFC 6598 which can be found at: 
Comment:        http://tools.ietf.org/html/rfc6598
Ref:            https://rdap.arin.net/registry/ip/100.64.0.0
```

### sudo ss -tunp
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo ss -tunp
Netid                      State                      Recv-Q                      Send-Q                                            Local Address:Port                                             Peer Address:Port                                                                          
tcp                        ESTAB                      0                           0                                                100.115.92.195:40364                                            40.71.11.167:443                        users:(("code",pid=379,fd=32))                     
tcp                        ESTAB                      0                           0                                                100.115.92.195:2222                                            100.115.92.25:34294                      users:(("sshd",pid=258,fd=3),("sshd",pid=243,fd=3))
```

### sudo lsof -nP -i
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo lsof -nP -i
COMMAND  PID       USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
dhclient  69       root    7u  IPv4   2345      0t0  UDP *:68 
sshd      96       root    3u  IPv4   3856      0t0  TCP *:2222 (LISTEN)
sshd      96       root    4u  IPv6   3865      0t0  TCP *:2222 (LISTEN)
sshd     243       root    3u  IPv4   6570      0t0  TCP 100.115.92.195:2222->100.115.92.25:34294 (ESTABLISHED)
sshd     258 connorstom    3u  IPv4   6570      0t0  TCP 100.115.92.195:2222->100.115.92.25:34294 (ESTABLISHED)
code     379 connorstom   32u  IPv4  39225      0t0  TCP 100.115.92.195:40364->40.71.11.167:443 (ESTABLISHED)
code     515 connorstom   85u  IPv4  15581      0t0  TCP 127.0.0.1:42451 (LISTEN)
```

### sudo lsof -nP -iTCP -sTCP:ESTABLISHED
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo lsof -nP -iTCP -sTCP:ESTABLISHED
COMMAND PID       USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
sshd    243       root    3u  IPv4   6570      0t0  TCP 100.115.92.195:2222->100.115.92.25:34294 (ESTABLISHED)
sshd    258 connorstom    3u  IPv4   6570      0t0  TCP 100.115.92.195:2222->100.115.92.25:34294 (ESTABLISHED)
code    379 connorstom   32u  IPv4  39225      0t0  TCP 100.115.92.195:40364->40.71.11.167:443 (ESTABLISHED)
```

### sudo lsof -nP -iTCP -sTCP:LISTEN
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo lsof -nP -iTCP -sTCP:LISTEN
COMMAND PID       USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
sshd     96       root    3u  IPv4   3856      0t0  TCP *:2222 (LISTEN)
sshd     96       root    4u  IPv6   3865      0t0  TCP *:2222 (LISTEN)
```
