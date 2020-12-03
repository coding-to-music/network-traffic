# network-traffic
&nbsp;

# What is using my port 2222 ????
## On both my chromebooks

# Good Articles

### Down The Rabbit Hole: How Hackers Exploit Weak SSH Credentials To Build DDoS Botnets by Christophe Tafani-Dereeper @christophetd 57 excellent slides
https://www.blackalps.ch/ba-17/files/talks/BlackAlps17-Tafani.pdf

### How to check open ports in Linux using the CLI
https://www.cyberciti.biz/faq/how-to-check-open-ports-in-linux-using-the-cli/

### Linux Find Out Which Process Is Listening Upon a Port
https://www.cyberciti.biz/faq/what-process-has-open-linux-port/

### Wikipedia List_of_TCP_and_UDP_port_numbers Ports 2222-2226 ESET Remote administrator
https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers

### Netcat - How to listen on a TCP port using IPv6 address? example port 2222
https://unix.stackexchange.com/questions/457670/netcat-how-to-listen-on-a-tcp-port-using-ipv6-address

### Recommends using ncat 
https://packages.debian.org/buster/ncat

### But really prefers using socat
https://packages.debian.org/stretch/socat

### ESET Bratislava, Slovak Republic Handles communication with agents, collecting and storing application data.
https://www.eset.com/int/business/remote-administrator/


### SpeedGuide.net Port 2222 Details
https://www.speedguide.net/port.php?port=2222

<p align="center">
 <img width="800px" src="https://github.com/coding-to-music/network-traffic/blob/main/Port-2222-uses.png?raw=true" align="center" alt="SpeedGuide.net Port 2222 Details" />
 
## ESET Linux proxy install instructions example, is this similar to what is running?
### Example of an installation script from ESET
https://help.eset.com/era_install/65/en-US/proxy_installation_linux.html
```bash
./proxy-linux-x86_64.sh \
--db-hostname=10.1.179.28 \
--db-name=era_6_db_proxy \
--db-admin-username=sa \
--db-admin-password=admin.1 \
--db-user-username=tester \
--db-user-password=Admin.1 \
--db-port=1433 \
--db-type="MS SQL Server" \
--db-driver=MySQL \
--skip-license \
--hostname=10.1.179.30 \
--port=2222 \
--cert-path=/home/adminko/Desktop/proxy.pfx \
--cert-auth-path=/home/adminko/Desktop/CA-server.der \
--cert-password=root \
```

### How to install lsof
```bash
sudo apt-get update

sudo apt-get install lsof

sudo lsof -T | grep 2222

netstat -tulpn
```

## lsof Command Example
### Type the command as follows:
```bash
lsof -i :portNumber 
lsof -i tcp:portNumber 
lsof -i udp:portNumber 
lsof -i :80
lsof -i :80 | grep LISTEN
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
tcp        0      0 100.115.92.195:40630    40.71.11.167:443        ESTABLISHED 1000       101991     379/code --type=uti 
tcp        0      0 100.115.92.195:2222     100.115.92.25:34294     ESTABLISHED 0          6570       243/sshd: connorsto 
```

### sudo netstat -atupen | grep 2222
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo netstat -atupen | grep 2222
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN      0          3856       96/sshd             
tcp        0      0 100.115.92.195:2222     100.115.92.25:34294     ESTABLISHED 0          6570       243/sshd: connorsto 
tcp6       0      0 :::2222                 :::*                    LISTEN      0          3865       96/sshd 
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
Netid   State    Recv-Q    Send-Q        Local Address:Port         Peer Address:Port                                      
tcp     ESTAB    0         0            100.115.92.195:40630        40.71.11.167:443      users:(("code",pid=379,fd=27))   
tcp     ESTAB    0         0            100.115.92.195:2222        100.115.92.25:34294    users:(("sshd",pid=258,fd=3),("sshd",pid=243,fd=3))
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
code     379 connorstom   27u  IPv4 101991      0t0  TCP 100.115.92.195:40630->40.71.11.167:443 (ESTABLISHED)
code     515 connorstom   85u  IPv4  15581      0t0  TCP 127.0.0.1:42451 (LISTEN)
```
### sudo lsof -nP -i | grep 2222
```bash
sshd      96       root    3u  IPv4   3856      0t0  TCP *:2222 (LISTEN)
sshd      96       root    4u  IPv6   3865      0t0  TCP *:2222 (LISTEN)
sshd     243       root    3u  IPv4   6570      0t0  TCP 100.115.92.195:2222->100.115.92.25:34294 (ESTABLISHED)
sshd     258 connorstom    3u  IPv4   6570      0t0  TCP 100.115.92.195:2222->100.115.92.25:34294 (ESTABLISHED)
```

### sudo apt-get install ncat
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo apt-get install ncat
```

### sudo apt-get install socat
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo apt-get install socat
```

### sudo grep -Rl "2222" /
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo grep -Rl "2222" /

nothing came back, killed process
```

### sudo lsof -nP -i | grep 2222
```bash
connorstom@penguin:~/aprojects/network-traffic$ sudo lsof -nP -i | grep 2222
sshd      96       root    3u  IPv4   3856      0t0  TCP *:2222 (LISTEN)
sshd      96       root    4u  IPv6   3865      0t0  TCP *:2222 (LISTEN)
sshd     243       root    3u  IPv4   6570      0t0  TCP 100.115.92.195:2222->100.115.92.25:34294 (ESTABLISHED)
sshd     258 connorstom    3u  IPv4   6570      0t0  TCP 100.115.92.195:2222->100.115.92.25:34294 (ESTABLISHED)
```

### sudo lsof -nP -i
```bash
connorstom@penguin:~/aprojects/network-traffic$ sudo lsof -nP -i 
COMMAND  PID       USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
dhclient  69       root    7u  IPv4   2345      0t0  UDP *:68 
sshd      96       root    3u  IPv4   3856      0t0  TCP *:2222 (LISTEN)
sshd      96       root    4u  IPv6   3865      0t0  TCP *:2222 (LISTEN)
sshd     243       root    3u  IPv4   6570      0t0  TCP 100.115.92.195:2222->100.115.92.25:34294 (ESTABLISHED)
sshd     258 connorstom    3u  IPv4   6570      0t0  TCP 100.115.92.195:2222->100.115.92.25:34294 (ESTABLISHED)
code     379 connorstom   33u  IPv4 150970      0t0  TCP 100.115.92.195:40786->40.71.11.167:443 (ESTABLISHED)
code     515 connorstom   85u  IPv4  15581      0t0  TCP 127.0.0.1:42451 (LISTEN)
```

## Find Out Current Working Directory Of a Process

### sudo ls -l /proc/96/exe
```bash
connorstom@penguin:~/aprojects/network-traffic$ sudo ls -l /proc/96/exe
lrwxrwxrwx. 1 root root 0 Dec  1 16:51 /proc/96/exe -> /usr/sbin/sshd
connorstom@penguin:~/aprojects/network-traffic$ sudo ls -l /proc/243/exe
lrwxrwxrwx. 1 root root 0 Dec  1 16:51 /proc/243/exe -> /usr/sbin/sshd
connorstom@penguin:~/aprojects/network-traffic$ sudo ls -l /proc/258/exe
lrwxrwxrwx. 1 root root 0 Dec  1 16:52 /proc/258/exe -> /usr/sbin/sshd
```

### whatis sshd
```bash
connorstom@penguin:~/aprojects/network-traffic$ whatis sshd
sshd (8)             - OpenSSH SSH daemon
connorstom@penguin:~/aprojects/network-traffic$ sudo ls -l /proc/258/cwd
lrwxrwxrwx. 1 root root 0 Dec  1 16:53 /proc/258/cwd -> /
connorstom@penguin:~/aprojects/network-traffic$ sudo ls -l /proc/243/cwd
lrwxrwxrwx. 1 root root 0 Dec  1 16:53 /proc/243/cwd -> /
connorstom@penguin:~/aprojects/network-traffic$ sudo ls -l /proc/96/cwd
lrwxrwxrwx. 1 root root 0 Dec  1 16:53 /proc/96/cwd -> /
```

### sudo pwdx 258
```bash
connorstom@penguin:~/aprojects/network-traffic$ pwdx 258
258: Permission denied
connorstom@penguin:~/aprojects/network-traffic$ sudo pwdx 258
258: /
connorstom@penguin:~/aprojects/network-traffic$ sudo pwdx 96
96: /
```
## Find Out Owner Of a Process on Linux
### ps aux | grep 96
```bash
connorstom@penguin:~/aprojects/network-traffic$ ps aux | grep 96
root        94  0.0  0.0   5384  1512 pts/0    Ss+  13:44   0:00 /sbin/agetty -o -p -- \u --noclear --keep-baud console 115200,38400,9600 vt220
root        96  0.0  0.0  15852  2148 ?        Ss   13:44   0:00 /usr/sbin/sshd -D -f /dev/.ssh/sshd_config
connors+   173  1.0  1.1 377496 32700 ?        Sl   13:45   2:00 /opt/google/cros-containers/bin/../lib/ld-linux-x86-64.so.2 --library-path /opt/google/cros-containers/bin/../lib --inhibit-rpath  /opt/google/cros-containers/bin/Xwayland.elf -nolisten tcp -rootless -displayfd 23 -wm 24 -auth /home/connorstom/.Xauthority -fp /usr/share/fonts/X11/misc, /usr/share/fonts/X11/cyrillic, /usr/share/fonts/X11/100dpi/:unscaled, /usr/share/fonts/X11/75dpi/:unscaled, /usr/share/fonts/X11/Type1, /usr/share/fonts/X11/100dpi, /usr/share/fonts/X11/75dpi, built-ins
root       249  0.0  0.0 239964  1268 ?        Ssl  13:45   0:00 /usr/lib/policykit-1/polkitd --no-debug
connors+   394  0.0  0.0   8964  2320 ?        Ss   13:45   0:04 /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
connors+   405  3.2  4.4 15199676 127524 ?     Sl   13:45   6:11 /usr/share/code/code --type=renderer --disable-color-correct-rendering --no-sandbox --field-trial-handle=17507012646794649728,6013345945898835886,131072 --enable-features=WebComponentsV0Enabled --disable-features=SpareRendererForSitePerProcess --lang=en-US --enable-crash-reporter=1ab5bc38-ae48-489e-b588-5aaf5e920939,no_channel --global-crash-keys=1ab5bc38-ae48-489e-b588-5aaf5e920939,no_channel,_companyName=Microsoft,_productName=VSCode,_version=1.51.1 --standard-schemes=vscode-webview,vscode-webview-resource --secure-schemes=vscode-webview,vscode-webview-resource --bypasscsp-schemes --cors-schemes=vscode-webview,vscode-webview-resource --fetch-schemes=vscode-webview,vscode-webview-resource --service-worker-schemes --app-path=/usr/share/code/resources/app --node-integration --webview-tag --no-sandbox --no-zygote --native-window-open --preload=/usr/share/code/resources/app/out/vs/base/parts/sandbox/electron-browser/preload.js --background-color=#1e1e1e --num-raster-threads=1 --renderer-client-id=5 --no-v8-untrusted-code-mitigations --shared-files=v8_snapshot_data:100
connors+   533  0.0  0.1   7916  3396 pts/0    Ss+  13:45   0:00 /bin/bash
connors+  3696  0.0  0.1   8048  4600 pts/2    Ss   14:58   0:00 /bin/bash
root      6358  0.0  0.1  10296  3236 pts/1    S+   16:37   0:00 sudo grep -Rl 2222 /
connors+  6529  0.0  0.0   6076   896 pts/2    S+   16:54   0:00 grep 96

```

### ps aux | grep 258
```bash
connorstom@penguin:~/aprojects/network-traffic$ ps aux | grep 258
connors+   258  0.0  0.0  16992  2356 ?        S    13:45   0:00 sshd: connorstom@notty
connors+  6535  0.0  0.0   6076   892 pts/2    S+   16:55   0:00 grep 258
connorstom@penguin:~/aprojects/network-traffic$ ps aux | grep 243
root       243  0.0  0.0  16992  2788 ?        Ss   13:45   0:00 sshd: connorstom [priv]
connors+  6537  0.0  0.0   6076   896 pts/2    S+   16:55   0:00 grep 243
```

### ps -eo pid,user,group,args,etime,lstart | grep '96'
```bash
connorstom@penguin:~/aprojects/network-traffic$ ps -eo pid,user,group,args,etime,lstart | grep '96'
   96 root     root     /usr/sbin/sshd -D -f /dev/.    03:11:07 Tue Dec  1 13:44:59 2020
 3696 connors+ connors+ /bin/bash                      01:57:49 Tue Dec  1 14:58:17 2020
 6546 connors+ connors+ grep 96                           00:00 Tue Dec  1 16:56:24 2020
connorstom@penguin:~/aprojects/network-traffic$ ps -eo pid,user,group,args,etime,lstart | grep '243'
  243 root     root     sshd: connorstom [priv]        03:11:20 Tue Dec  1 13:45:07 2020
 6548 connors+ connors+ grep 243                          00:00 Tue Dec  1 16:56:45 2020
connorstom@penguin:~/aprojects/network-traffic$ ps -eo pid,user,group,args,etime,lstart | grep '258'
  258 connors+ connors+ sshd: connorstom@notty         03:11:40 Tue Dec  1 13:45:08 2020
 6555 connors+ connors+ grep 258                          00:00 Tue Dec  1 16:57:06 2020
```

### ps aux | grep notty
```bash
connorstom@penguin:~/aprojects/network-traffic$ ps aux | grep notty
connors+   258  0.0  0.0  16992  2356 ?        S    13:45   0:00 sshd: connorstom@notty
connors+  6574  0.0  0.0   6208   828 pts/2    S+   17:02   0:00 grep notty
```

### cat /proc/96/environ
```bash
connorstom@penguin:~/aprojects/network-traffic$ cat /proc/96/environ
cat: /proc/96/environ: Permission denied
connorstom@penguin:~/aprojects/network-traffic$ sudo cat /proc/96/environ
LANG=en_US.UTF-8PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/binNOTIFY_SOCKET=/run/systemd/notifyINVOCATION_ID=0d3d1a8ff3c4458889bcccc64b14e4dcJOURNAL_STREAM=8:3836RUNTIME_DIRECTORY=/run/sshd
```

## Help: I Discover an Open Port Which I Don’t Recognize At All
### grep port /etc/services
```bash
connorstom@penguin:~/aprojects/network-traffic$ grep port /etc/services
# port number for both TCP and UDP; hence, officially ports have two entries
# even if the protocol doesn't support UDP operations.
# Updated from https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml .
# New ports will be added on request if they have been officially assigned
tcpmux          1/tcp                           # TCP port service multiplexer
sunrpc          111/tcp         portmapper      # RPC 4.0 portmapper
sunrpc          111/udp         portmapper
mailq           174/tcp                 # Mailer transport queue for Zmailer
rpc2portmap     369/tcp
rpc2portmap     369/udp                         # Coda portmapper
imsp            406/tcp                 # Interactive Mail Support Protocol
tinc            655/tcp                         # tinc control port
#> providing services to unknown callers, a service contact port is
#> defined.  This list specifies the port used by the server process as its
#> contact port.  While the IANA can not control uses of these ports it
#> does register or list uses of these ports as a convienence to the
sa-msg-port     1646/tcp        old-radacct
sa-msg-port     1646/udp        old-radacct
venus           2430/tcp                        # codacon port
codasrv         2432/udp                        # server port
radmin-port     4899/tcp                        # RAdmin Port
radmin-port     4899/udp
# The remaining port numbers are not as allocated by IANA.
skkserv         1178/tcp                        # skk jisho server port
support         1529/tcp                        # GNATS
sane-port       6566/tcp        sane saned      # SANE network scanner daemon
```

### sudo apt-get install fd-find
```bash
connorstom@penguin:~/aprojects/network-traffic$ sudo apt-get install fd-find

connorstom@penguin:~/aprojects/network-traffic$ fdfind 2222 /
/home/connorstom/aprojects/network-traffic/Port-2222-uses.png

```

### sudo apt-get install tcpdump
https://linuxize.com/post/tcpdump-command-in-linux/
```bash
connorstom@penguin:~/aprojects/network-traffic$ sudo apt-get install tcpdump

Options
-i any : Listen on all interfaces just to see if you’re seeing any traffic.
-i eth0 : Listen on the eth0 interface.
-D : Show the list of available interfaces
-n : Don’t resolve hostnames.
-nn : Don’t resolve hostnames or port names.
-q : Be less verbose (more quiet) with your output.
-t : Give human-readable timestamp output.
-tttt : Give maximally human-readable timestamp output.
-X : Show the packet’s contents in both hex and ASCII.
-XX : Same as -X, but also shows the ethernet header.
-v, -vv, -vvv : Increase the amount of packet information you get back.
-c : Only get x number of packets and then stop.
-s : Define the size of the capture in bytes. Use -s0 to get everything, unless you are intentionally capturing less.
-S : Print absolute sequence numbers.
-e : Get the ethernet header as well.
-q : Show less protocol information.
-E : Decrypt IPSEC traffic by providing an encryption key.

There are three main types of expression: type, dir, and proto.

Type options are: host, net, and port.
Direction lets you do src, dst, and combinations thereof.
Proto(col) lets you designate: tcp, udp, icmp, ah, and many more.

connorstom@penguin:~/aprojects/go-vue-sourcefiles$ tcpdump -D
1.eth0 [Up, Running]
2.any (Pseudo-device that captures on all interfaces) [Up, Running]
3.lo [Up, Running, Loopback]
4.nflog (Linux netfilter log (NFLOG) interface)
5.nfqueue (Linux netfilter queue (NFQUEUE) interface)
6.usbmon1 (USB bus number 1)
7.usbmon2 (USB bus number 2)

connorstom@penguin:~/aprojects/goColorsTests$ sudo tcpdump -nAtvvv       port 2222
connorstom@penguin:~/aprojects/goColorsTests$ sudo tcpdump -nAtvvv   src port 2222
connorstom@penguin:~/aprojects/goColorsTests$ sudo tcpdump -nAtvvvX  src port 2222
connorstom@penguin:~/aprojects/goColorsTests$ sudo tcpdump -nAtvvvXX src port 2222

connorstom@penguin:~/aprojects/go-vue-sourcefiles$ sudo tcpdump -n -A port 2222
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
```

### sudo apt-get install nmap
https://nmap.org/book/install.html#inst-already
```bash
connorstom@penguin:~/aprojects/network-traffic$ nmap --version
Nmap version 7.70 ( https://nmap.org )
Platform: x86_64-pc-linux-gnu
Compiled with: liblua-5.3.3 openssl-1.1.1d libssh2-1.8.0 libz-1.2.11 libpcre-8.39 libpcap-1.8.1 nmap-libdnet-1.12 ipv6
Compiled without:
Available nsock engines: epoll poll select

connorstom@penguin:~/aprojects/network-traffic$ nmap -A -T4 scanme.nmap.org
Starting Nmap 7.70 ( https://nmap.org ) at 2020-12-02 02:15 EST
Nmap scan report for scanme.nmap.org (45.33.32.156)
Host is up (0.093s latency).
Other addresses for scanme.nmap.org (not scanned): 2600:3c01::f03c:91ff:fe18:bb2f
Not shown: 992 closed ports
PORT      STATE    SERVICE      VERSION
22/tcp    open     ssh          OpenSSH 6.6.1p1 Ubuntu 2ubuntu2.13 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   1024 ac:00:a0:1a:82:ff:cc:55:99:dc:67:2b:34:97:6b:75 (DSA)
|   2048 20:3d:2d:44:62:2a:b0:5a:9d:b5:b3:05:14:c2:a6:b2 (RSA)
|   256 96:02:bb:5e:57:54:1c:4e:45:2f:56:4c:4a:24:b2:57 (ECDSA)
|_  256 33:fa:91:0f:e0:e1:7b:1f:6d:05:a2:b0:f1:54:41:56 (ED25519)
25/tcp    filtered smtp
80/tcp    open     http         Apache httpd 2.4.7 ((Ubuntu))
|_http-server-header: Apache/2.4.7 (Ubuntu)
|_http-title: Go ahead and ScanMe!
135/tcp   filtered msrpc
139/tcp   filtered netbios-ssn
445/tcp   filtered microsoft-ds
9929/tcp  open     nping-echo   Nping echo
31337/tcp open     tcpwrapped
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 19.41 seconds
```


### sudo apt-get install wireshark
```bash
connorstom@penguin:~/aprojects/network-traffic$ sudo apt-get install wireshark

// got this error: “couldnt run /usr/bin/dumpcap in child process

sudo dpkg-reconfigure wireshark-common
// answer Yes to letting non-supervisors use wireshark

sudo chmod +x /usr/bin/dumpcap
```

### After reboot, Check what ip address is using port 2222 
```bash
connorstom@penguin:~/aprojects/network-traffic$ sudo netstat -atupen | grep 2222
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN      0          3664       97/sshd             
tcp        0      0 100.115.92.195:2222     100.115.92.25:36440     ESTABLISHED 0          5074       245/sshd: connorsto 
tcp6       0      0 :::2222                 :::*                    LISTEN      0          3666       97/sshd             
connorstom@penguin:~/aprojects/network-traffic$ sudo netstat -atupen
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode      PID/Program name    
tcp        0      0 127.0.0.1:40609         0.0.0.0:*               LISTEN      1000       11295      514/code            
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN      0          3664       97/sshd             
tcp        0      0 100.115.92.195:35394    151.101.116.133:443     ESTABLISHED 1000       25280      376/code --type=uti 
tcp        0      0 100.115.92.195:55000    40.71.11.167:443        ESTABLISHED 1000       75504      376/code --type=uti 
tcp        0      0 100.115.92.195:2222     100.115.92.25:36440     ESTABLISHED 0          5074       245/sshd: connorsto 
tcp6       0      0 :::2222                 :::*                    LISTEN      0          3666       97/sshd             
udp        0      0 0.0.0.0:68              0.0.0.0:*                           0          3442       69/dhclient         
connorstom@penguin:~/aprojects/network-traffic$ netstat -tulpn
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 127.0.0.1:40609         0.0.0.0:*               LISTEN      514/code            
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN      -                   
tcp6       0      0 :::2222                 :::*                    LISTEN      -                   
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -                   
connorstom@penguin:~/aprojects/network-traffic$ sudo lsof -nP -i | grep 2222
sshd      97       root    3u  IPv4   3664      0t0  TCP *:2222 (LISTEN)
sshd      97       root    4u  IPv6   3666      0t0  TCP *:2222 (LISTEN)
sshd     245       root    3u  IPv4   5074      0t0  TCP 100.115.92.195:2222->100.115.92.25:36440 (ESTABLISHED)
sshd     255 connorstom    3u  IPv4   5074      0t0  TCP 100.115.92.195:2222->100.115.92.25:36440 (ESTABLISHED)
```

### Using wireshark, can filter on port and ip_address, can see vscode in the contents 
```bash
// filters such as:
tcp.port == 2222 || udp.port == 2222

tcp contains 2222

tcp contains vscode

ip.addr == 100.115.92.25
```


### can see vscode in the contents but turns out it is not port 2222 
<p align="center">
 <img width="800px" src="https://github.com/coding-to-music/network-traffic/blob/main/vscode-wireshark.png?raw=true" align="center" alt="vscode in the contents" />

### This is traffic leaving 2222 and going to the mystery ip address 
<p align="center">
 <img width="800px" src="https://github.com/coding-to-music/network-traffic/blob/main/wireshark-port-2222.png?raw=true" align="center" alt="vscode in the contents" />
