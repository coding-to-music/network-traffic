# network-traffic
&nbsp;

# What is using my port 2222 ????
## On both my chromebooks

- [network-traffic](#network-traffic)
- [What is using my port 2222 ????](#what-is-using-my-port-2222-)
  - [On both my chromebooks](#on-both-my-chromebooks)
- [Good Articles](#good-articles)
    - [Down The Rabbit Hole: How Hackers Exploit Weak SSH Credentials To Build DDoS Botnets by Christophe Tafani-Dereeper @christophetd 57 excellent slides](#down-the-rabbit-hole-how-hackers-exploit-weak-ssh-credentials-to-build-ddos-botnets-by-christophe-tafani-dereeper-christophetd-57-excellent-slides)
    - [SSH Penetration Testing (Port 22)](#ssh-penetration-testing-port-22)
    - [How to check open ports in Linux using the CLI](#how-to-check-open-ports-in-linux-using-the-cli)
    - [Linux Find Out Which Process Is Listening Upon a Port](#linux-find-out-which-process-is-listening-upon-a-port)
    - [Wikipedia List_of_TCP_and_UDP_port_numbers Ports 2222-2226 ESET Remote administrator](#wikipedia-list_of_tcp_and_udp_port_numbers-ports-2222-2226-eset-remote-administrator)
    - [Netcat - How to listen on a TCP port using IPv6 address? example port 2222](#netcat---how-to-listen-on-a-tcp-port-using-ipv6-address-example-port-2222)
    - [Recommends using ncat](#recommends-using-ncat)
    - [But really prefers using socat](#but-really-prefers-using-socat)
    - [ESET Bratislava, Slovak Republic Handles communication with agents, collecting and storing application data.](#eset-bratislava-slovak-republic-handles-communication-with-agents-collecting-and-storing-application-data)
    - [SpeedGuide.net Port 2222 Details](#speedguidenet-port-2222-details)
- [Overview of commands and purpose](#overview-of-commands-and-purpose)
- [cat /proc/96/environ](#cat-proc96environ)
- [dsmeg](#dsmeg)
    - [dmesg | grep port](#dmesg--grep-port)
- [fd-find](#fd-find)
    - [sudo apt-get install fd-find](#sudo-apt-get-install-fd-find)
- [Fuser](#fuser)
    - [sudo fuser -v -n tcp 2222](#sudo-fuser--v--n-tcp-2222)
- [sudo journalctl # grep 2222](#sudo-journalctl--grep-2222)
    - [sudo journalctl | grep 2222](#sudo-journalctl--grep-2222-1)
- [sudo journalctl -u getty.target](#sudo-journalctl--u-gettytarget)
    - [sudo journalctl -u getty.target](#sudo-journalctl--u-gettytarget-1)
- [ls -l /proc/96/ext # working dir of a process](#ls--l-proc96ext--working-dir-of-a-process)
  - [Find Out Current Working Directory Of a Process](#find-out-current-working-directory-of-a-process)
    - [sudo ls -l /proc/96/exe](#sudo-ls--l-proc96exe)
- [lsof](#lsof)
    - [How to install lsof](#how-to-install-lsof)
  - [lsof Command Example](#lsof-command-example)
    - [Type the command as follows:](#type-the-command-as-follows)
    - [sudo lsof -T | grep 2222](#sudo-lsof--t--grep-2222)
    - [sudo lsof -nP -i](#sudo-lsof--np--i)
    - [sudo lsof -nP -i | grep 2222](#sudo-lsof--np--i--grep-2222)
    - [sudo lsof -nP -i](#sudo-lsof--np--i-1)
- [ncat](#ncat)
    - [sudo apt-get install ncat](#sudo-apt-get-install-ncat)
- [nmap](#nmap)
    - [sudo apt-get install nmap](#sudo-apt-get-install-nmap)
  - [Nightmare write-up by 0xEA31 about port 2222 exploits](#nightmare-write-up-by-0xea31-about-port-2222-exploits)
  - [nmap fast check out my own ip_addr](#nmap-fast-check-out-my-own-ip_addr)
    - [nmap -T5 -p- -vvv -oA full_T5 100.115.92.195](#nmap--t5--p---vvv--oa-full_t5-10011592195)
    - [nmap -vv --reason -Pn -A --osscan-guess --version-all -p- 100.115.92.195](#nmap--vv---reason--pn--a---osscan-guess---version-all--p--10011592195)
    - [nmap -sV -p2222 100.115.92.195](#nmap--sv--p2222-10011592195)
    - [nmap -sV -p22 100.115.92.195](#nmap--sv--p22-10011592195)
  - [nmap targeted (my own ip_id)](#nmap-targeted-my-own-ip_id)
    - [nmap -A -p80,2222- -vvv -oA targeted 100.115.92.195](#nmap--a--p802222---vvv--oa-targeted-10011592195)
    - [nmap -A -T4 scanme.nmap.org](#nmap--a--t4-scanmenmaporg)
- [netstat](#netstat)
    - [depends if you are sudo or not](#depends-if-you-are-sudo-or-not)
    - [sudo netstat -tunlp](#sudo-netstat--tunlp)
    - [netstat -tulpn](#netstat--tulpn)
    - [sudo netstat -atupen](#sudo-netstat--atupen)
    - [sudo netstat -atupen | grep EST](#sudo-netstat--atupen--grep-est)
    - [sudo netstat -atupen | grep 2222](#sudo-netstat--atupen--grep-2222)
- [nikto](#nikto)
  - [Nikto Installation](#nikto-installation)
    - [Run nikto normally:](#run-nikto-normally)
    - [Nikto Run as a Docker container:](#nikto-run-as-a-docker-container)
    - [Starting a Nikto Web Scan](#starting-a-nikto-web-scan)
- [nmap -vv --reason -Pn -A --osscan-guess --version-all -p- 100.115.92.195](#nmap--vv---reason--pn--a---osscan-guess---version-all--p--10011592195-1)
- [ps -aux](#ps--aux)
  - [Find Out Owner Of a Process on Linux](#find-out-owner-of-a-process-on-linux)
    - [ps -aux](#ps--aux-1)
    - [ps aux | grep 96](#ps-aux--grep-96)
    - [ps aux | grep 258](#ps-aux--grep-258)
    - [ps -eo pid,user,group,args,etime,lstart | grep '96'](#ps--eo-pidusergroupargsetimelstart--grep-96)
    - [ps aux | grep notty](#ps-aux--grep-notty)
- [ps -eo pid,lstart,cmd # When did a process first start?](#ps--eo-pidlstartcmd--when-did-a-process-first-start)
- [ps -feww](#ps--feww)
- [pstree](#pstree)
    - [pstree -a](#pstree--a)
- [sudo pwdx 258](#sudo-pwdx-258)
  - [need more info about pwdx](#need-more-info-about-pwdx)
- [Socat](#socat)
    - [sudo apt-get install socat](#sudo-apt-get-install-socat)
    - [socat/EXAMPLES](#socatexamples)
- [ss](#ss)
    - [socket statistics command (i.e. ss)](#socket-statistics-command-ie-ss)
    - [sudo ss -tunp](#sudo-ss--tunp)
    - [sudo ss -lptn 'sport = :2222'](#sudo-ss--lptn-sport--2222)
    - [socket statistics command (i.e. ss)](#socket-statistics-command-ie-ss-1)
- [init.d directory](#initd-directory)
    - [README-create-debian-startup-script.md](#readme-create-debian-startup-scriptmd)
  - [Debian Boot Process](#debian-boot-process)
  - [Get To Know Linux: The /etc/init.d Directory](#get-to-know-linux-the-etcinitd-directory)
    - [All scripts executed by the init system are located in the directory /etc/init.d/](#all-scripts-executed-by-the-init-system-are-located-in-the-directory-etcinitd)
  - [init. d contains the start/stop scripts the daemon while the system is running or during boot](#init-d-contains-the-startstop-scripts-the-daemon-while-the-system-is-running-or-during-boot)
    - [Get To Know Linux: The /etc/init.d Directory](#get-to-know-linux-the-etcinitd-directory-1)
- [Linux Runlevel programs](#linux-runlevel-programs)
- [Chart: systemctl vs service tools](#chart-systemctl-vs-service-tools)
    - [systemctl status 2185](#systemctl-status-2185)
- [systemctl](#systemctl)
    - [systemctl status 2185](#systemctl-status-2185-1)
    - [systemctl status $(pgrep perl)](#systemctl-status-pgrep-perl)
  - [How To List Startup Services At Boot In Linux](#how-to-list-startup-services-at-boot-in-linux)
  - [to stop a service **permanently** in debian](#to-stop-a-service-permanently-in-debian)
- [systemctl status getty.target](#systemctl-status-gettytarget)
  - [systemctl list-dependencies](#systemctl-list-dependencies)
    - [systemctl status getty.target](#systemctl-status-gettytarget-1)
    - [systemctl list-sockets](#systemctl-list-sockets)
    - [View the logs in /var/log](#view-the-logs-in-varlog)
- [systemd journal files](#systemd-journal-files)
    - [How to inspect systemd journal files directly?](#how-to-inspect-systemd-journal-files-directly)
- [tcpdump](#tcpdump)
    - [sudo apt-get install tcpdump](#sudo-apt-get-install-tcpdump)
    - [To view available devices    sudo tcpdump -D](#to-view-available-devices----sudo-tcpdump--d)
    - [sudo tcpdump -vvv -i eth0 port 2222](#sudo-tcpdump--vvv--i-eth0-port-2222)
    - [sudo tcpdump -v -i eth0 dst 100.115.92.25](#sudo-tcpdump--v--i-eth0-dst-1001159225)
    - [sudo tcpdump -nAtvvvXX src port 2222](#sudo-tcpdump--natvvvxx-src-port-2222)
    - [top -p 1859](#top--p-1859)
    - [sudo apt-get install whois](#sudo-apt-get-install-whois)
    - [whois 100.115.92.25](#whois-1001159225)
- [wireshark](#wireshark)
    - [sudo apt-get install wireshark](#sudo-apt-get-install-wireshark)
    - [Using wireshark, can filter on port and ip_address, can see vscode in the contents](#using-wireshark-can-filter-on-port-and-ip_address-can-see-vscode-in-the-contents)
    - [can see vscode in the contents but turns out it is not port 2222](#can-see-vscode-in-the-contents-but-turns-out-it-is-not-port-2222)
    - [This is traffic leaving 2222 and going to the mystery ip address](#this-is-traffic-leaving-2222-and-going-to-the-mystery-ip-address)
- [End of document](#end-of-document)
        - [End of document](#end-of-document-1)
        - [End of document](#end-of-document-2)
        - [End of document](#end-of-document-3)
        - [End of document](#end-of-document-4)
        - [End of document](#end-of-document-5)
        - [End of document](#end-of-document-6)
        - [End of document](#end-of-document-7)
        - [End of document](#end-of-document-8)
        - [End of document](#end-of-document-9)
        - [End of document](#end-of-document-10)
        - [End of document](#end-of-document-11)
        - [End of document](#end-of-document-12)
        - [End of document](#end-of-document-13)
- [Trying various commands](#trying-various-commands)
  - [ESET Linux proxy install instructions example, is this similar to what is running?](#eset-linux-proxy-install-instructions-example-is-this-similar-to-what-is-running)
    - [Example of an installation script from ESET](#example-of-an-installation-script-from-eset)
    - [Simple way to start analysis](#simple-way-to-start-analysis)
    - [cat /proc/96/environ](#cat-proc96environ-1)
  - [Help: I Discover an Open Port Which I Don’t Recognize At All](#help-i-discover-an-open-port-which-i-dont-recognize-at-all)
    - [grep port /etc/services](#grep-port-etcservices)
    - [After reboot, Check what ip address is using port 2222](#after-reboot-check-what-ip-address-is-using-port-2222)
    - [The usual key indicators of port 2222](#the-usual-key-indicators-of-port-2222)
    - [SSH Penetration Testing (Port 22)](#ssh-penetration-testing-port-22-1)
  - [openssh-server](#openssh-server)
    - [SSH Penetration Testing (Port 22)](#ssh-penetration-testing-port-22-2)
    - [edit /etc/ssh/sshd_config](#edit-etcsshsshd_config)
- [Misc](#misc)
    - [ls -al /proc/](#ls--al-proc)
    - [When did a process first start?   ps -eo pid,lstart,cmd](#when-did-a-process-first-start---ps--eo-pidlstartcmd)
  - [cat /proc/2177/status](#cat-proc2177status)

# Good Articles

### Down The Rabbit Hole: How Hackers Exploit Weak SSH Credentials To Build DDoS Botnets by Christophe Tafani-Dereeper @christophetd 57 excellent slides
https://www.blackalps.ch/ba-17/files/talks/BlackAlps17-Tafani.pdf

### SSH Penetration Testing (Port 22)
https://www.hackingarticles.in/ssh-penetration-testing-port-22/

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
 

# Overview of commands and purpose

| Command | Description and Comment |
|---------|-------------------------|
| cat /proc/96/environ | textHere | 
| dsmeg |  textHere | 
| fd-find | textHere | 
| fuser | textHere | 
| sudo journalctl -u getty.target | textHere |  
| sudo journalctl | grep 2222 | textHere | 
| ls -l /proc/96/ext # working dir of a process | textHere | 
| lsof  | textHere | 
| ncat  | textHere | 
| netstat | textHere | 
| nikto | textHere | 
| nmap -vv --reason -Pn -A --osscan-guess --version-all -p- 100.115.92.195 | textHere |    
| ps -aux | textHere | 
| ps -eo pid,lstart,cmd | When did a process first start? | textHere |    
| ps -feww | textHere | 
| pstree | textHere | 
| socat | textHere | 
| ss | textHere | 
| systemctl status getty.target | textHere |  
| systemd journal files | textHere | 
| tcpdump | textHere | 
| whatis | textHere | 
| wireshark | textHere | 


# cat /proc/96/environ 

some stuff

# dsmeg 
### dmesg | grep port
```bash
    2.305095] 8021q: 802.1Q VLAN Support v1.8
[    2.305295] 9pnet: Installing 9P2000 support
[    2.776671] maitred: Server listening on port 8888
[    2.791686] maitred: Using startup listener port: 7777
[   11.239029] lxdbr0: port 1(veth95d428a9) entered blocking state
[   11.240340] lxdbr0: port 1(veth95d428a9) entered disabled state
[   11.630945] cgroup: lxd (282) created nested cgroup for controller "memory" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
[   11.666585] lxdbr0: port 1(veth95d428a9) entered blocking state
[   11.666828] lxdbr0: port 1(veth95d428a9) entered forwarding state
```

# fd-find  

### sudo apt-get install fd-find
```bash
connorstom@penguin:~/aprojects/network-traffic$ sudo apt-get install fd-find

connorstom@penguin:~/aprojects/network-traffic$ fdfind 2222 /
/home/connorstom/aprojects/network-traffic/Port-2222-uses.png
```


# Fuser
### sudo fuser -v -n tcp 2222
```bash
connorstom@penguin:/proc/2185$ sudo fuser -v -n tcp 2222
                     USER        PID ACCESS COMMAND
2222/tcp:            root         96 F.... sshd
                     root       2185 F.... sshd
                     connorstom   2211 F.... sshd
```


# sudo journalctl # grep 2222 

### sudo journalctl | grep 2222
```bash
sudo journalctl | grep 2222

Nov 30 01:01:35 penguin sshd[95]: Server listening on 0.0.0.0 port 2222.
Nov 30 01:01:35 penguin sshd[95]: Server listening on :: port 2222.
Nov 30 12:58:43 penguin sshd[97]: Server listening on 0.0.0.0 port 2222.
Nov 30 12:58:43 penguin sshd[97]: Server listening on :: port 2222.
Dec 01 04:15:27 penguin sshd[95]: Server listening on 0.0.0.0 port 2222.
Dec 01 04:15:27 penguin sshd[95]: Server listening on :: port 2222.
Dec 01 13:44:59 penguin sshd[96]: Server listening on 0.0.0.0 port 2222.
Dec 01 13:44:59 penguin sshd[96]: Server listening on :: port 2222.
Dec 02 14:08:00 penguin sshd[97]: Server listening on 0.0.0.0 port 2222.
Dec 02 14:08:00 penguin sshd[97]: Server listening on :: port 2222.
Dec 03 16:30:46 penguin sshd[97]: Server listening on 0.0.0.0 port 2222.
Dec 03 16:30:46 penguin sshd[97]: Server listening on :: port 2222.
```

# sudo journalctl -u getty.target  

### sudo journalctl -u getty.target
```bash
# sudo journalctl -u getty.target

connorstom@penguin:~$ sudo journalctl -u getty.target
-- Logs begin at Wed 2020-11-25 00:28:24 EST, end at Mon 2020-12-07 17:41:40 EST. --
Nov 25 00:28:25 penguin systemd[1]: Reached target Login Prompts.
-- Reboot --
Nov 25 14:28:58 penguin systemd[1]: Reached target Login Prompts.
Nov 26 04:27:35 penguin systemd[1]: Stopped target Login Prompts.
-- Reboot --
Nov 26 13:36:16 penguin systemd[1]: Reached target Login Prompts.
-- Reboot --
Nov 27 13:54:19 penguin systemd[1]: Reached target Login Prompts.
-- Reboot --
Nov 28 12:24:43 penguin systemd[1]: Reached target Login Prompts.
-- Reboot --
Nov 29 01:04:09 penguin systemd[1]: Reached target Login Prompts.
-- Reboot --
Nov 29 05:29:44 penguin systemd[1]: Reached target Login Prompts.
-- Reboot --
Nov 29 19:42:29 penguin systemd[1]: Reached target Login Prompts.
```

# ls -l /proc/96/ext # working dir of a process 

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

# lsof  
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

# ncat  

### sudo apt-get install ncat
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo apt-get install ncat
```

# nmap  
### sudo apt-get install nmap
https://nmap.org/book/install.html#inst-already
```bash
connorstom@penguin:~/aprojects/network-traffic$ nmap --version
Nmap version 7.70 ( https://nmap.org )
Platform: x86_64-pc-linux-gnu
Compiled with: liblua-5.3.3 openssl-1.1.1d libssh2-1.8.0 libz-1.2.11 libpcre-8.39 libpcap-1.8.1 nmap-libdnet-1.12 ipv6
Compiled without:
Available nsock engines: epoll poll select
```

## Nightmare write-up by 0xEA31 about port 2222 exploits
https://forum.hackthebox.eu/discussion/891/nightmare-write-up-by-0xea31

## nmap fast check out my own ip_addr
### nmap -T5 -p- -vvv -oA full_T5 100.115.92.195
```bash
connorstom@penguin:~/aprojects/network-traffic$ nmap -T5 -p- -vvv -oA full_T5 100.115.92.195
Starting Nmap 7.70 ( https://nmap.org ) at 2020-12-03 03:28 EST
Initiating Ping Scan at 03:28
Scanning 100.115.92.195 [2 ports]
Completed Ping Scan at 03:28, 0.00s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 03:28
Completed Parallel DNS resolution of 1 host. at 03:28, 0.00s elapsed
DNS resolution of 1 IPs took 0.00s. Mode: Async [#: 1, OK: 1, NX: 0, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating Connect Scan at 03:28
Scanning penguin.lxd (100.115.92.195) [65535 ports]
Discovered open port 2222/tcp on 100.115.92.195
Completed Connect Scan at 03:28, 5.06s elapsed (65535 total ports)
Nmap scan report for penguin.lxd (100.115.92.195)
Host is up, received conn-refused (0.00033s latency).
Scanned at 2020-12-03 03:28:04 EST for 5s
Not shown: 65534 closed ports
Reason: 65534 conn-refused
PORT     STATE SERVICE      REASON
2222/tcp open  EtherNetIP-1 syn-ack

Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 5.22 seconds
```
### nmap -vv --reason -Pn -A --osscan-guess --version-all -p- 100.115.92.195
```bash
connorstom@penguin:~$ nmap -vv --reason -Pn -A --osscan-guess --version-all -p- 100.115.92.195
Starting Nmap 7.70 ( https://nmap.org ) at 2020-12-04 16:01 EST
NSE: Loaded 148 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 16:01
Completed NSE at 16:01, 0.00s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 16:01
Completed NSE at 16:01, 0.00s elapsed
Initiating Parallel DNS resolution of 1 host. at 16:01
Completed Parallel DNS resolution of 1 host. at 16:01, 0.02s elapsed
Initiating Connect Scan at 16:01
Scanning penguin.lxd (100.115.92.195) [65535 ports]
Discovered open port 2222/tcp on 100.115.92.195
Completed Connect Scan at 16:01, 6.22s elapsed (65535 total ports)
Initiating Service scan at 16:01
Scanning 1 service on penguin.lxd (100.115.92.195)
Completed Service scan at 16:01, 0.02s elapsed (1 service on 1 host)
NSE: Script scanning 100.115.92.195.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 16:01
Completed NSE at 16:01, 0.20s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 16:01
Completed NSE at 16:01, 0.01s elapsed
Nmap scan report for penguin.lxd (100.115.92.195)
Host is up, received user-set (0.00035s latency).
Scanned at 2020-12-04 16:01:50 EST for 6s
Not shown: 65534 closed ports
Reason: 65534 conn-refused
PORT     STATE SERVICE REASON  VERSION
2222/tcp open  ssh     syn-ack OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   256 12:a8:2c:13:f8:7c:a7:e4:b5:40:c5:9a:d8:7a:e8:7a (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIIggM0IeRkTAbccYEuCLZVVyfYUzAi2OdxDmu6uhlb9j
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 16:01
Completed NSE at 16:01, 0.00s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 16:01
Completed NSE at 16:01, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 7.83 seconds
```
### nmap -sV -p2222 100.115.92.195
```bash
connorstom@penguin:~$ nmap -sV -p2222 100.115.92.195
Starting Nmap 7.70 ( https://nmap.org ) at 2020-12-04 00:33 EST
Nmap scan report for penguin.lxd (100.115.92.195)
Host is up (0.00043s latency).

PORT     STATE SERVICE VERSION
2222/tcp open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1.62 seconds
```

### nmap -sV -p22 100.115.92.195
```bash
connorstom@penguin:~$ nmap -sV -p22 100.115.92.195
Starting Nmap 7.70 ( https://nmap.org ) at 2020-12-04 00:33 EST
Nmap scan report for penguin.lxd (100.115.92.195)
Host is up (0.00027s latency).

PORT   STATE  SERVICE VERSION
22/tcp closed ssh

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 0.88 seconds
```

## nmap targeted (my own ip_id)
### nmap -A -p80,2222- -vvv -oA targeted 100.115.92.195
```bash 
connorstom@penguin:~/aprojects/network-traffic$ nmap -A -p80,2222- -vvv -oA targeted 100.115.92.195
Starting Nmap 7.70 ( https://nmap.org ) at 2020-12-03 03:29 EST
NSE: Loaded 148 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 03:29
Completed NSE at 03:29, 0.00s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 03:29
Completed NSE at 03:29, 0.00s elapsed
Initiating Ping Scan at 03:29
Scanning 100.115.92.195 [2 ports]
Completed Ping Scan at 03:29, 0.00s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 03:29
Completed Parallel DNS resolution of 1 host. at 03:29, 0.01s elapsed
DNS resolution of 1 IPs took 0.01s. Mode: Async [#: 1, OK: 1, NX: 0, DR: 0, SF: 0, TR: 1, CN: 0]
Initiating Connect Scan at 03:29
Scanning penguin.lxd (100.115.92.195) [63315 ports]
Discovered open port 2222/tcp on 100.115.92.195
Completed Connect Scan at 03:29, 5.02s elapsed (63315 total ports)
Initiating Service scan at 03:29
Scanning 1 service on penguin.lxd (100.115.92.195)
Completed Service scan at 03:29, 0.02s elapsed (1 service on 1 host)
NSE: Script scanning 100.115.92.195.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 03:29
Completed NSE at 03:29, 0.41s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 03:29
Completed NSE at 03:29, 0.01s elapsed
Nmap scan report for penguin.lxd (100.115.92.195)
Host is up, received conn-refused (0.00053s latency).
Scanned at 2020-12-03 03:29:28 EST for 5s
Not shown: 63314 closed ports
Reason: 63314 conn-refused
PORT     STATE SERVICE REASON  VERSION
2222/tcp open  ssh     syn-ack OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey: 
|   256 12:a8:2c:13:f8:7c:a7:e4:b5:40:c5:9a:d8:7a:e8:7a (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIIggM0IeRkTAbccYEuCLZVVyfYUzAi2OdxDmu6uhlb9j
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

NSE: Script Post-scanning.
NSE: Starting runlevel 1 (of 2) scan.
Initiating NSE at 03:29
Completed NSE at 03:29, 0.00s elapsed
NSE: Starting runlevel 2 (of 2) scan.
Initiating NSE at 03:29
Completed NSE at 03:29, 0.00s elapsed
Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 6.95 seconds
```

### nmap -A -T4 scanme.nmap.org
```bash 
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


# netstat 
### depends if you are sudo or not
### sudo netstat -tunlp
```bash
connorstom@penguin:~/aprojects/network-traffic$ sudo netstat -tunlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN      97/sshd             
tcp6       0      0 :::2222                 :::*                    LISTEN      97/sshd             
udp        0      0 0.0.0.0:68              0.0.0.0:*                           69/dhclient    
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


# nikto 
Nikto web server scanner  - https://cirt.net/Nikto2

Full documentation - https://cirt.net/nikto2-docs/


## Nikto Installation

```bash
# get the file
test@ubuntu:~$ wget https://github.com/sullo/nikto/archive/master.zip
```

```bash
# unzip into a directory, run
test@ubuntu:~$ unzip master.zip
test@ubuntu:~$ cd nikto-master/program
test@ubuntu:~/nikto-master/program$ perl nikto.pl
```

### Run nikto normally:

```bash
git clone https://github.com/sullo/nikto
# Main script is in program/
cd nikto/program
# Run using the shebang interpreter
./nikto.pl -h http://www.example.com
# Run using perl (if you forget to chmod)
perl nikto.pl -h http://www.example.com

./nikto.pl -h $IPADDRESS
```

### Nikto Run as a Docker container:

```bash
git clone https://github.com/sullo/nikto.git
cd nikto
docker build -t sullo/nikto .
# Call it without arguments to display the full help
docker run --rm sullo/nikto
# Basic usage
docker run --rm sullo/nikto -h http://www.example.com
# To save the report in a specific format, mount /tmp as a volume:
docker run --rm -v $(pwd):/tmp sullo/nikto -h http://www.example.com -o /tmp/out.json
```

### Starting a Nikto Web Scan
```bash
perl nikto.pl -host https://nikto-test.com
```

# nmap -vv --reason -Pn -A --osscan-guess --version-all -p- 100.115.92.195    



# ps -aux 
## Find Out Owner Of a Process on Linux

### ps -aux
```bash
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root      1859  0.0  0.1  16992  2932 ?        Ss   Dec03   0:00 sshd: connorstom [priv]
connors+  1865  0.0  0.0  16992  2180 ?        S    Dec03   0:00 sshd: connorstom@notty
connors+  1866  0.0  0.0  16992  2192 ?        Ss   Dec03   0:00 sshd: connorstom@internal-sftp
```

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

# ps -eo pid,lstart,cmd # When did a process first start?    



# ps -feww
```bash
# -ww    unlimited width
# -ef    is the usual ps -ef
# -e     Select all processes
# -f     Do full-format listing
# -H     Show process hierarchy (forest)
ps -feww

connorstom@penguin:~$ ps -Hf -p 2185,96,2211
UID        PID  PPID  C STIME TTY          TIME CMD
root        96     1  0 Dec04 ?        00:00:00 /usr/sbin/sshd -D -f /dev/.ssh/sshd_config
root      2185    96  0 Dec04 ?        00:00:00   sshd: connorstom [priv]
connors+  2211  2185  0 Dec04 ?        00:00:00     sshd: connorstom@notty
```

# pstree
```bash
connorstom@penguin:/proc/2185$ pstree
systemd─┬─agetty
        ├─dbus-daemon
        ├─dhclient
        ├─polkitd───2*[{polkitd}]
        ├─sshd───sshd───sshd───sshd
        ├─systemd─┬─(sd-pam)
        │         ├─at-spi-bus-laun─┬─dbus-daemon
        │         │                 └─3*[{at-spi-bus-laun}]
        │         ├─at-spi2-registr───2*[{at-spi2-registr}]
        │         ├─dbus-daemon
        │         ├─gnome-keyring-d───3*[{gnome-keyring-d}]
        │         ├─2*[ld-linux-x86-64───ld-linux-x86-64───4*[{ld-linux-x86-64}]]
        │         ├─2*[ld-linux-x86-64]
        │         └─ld-linux-x86-64─┬─code─┬─code───code───5*[{code}]
        │                           │      ├─code
        │                           │      ├─code───6*[{code}]
        │                           │      ├─code─┬─bash
        │                           │      │      ├─code─┬─code───7*[{code}]
        │                           │      │      │      └─16*[{code}]
        │                           │      │      ├─code───11*[{code}]
        │                           │      │      └─20*[{code}]
        │                           │      ├─code─┬─bash───pstree
        │                           │      │      ├─code───16*[{code}]
        │                           │      │      └─20*[{code}]
        │                           │      ├─code─┬─bash
        │                           │      │      ├─code───16*[{code}]
        │                           │      │      └─19*[{code}]
        │                           │      ├─code───18*[{code}]
        │                           │      └─30*[{code}]
        │                           ├─ld-linux-x86-64───bash
        │                           └─10*[{ld-linux-x86-64}]
        ├─systemd-journal
        ├─systemd-logind
        └─systemd-udevd
```

### pstree -a
```bash
# -a Show command line arguments
connorstom@penguin:/proc/2185$ pstree -a
systemd
  ├─agetty -o -p -- \\u --noclear --keep-baud console 115200,38400,9600 vt220
  ├─dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
  ├─dhclient -4 -v -i -pf /run/dhclient.eth0.pid -lf /var/lib/dhcp/dhclient.eth0.leases -I -df/var/lib/dhcp/dhclient6.eth0.lea
  ├─polkitd --no-debug
  │   └─2*[{polkitd}]
  ├─sshd -D -f /dev/.ssh/sshd_config
  │   └─sshd                      
  │       └─sshd                       
  │           └─sshd               
  ├─systemd --user
  │   ├─(sd-pam)  
  │   ├─at-spi-bus-laun
  │   │   ├─dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibility.conf --nofork --print-address 3
  │   │   └─3*[{at-spi-bus-laun}]
  │   ├─at-spi2-registr --use-gnome-session
  │   │   └─2*[{at-spi2-registr}]
  │   ├─dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
  │   ├─gnome-keyring-d --start --foreground --components=secrets
  │   │   └─3*[{gnome-keyring-d}]
  │   ├─ld-linux-x86-64 --library-path /opt/google/cros-containers/bin/../lib--inhibit-rpath
  │   │   └─ld-linux-x86-64 --library-path /opt/google/cros-containers/bin/../lib--inhibit-rpath
  │   │       └─4*[{ld-linux-x86-64}]
  │   ├─ld-linux-x86-64 --library-path /opt/google/cros-containers/bin/../lib--inhibit-rpath
  ├─systemd-journal
  ├─systemd-logind
  └─systemd-udevd
```


# sudo pwdx 258
## need more info about pwdx
```bash
connorstom@penguin:~/aprojects/network-traffic$ pwdx 258
258: Permission denied
connorstom@penguin:~/aprojects/network-traffic$ sudo pwdx 258
258: /
connorstom@penguin:~/aprojects/network-traffic$ sudo pwdx 96
96: /
```

# Socat

### sudo apt-get install socat
```bash
connorstom@penguin:~/aprojects/br-build-site$ sudo apt-get install socat
```

### socat/EXAMPLES
https://github.com/craSH/socat/blob/master/EXAMPLES
```bash
# socat- [network-traffic](#network-traffic)

# multipurpose relay for bidirectional data transfer

# Socat (for SOcket CAT) establishes two bidirectional byte streams and transfers data between them. 

# Data channels may be files, pipes, devices (terminal or modem, etc.), or sockets (Unix, IPv4, IPv6, raw, UDP, TCP, SSL).

#Examples of using socat
#Let's get started with some basic examples of using socat for various connections.

1. Connect to TCP port 80 on the local or remote system:

# socat - TCP4:www.example.com:80
In this case, socat transfers data between STDIO (-) and a TCP4 connection to port 80 on a host named www.example.com.

2. Use socat as a TCP port forwarder:

For a single connection, enter:

# socat TCP4-LISTEN:81 TCP4:192.168.1.10:80
For multiple connections, use the fork option as used in the examples below:

# socat TCP4-LISTEN:81,fork,reuseaddr TCP4:TCP4:192.168.1.10:80
This example listens on port 81, accepts connections, and forwards the connections to port 80 on the remote host.

# socat TCP-LISTEN:3307,reuseaddr,fork UNIX-CONNECT:/var/lib/mysql/mysql.sock 
The above example listens on port 3307, accepts connections, and forwards the connections to a Unix socket on the remote host.

3. Implement a simple network-based message collector:

# socat -u TCP4-LISTEN:3334,reuseaddr,fork OPEN:/tmp/test.log,creat,append
In this example, when a client connects to port 3334, a new child process is generated. All data sent by the clients is appended to the file /tmp/test.log. If the file does not exist, socat creates it. The option reuseaddr allows an immediate restart of the server process.

4. Send a broadcast to the local network:

# socat - UDP4-DATAGRAM:224.255.0.1:6666,bind=:6666,ip-add-membership=224.255.0.1:eth0
In this case, socat transfers data from stdin to the specified multicast address using UDP over port 6666 for both the local and remote connections. The command also tells the interface eth0 to accept multicast packets for the given group.

Practical uses for socat
Socat is a great tool for troubleshooting. It is also handy for easily making remote connections. Practically, I have used socat for remote MySQL connections. In the example below, I demonstrate how I use socat to connect my web application to a remote MySQL server by connecting over the local socket.

1. On my remote MySQL server, I enter:

# socat TCP-LISTEN:3307,reuseaddr,fork UNIX-CONNECT:/var/lib/mysql/mysql.sock &
This command starts socat and configures it to listen by using port 3307.

2. On my webserver, I enter:

# socat UNIX-LISTEN:/var/lib/mysql/mysql.sock,fork,reuseaddr,unlink-early,user=mysql,group=mysql,mode=777 TCP:192.168.100.5:3307 &
The above command connects to the remote server 192.168.100.5 by using port 3307.

However, all communication will be done on the Unix socket /var/lib/mysql/mysql.sock, and this makes it appear to be a local server.
```

# ss  
### socket statistics command (i.e. ss) 
### sudo ss -tunp
```bash
Netid   State    Recv-Q    Send-Q        Local Address:Port         Peer Address:Port                                      
tcp     ESTAB    0         0            100.115.92.195:40630        40.71.11.167:443      users:(("code",pid=379,fd=27))   
tcp     ESTAB    0         0            100.115.92.195:2222        100.115.92.25:34294    users:(("sshd",pid=258,fd=3),("sshd",pid=243,fd=3))
```

### sudo ss -lptn 'sport = :2222'
```bash
connorstom@penguin:/proc/2185$ sudo ss -lptn 'sport = :2222'
State       Recv-Q      Send-Q           Local Address:Port            Peer Address:Port                                         
LISTEN      0           128                    0.0.0.0:2222                 0.0.0.0:*          users:(("sshd",pid=96,fd=3))      
LISTEN      0           128                       [::]:2222                    [::]:*          users:(("sshd",pid=96,fd=4))  
```

### socket statistics command (i.e. ss) 
```bash
# Here is an example of execution:

connorstom@penguin:/proc/2185$ ss -tanp | grep '222\|State'
State    Recv-Q   Send-Q        Local Address:Port         Peer Address:Port                       
LISTEN   0        128                 0.0.0.0:2222              0.0.0.0:*            
ESTAB    0        0            100.115.92.195:2222        100.115.92.25:33504
LISTEN   0        128                    [::]:2222                 [::]:*     
```

# init.d directory
### README-create-debian-startup-script.md
https://gist.github.com/drmalex07/298ab26c06ecf401f66c

The following is mostly taken from the example published at https://mkaz.com/2013/07/03/run-script-at-start-on-debian/

Write an init.d script according to the the dependency-booting specification (see at https://wiki.debian.org/LSBInitScripts)
```bash
# say it foo.sh 
# Place the script under /etc/init.d.

ln -s /root/scripts/foo.sh /etc/init.d/foo 

# Update the runlevel directories under /etc/rc*:

update-rc.d foo defaults
```

```bash
# foo.sh
#! /bin/bash

### BEGIN INIT INFO
# Provides:          foo
# Required-Start:    $local_fs $network
# Required-Stop:     $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: foo service
# Description:       Run Foo service
### END INIT INFO

# Carry out specific functions when asked to by the system
case "$1" in
  start)
    echo "Starting Foo..."
    sudo -u foo-user bash -c 'cd /path/to/scripts/ && ./start-foo.sh'
    ;;
  stop)
    echo "Stopping Foo..."
    sudo -u foo-user bash -c 'cd /path/to/scripts/ && ./stop-foo.sh'
    sleep 2
    ;;
  *)
    echo "Usage: /etc/init.d/foo {start|stop}"
    exit 1
    ;;
esac

exit 0
```

## Debian Boot Process 
## Get To Know Linux: The /etc/init.d Directory
```bash
# If you look at the /etc directory you will find directories that are in the form rc#.d 
# (Where # is a number reflects a specific initialization level - from 0 to 6). 
# Within each of these directories is a number of other scripts that control processes. 
# These scripts will either begin with a "K" or an "S". All "K" scripts are run before "S" scripts. 
# And depending upon where the scripts are located will determine when the scripts initiate.
```

### All scripts executed by the init system are located in the directory /etc/init.d/
https://wiki.debian.org/BootProcess
```bash
The meanings of all the runlevels are as follows:

runlevel    directory           meaning
N           none                System bootup (NONE). There is no /etc/rcN.d/ directory.
0           /etc/rc0.d/         Halt the system.
S           /etc/rcS.d/         Single-user mode on boot. The lower case s can be used as alias.
1           /etc/rc1.d/         Single-user mode switched from multi-user mode.
2 ... 5     /etc/rc{2,3,4,5}.d/ Multi-user mode. The Debian system does not pre-assign any special meaning differences among these.
6           /etc/rc6.d/         Reboot the system.
7 ... 9     /etc/rc{7,8,9}.d/   Valid multi-user mode but traditional Unix variants don’t use. 

The configuration decision on the use of the runlevels between 2 and 5, is solely left to the system administrator on the Debian system.
```

## init. d contains the start/stop scripts the daemon while the system is running or during boot 
```bash
# d is the sub-directory of /etc directory in Linux file system. 
# init. d basically contains the bunch of start/stop scripts which are used to control 
# (start,stop,reload,restart) the daemon while the system is running or during boot.
```

### Get To Know Linux: The /etc/init.d Directory
https://www.ghacks.net/2009/04/04/get-to-know-linux-the-etcinitd-directory/

In order to control any of the scripts in init.d manually you have to have root (or sudo) access. Each script will be run as a command and the structure of the command will look like:

```bash
/etc/init.d/command OPTION
```

Where command is the actual command to run and OPTION can be one of the following:

- start
- stop
- reload
- restart
- force-reload
  
Most often you will use either start, stop, or restart. So if you want to stop your network you can issue the command:

```bash
/etc/init.d/networking stop
```

Or if you make a change to your network and need to restart it, you could do so with the following command:

```bash
/etc/init.d/networking restart
```

Some of the more common init scripts in this directory are:

- networking
- samba
- apache2
- ftpd
- sshd
- dovecot
- mysql
  
Of course there may be more often-used scripts in your directory - it depends upon what you have installed. The above list was taken from a Ubuntu Server 8.10 installation so a standard desktop installation would have a few less networking-type scripts.

** But what about /etc/rc.local **

There is a third option that I used to use quite a bit. This option is the /etc/rc.local script. This file runs after all other init level scripts have run, so it's safe to put various commands that you want to have issued upon startup. Many times I will place mounting instructions for things like nfs in this script. This is also a good place to place "troubleshooting" scripts in. For instance, once I had a machine that, for some reason, samba seemed to not want to start. Even afer checking to make sure the Samba daemon was setup to initialize at boot up. So instead of spending all of my time up front with this I simply placed the line:

```bash
/etc/init.d/samba start
```

in the /etc/rc.local script and Samba worked like a charm. Eventually I would come back and trouble shoot this issue.


here is text
# Linux Runlevel programs
https://www.thegeekstuff.com/2011/02/linux-boot-process/
- When the Linux system is booting up, you might see various services getting started. For example, it might say “starting sendmail …. OK”. Those are the runlevel programs, executed from the run level directory as defined by your run level.
- Depending on your default init level setting, the system will execute the programs from one of the following directories.
  - Run level 0 – /etc/rc.d/rc0.d/
  - Run level 1 – /etc/rc.d/rc1.d/
  - Run level 2 – /etc/rc.d/rc2.d/
  - Run level 3 – /etc/rc.d/rc3.d/
  - Run level 4 – /etc/rc.d/rc4.d/
  - Run level 5 – /etc/rc.d/rc5.d/
  - Run level 6 – /etc/rc.d/rc6.d/
- Please note that there are also symbolic links available for these directory under /etc directly. So, /etc/rc0.d is linked to /etc/rc.d/rc0.d.
- Under the /etc/rc.d/rc*.d/ directories, you would see programs that start with S and K.
- Programs starts with S are used during startup. S for startup.
- Programs starts with K are used during shutdown. K for kill.
- There are numbers right next to S and K in the program names. Those are the sequence number in which the programs should be started or killed.
- For example, S12syslog is to start the syslog deamon, which has the sequence number of 12. S80sendmail is to start the sendmail daemon, which has the sequence number of 80. So, syslog program will be started before sendmail.

# Chart: systemctl vs service tools 
<br/>
<p align="center">
 <img width="800px" src="https://github.com/coding-to-music/network-traffic/blob/main/systemctl-vs-service-tools.png?raw=true" align="center" alt="systemctl vs service tools" />
<br/>
&nbsp;

### systemctl status 2185
```bash
connorstom@penguin:/proc/2185$ systemctl status 2185
● session-3.scope - Session 3 of user connorstom
   Loaded: loaded (/run/systemd/transient/session-3.scope; transient)
Transient: yes
   Active: active (running) since Fri 2020-12-04 23:49:07 EST; 2h 11min ago
    Tasks: 3
   Memory: 1.3M
   CGroup: /user.slice/user-1000.slice/session-3.scope
           ├─2185 sshd: connorstom [priv]
           ├─2211 sshd: connorstom@notty
           └─2215 sshd: connorstom@internal-sftp
```

# systemctl
### systemctl status 2185
```bash
connorstom@penguin:/proc/2185$ systemctl status 2185
● session-3.scope - Session 3 of user connorstom
   Loaded: loaded (/run/systemd/transient/session-3.scope; transient)
Transient: yes
   Active: active (running) since Fri 2020-12-04 23:49:07 EST; 1h 56min ago
    Tasks: 3
   Memory: 1.3M
   CGroup: /user.slice/user-1000.slice/session-3.scope
           ├─2185 sshd: connorstom [priv]
           ├─2211 sshd: connorstom@notty
           └─2215 sshd: connorstom@internal-sftp
```

### systemctl status $(pgrep perl)
```bash
connorstom@penguin:/proc/2185$ systemctl status $(pgrep perl)
● penguin
    State: running
     Jobs: 0 queued
   Failed: 0 units
    Since: Fri 2020-12-04 15:20:14 EST; 10h ago
   CGroup: /
           ├─user.slice
           │ └─user-1000.slice
           │   ├─user@1000.service
           │   │ ├─sommelier\x2dx.slice
           │   │ │ ├─sommelier-x@1.service
           │   │ │ │ ├─143 /opt/google/cros-containers/bin/../lib/ld-linux-x86-64.so.2 --library-path /opt/google/cros-containers
           │   │ │ │ └─176 /opt/google/cros-containers/bin/../lib/ld-linux-x86-64.so.2 --library-path /opt/google/cros-containers
           │   │ │ └─sommelier-x@0.service
           │   │ │   ├─146 /opt/google/cros-containers/bin/../lib/ld-linux-x86-64.so.2 --library-path /opt/google/cros-containers
           │   │ │   └─177 /opt/google/cros-containers/bin/../lib/ld-linux-x86-64.so.2 --library-path /opt/google/cros-containers
           │   │ ├─sommelier.slice
           │   │ │ ├─sommelier@0.service
           │   │ │ │ └─160 /opt/google/cros-containers/bin/../lib/ld-linux-x86-64.so.2 --library-path /opt/google/cros-containers
           │   │ │ └─sommelier@1.service
           │   │ │   └─148 /opt/google/cros-containers/bin/../lib/ld-linux-x86-64.so.2 --library-path /opt/google/cros-containers
           │   │ ├─init.scope
           │   │ │ ├─ 98 /lib/systemd/systemd --user
           │   │ │ └─101 (sd-pam)
           │   │ ├─at-spi-dbus-bus.service
           │   │ │ ├─398 /usr/lib/at-spi2-core/at-spi-bus-launcher
           │   │ │ ├─403 /usr/bin/dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibility.conf --nofork --print-addre
           │   │ │ └─405 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
           │   │ └─dbus.service
           │   │   ├─397 /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-onl
           │   │   └─574 /usr/bin/gnome-keyring-daemon --start --foreground --components=secrets
           │   └─session-3.scope
           │     ├─2185 sshd: connorstom [priv]
           │     ├─2211 sshd: connorstom@notty
           │     └─2215 sshd: connorstom@internal-sftp
           ├─init.scope
           │ └─1 /sbin/init
           └─system.slice
             ├─systemd-udevd.service
             │ └─45 /lib/systemd/systemd-udevd
             ├─networking.service
             │ └─71 /sbin/dhclient -4 -v -i -pf /run/dhclient.eth0.pid -lf /var/lib/dhcp/dhclient.eth0.leases -I -df /var/lib/dhc
             ├─polkit.service
             │ └─259 /usr/lib/policykit-1/polkitd --no-debug
             ├─systemd-journald.service
             │ └─36 /lib/systemd/systemd-journald
             ├─console-getty.service
             │ └─95 /sbin/agetty -o -p -- \u --noclear --keep-baud console 115200,38400,9600 vt220
             ├─cros-sftp.service
             │ └─96 /usr/sbin/sshd -D -f /dev/.ssh/sshd_config
             ├─dbus.service
             │ └─63 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
             └─systemd-logind.service
               └─64 /lib/systemd/systemd-logind
```



## How To List Startup Services At Boot In Linux
[How To List Startup Services At Boot In Linux](https://ostechnix.com/how-to-list-startup-services-at-boot-in-linux/)
```bash
sudo systemctl list-unit-files --type=service

# To list only the enabled services at system boot, run:
sudo systemctl list-unit-files --type=service --state=enabled --all

UNIT FILE                              STATE  
autovt@.service                        enabled
dbus-org.freedesktop.timesync1.service enabled
getty@.service                         enabled
networking.service                     enabled
ssh.service                            enabled
sshd.service                           enabled
systemd-timesyncd.service              enabled

7 unit files listed.

# To list only the disabled services at system boot, run:
connorstom@penguin:~$ sudo systemctl list-unit-files --type=service --state=disabled --all
UNIT FILE                              STATE   
cros-sftp.service                      disabled
debug-shell.service                    disabled
ifupdown-wait-online.service           disabled
nftables.service                       disabled
rtkit-daemon.service                   disabled
serial-getty@.service                  disabled
systemd-boot-check-no-failures.service disabled
systemd-resolved.service               disabled
systemd-time-wait-sync.service         disabled

9 unit files listed.

# run the following command to list all services:

connorstom@penguin:~$ sudo service --status-all
 [ + ]  dbus
 [ - ]  hwclock.sh
 [ + ]  networking
 [ + ]  procps
 [ - ]  ssh
 [ - ]  sudo
 [ + ]  udev
 [ - ]  x11-common

# Here, the + indicates the service is running, and - indicates a stopped service. If you see ? in the output, the service state cannot be determined (for some reason).
```
## to stop a service **permanently** in debian
[to stop a service **permanently** in debian](https://www.linuxquestions.org/questions/debian-26/chkconfig-equivalent-debian-346901/)
```bash
# using the 'update-rc.d' command which allows you to add/remove/set the symlinks in /etc/rc*.d that point to scripts in /etc/init.d.
# To remove a script that starts a certain service run

update-rc.d -f script_name remove

# then you can keep or delete the corresponding script in /etc/init.d/
```


# systemctl status getty.target  

## systemctl list-dependencies
[How to list, start and stop services at boot time in Debian linux](https://net2.com/how-to-list-start-and-stop-services-at-boot-time-in-linux-ubuntu-debian/)
```bash
connorstom@penguin:~$ systemctl list-dependencies
default.target
● ├─cros-sftp.service
● ├─display-manager.service
● ├─systemd-update-utmp-runlevel.service
● └─multi-user.target
●   ├─dbus.service
●   ├─networking.service
●   ├─ssh.service
●   ├─systemd-ask-password-wall.path
●   ├─systemd-logind.service
●   ├─systemd-update-utmp-runlevel.service
●   ├─systemd-user-sessions.service
●   ├─basic.target
●   │ ├─tmp.mount
●   │ ├─paths.target
●   │ ├─slices.target
●   │ │ ├─-.slice
●   │ │ └─system.slice
●   │ ├─sockets.target
●   │ │ ├─dbus.socket
●   │ │ ├─systemd-initctl.socket
●   │ │ ├─systemd-journald-audit.socket
●   │ │ ├─systemd-journald-dev-log.socket
●   │ │ ├─systemd-journald.socket
●   │ │ ├─systemd-udevd-control.socket
●   │ │ └─systemd-udevd-kernel.socket
●   │ ├─sysinit.target
●   │ │ ├─dev-hugepages.mount
●   │ │ ├─dev-mqueue.mount
●   │ │ ├─kmod-static-nodes.service
●   │ │ ├─proc-sys-fs-binfmt_misc.automount
●   │ │ ├─sys-fs-fuse-connections.mount
●   │ │ ├─sys-kernel-config.mount
●   │ │ ├─sys-kernel-debug.mount
●   │ │ ├─systemd-ask-password-console.path
●   │ │ ├─systemd-binfmt.service
●   │ │ ├─systemd-hwdb-update.service
●   │ │ ├─systemd-journal-flush.service
●   │ │ ├─systemd-journald.service
●   │ │ ├─systemd-machine-id-commit.service
●   │ │ ├─systemd-modules-load.service
●   │ │ ├─systemd-random-seed.service
●   │ │ ├─systemd-sysctl.service
●   │ │ ├─systemd-sysusers.service
●   │ │ ├─systemd-timesyncd.service
●   │ │ ├─systemd-tmpfiles-setup-dev.service
●   │ │ ├─systemd-tmpfiles-setup.service
●   │ │ ├─systemd-udev-trigger.service
●   │ │ ├─systemd-udevd.service
●   │ │ ├─systemd-update-utmp.service
●   │ │ ├─cryptsetup.target
●   │ │ ├─local-fs.target
●   │ │ │ └─systemd-remount-fs.service
●   │ │ └─swap.target
●   │ └─timers.target
●   │   ├─apt-daily-upgrade.timer
●   │   ├─apt-daily.timer
●   │   ├─man-db.timer
●   │   └─systemd-tmpfiles-clean.timer
●   ├─getty.target
●   │ ├─console-getty.service
●   │ ├─getty-static.service
●   │ └─getty@tty1.service
●   └─remote-fs.target
```

### systemctl status getty.target
```bash
# systemctl status getty.target
connorstom@penguin:~$ systemctl status getty.target
● getty.target - Login Prompts
   Loaded: loaded (/lib/systemd/system/getty.target; static; vendor preset: enabled)
   Active: active since Mon 2020-12-07 17:11:12 EST; 15min ago
     Docs: man:systemd.special(7)
           man:systemd-getty-generator(8)
           http://0pointer.de/blog/projects/serial-console.html

Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.
connorstom@penguin:~$ systemctl status timers.target
● timers.target - Timers
   Loaded: loaded (/lib/systemd/system/timers.target; static; vendor preset: enabled)
   Active: active since Mon 2020-12-07 17:11:12 EST; 15min ago
     Docs: man:systemd.special(7)

Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.
connorstom@penguin:~$ systemctl status cros-sftp.service
● cros-sftp.service - CrOS SFTP service
   Loaded: loaded (/usr/lib/systemd/system/cros-sftp.service; disabled; vendor preset: enabled)
   Active: active (running) since Mon 2020-12-07 17:11:12 EST; 16min ago
  Process: 93 ExecStartPre=/usr/sbin/sshd -t -f /dev/.ssh/sshd_config (code=exited, status=0/SUCCESS)
 Main PID: 97 (sshd)
    Tasks: 1 (limit: 3330)
   Memory: 3.2M
   CGroup: /system.slice/cros-sftp.service
           └─97 /usr/sbin/sshd -D -f /dev/.ssh/sshd_config

Warning: Journal has been rotated since unit was started. Log output is incomplete or unavailable.
```


### systemctl list-sockets
```bash
connorstom@penguin:~/aprojects/network-traffic$ systemctl list-sockets
LISTEN                          UNIT                            ACTIVATES
/run/initctl                    systemd-initctl.socket          systemd-initctl.service
/run/systemd/journal/dev-log    systemd-journald-dev-log.socket systemd-journald.service
/run/systemd/journal/socket     systemd-journald.socket         systemd-journald.service
/run/systemd/journal/stdout     systemd-journald.socket         systemd-journald.service
/run/udev/control               systemd-udevd-control.socket    systemd-udevd.service
/var/run/dbus/system_bus_socket dbus.socket                     dbus.service
kobject-uevent 1                systemd-udevd-kernel.socket     systemd-udevd.service

7 sockets listed.
Pass --all to see loaded but inactive sockets, too.
```

### View the logs in /var/log
```bash
connorstom@penguin:~/aprojects/network-traffic$ cd /var/log
connorstom@penguin:/var/log$ ll
total 400
-rw-rw-r--  1 root utmp             21888 Dec  3 16:30 wtmp
-rw-r--r--  1 root root            319068 Dec  2 03:30 dpkg.log
drwxr-xr-x  1 root root                60 Dec  2 03:20 apt/
-rw-r--r--  1 root root             16398 Dec  2 02:11 alternatives.log
drwxr-sr-x+ 1 root systemd-journal     64 Nov 25 00:28 journal/
drwxr-xr-x  1 root root               180 Nov 25 00:28 ./
drwx------  1 root root                 0 Nov 25 00:28 private/
-rw-r--r--  1 root root              3456 Jul 22 00:26 faillog
-rw-rw-r--  1 root utmp             31536 Jul 22 00:26 lastlog
-rw-r--r--  1 root root              1943 Jul 22 00:26 fontconfig.log
-rw-r--r--  1 root root             34664 Jul 21 01:26 bootstrap.log
drwxr-xr-x  1 root root                90 Jul 21 01:26 ../
-rw-rw----  1 root utmp                 0 Jul 21 01:26 btmp
```


# systemd journal files
### How to inspect systemd journal files directly?
https://www.linuxtopia.org/online_books/opensuse_guides/opensuse11.1_startup_guide/sec_trouble_info.html
```bash
# As indicated in the other answer, these logs are regularly rotated, and may not stretch back as far as you might hope.
journalctl --file /path/to/some/file.journal

# The following is a list of the most commonly checked log files and what they typically contain.
Log File                  Description
~/.xsession-errors        Messages from the desktop applications currently running. The ~ is the home directory of the current user.
/var/log/apparmor/        Log files from AppArmor, see Novell AppArmor Administration Guide, (↑ Novell AppArmor Administration Guide )
/var/log/audit/audit.log  Log file from Audit to track any access to files, directories, or resources of your system and trace system calls.
/var/log/boot.msg         Messages from the kernel during the boot process.
/var/log/mail.*           Messages from the mail system.
/var/log/messages         Ongoing messages from the kernel and system log daemon when running.
/var/log/NetworkManager   Log file from NetworkManager to collect problems with network connectivity
/var/log/warn             All messages from the kernel and system log daemon assigned WARNING level or higher.
/var/log/wtmp             Binary file containing user login records for the current machine session. View it with last.

# Apart from log files, your machine also supplies you with information about the running system

File                Description
/proc/cpuinfo       This displays processor information, including its type, make, model, and performance.
/proc/dma           This shows which DMA channels are currently being used.
/proc/interrupts    This shows which interrupts are in use and how many of each have been in use.
/proc/iomem         This displays the status of I/O (input/output) memory.
/proc/ioports       This shows which I/O ports are in use at the moment.
/proc/meminfo       This displays memory status.
/proc/modules       This displays the individual modules.
/proc/mounts        This displays devices currently mounted.
/proc/partitions    This shows the partitioning of all hard disks.
/proc/version       This displays the current version of Linux.

connorstom@penguin:/var/log/journal/34f82f01ee4a706f645f9d635f17bfe9$ journalctl --file  /var/log/journal/34f82f01ee4a706f645f9d635f17bfe9/user-1000.journal 

Dec 03 04:23:34 penguin systemd[100]: sommelier@0.service: Main process exited, code=killed, status=15/TERM
Dec 03 04:23:34 penguin systemd[100]: cros-garcon.service: Main process exited, code=killed, status=15/TERM
-- Reboot --
Dec 03 16:30:46 penguin systemd[99]: Listening on GnuPG network certificate management daemon.
Dec 03 16:30:46 penguin systemd[99]: Reached target Paths.
Dec 03 16:30:46 penguin systemd[99]: Starting D-Bus User Message Bus Socket.
Dec 03 16:30:46 penguin systemd[99]: Created slice sommelier.slice.
Dec 03 16:30:46 penguin systemd[99]: Reached target Timers.
Dec 03 16:30:46 penguin systemd[99]: Listening on GnuPG cryptographic agent and passphrase cache (restricted).
Dec 03 16:30:46 penguin systemd[99]: Created slice sommelier\x2dx.slice.
Dec 03 16:30:46 penguin systemd[99]: Listening on Sound System.
Dec 03 16:30:46 penguin systemd[99]: Listening on GnuPG cryptographic agent and passphrase cache.
Dec 03 16:30:46 penguin systemd[99]: Listening on GnuPG cryptographic agent and passphrase cache (access for web browsers).
Dec 03 16:30:46 penguin systemd[99]: Listening on GnuPG cryptographic agent (ssh-agent emulation).
Dec 03 16:30:46 penguin systemd[99]: Listening on D-Bus User Message Bus Socket.

connorstom@penguin:/var/log/journal/34f82f01ee4a706f645f9d635f17bfe9$ journalctl --file  /var/log/journal/34f82f01ee4a706f645f9d635f17bfe9/user-1000.journal | grep ' port '
Dec 02 16:51:14 penguin sshd[255]: Received disconnect from 100.115.92.25 port 36440:11: disconnected by user
Dec 02 16:51:14 penguin sshd[255]: Disconnected from user connorstom 100.115.92.25 port 36440
Dec 03 16:30:49 penguin garcon[217]: [217]: Server listening on vsock port 10000
Dec 04 15:20:18 penguin garcon[232]: [232]: Server listening on vsock port 10000
Dec 04 18:32:57 penguin sshd[255]: Received disconnect from 100.115.92.25 port 44194:11: disconnected by user
Dec 04 18:32:57 penguin sshd[255]: Disconnected from user connorstom 100.115.92.25 port 44194
Dec 05 14:02:05 penguin garcon[217]: [217]: Server listening on vsock port 10000
```


# tcpdump 

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
### To view available devices    sudo tcpdump -D
```bash
connorstom@penguin:/var/log$ sudo tcpdump -D
1.eth0 [Up, Running]
2.any (Pseudo-device that captures on all interfaces) [Up, Running]
3.lo [Up, Running, Loopback]
4.nflog (Linux netfilter log (NFLOG) interface)
5.nfqueue (Linux netfilter queue (NFQUEUE) interface)
6.usbmon1 (USB bus number 1)
7.usbmon2 (USB bus number 2)
```

### sudo tcpdump -vvv -i eth0 port 2222
```bash

```

### sudo tcpdump -v -i eth0 dst 100.115.92.25
```bash
connorstom@penguin:/var/log$ sudo tcpdump -vvv -i eth0 port 2222
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
02:20:59.222300 IP (tos 0x8, ttl 64, id 22599, offset 0, flags [DF], proto TCP (6), length 52)
    penguin.lxd.2222 > 100.115.92.25.34128: Flags [.], cksum 0x81e9 (incorrect -> 0x2121), seq 1742051507, ack 313750789, win 501, options [nop,nop,TS val 1236229481 ecr 239470150], length 0
02:20:59.222659 IP (tos 0x20, ttl 63, id 48872, offset 0, flags [DF], proto TCP (6), length 52)
    100.115.92.25.34128 > penguin.lxd.2222: Flags [.], cksum 0x81e9 (incorrect -> 0x7127), seq 1, ack 1, win 1454, options [nop,nop,TS val 246807916 ecr 1236144660], length 0
^C
2 packets captured
2 packets received by filter
0 packets dropped by kernel
```

### sudo tcpdump -nAtvvvXX src port 2222
```bash
connorstom@penguin:~/aprojects/goColorsTests$ sudo tcpdump -nAtvvvXX src port 2222
```

### top -p 1859
```bash
top - 02:13:17 up  9:42,  0 users,  load average: 0.82, 0.83, 0.60
Tasks:   1 total,   0 running,   1 sleeping,   0 stopped,   0 zombie
%Cpu(s): 12.1 us,  4.0 sy,  0.0 ni, 60.1 id,  0.0 wa,  0.0 hi,  0.0 si, 23.8 st
MiB Mem :   2779.8 total,   2772.4 free,      5.6 used,      1.8 buff/cache
MiB Swap:      0.0 total,      0.0 free,      0.0 used.   2774.2 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                                                                           
 1859 root      20   0   16992   2332   1212 S   0.0   0.1   0:00.10 sshd                                                                                                                                                                  ```

# whatis 

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



# wireshark 

### sudo apt-get install wireshark
```bash
connorstom@penguin:~/aprojects/network-traffic$ sudo apt-get install wireshark

// got this error: “couldnt run /usr/bin/dumpcap in child process

sudo dpkg-reconfigure wireshark-common
// answer Yes to letting non-supervisors use wireshark

sudo chmod +x /usr/bin/dumpcap
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




# End of document ###########
##### End of document #################################################################################################
##### End of document #################################################################################################
##### End of document #################################################################################################
##### End of document #################################################################################################
##### End of document #################################################################################################
##### End of document #################################################################################################
##### End of document #################################################################################################
##### End of document #################################################################################################
##### End of document #################################################################################################
##### End of document #################################################################################################
##### End of document #################################################################################################
##### End of document #################################################################################################
##### End of document #################################################################################################


# Trying various commands
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

### Simple way to start analysis
```bash
sudo netstat -atupen | grep 2222
sudo netstat -atupen
netstat -tulpn
sudo lsof -nP -i | grep 2222
nmap -T5 -p- -vvv -oA full_T5 100.115.92.195
nmap -A -p80,2222- -vvv -oA targeted 100.115.92.195


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
```

### The usual key indicators of port 2222
```bash
connorstom@penguin:~/aprojects/network-traffic$ sudo netstat -atupen | grep 2222
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN      0          3664       97/sshd             
tcp        0      0 100.115.92.195:2222     100.115.92.25:41452     ESTABLISHED 0          172739     3370/sshd: connorst 
tcp6       0      0 :::2222                 :::*                    LISTEN      0          3666       97/sshd             
connorstom@penguin:~/aprojects/network-traffic$ sudo netstat -atupen
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode      PID/Program name    
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN      0          3664       97/sshd             
tcp        0      0 100.115.92.195:2222     100.115.92.25:41452     ESTABLISHED 0          172739     3370/sshd: connorst 
tcp        0      0 100.115.92.195:55576    40.71.11.167:443        ESTABLISHED 1000       208438     3867/code --type=ut 
tcp6       0      0 :::2222                 :::*                    LISTEN      0          3666       97/sshd             
udp        0      0 0.0.0.0:68              0.0.0.0:*                           0          3442       69/dhclient         
connorstom@penguin:~/aprojects/network-traffic$ netstat -tulpn
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN      -                   
tcp6       0      0 :::2222                 :::*                    LISTEN      -                   
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -                   
connorstom@penguin:~/aprojects/network-traffic$ sudo lsof -nP -i | grep 2222
sshd       97       root    3u  IPv4   3664      0t0  TCP *:2222 (LISTEN)
sshd       97       root    4u  IPv6   3666      0t0  TCP *:2222 (LISTEN)
sshd     3370       root    3u  IPv4 172739      0t0  TCP 100.115.92.195:2222->100.115.92.25:41452 (ESTABLISHED)
sshd     3376 connorstom    3u  IPv4 172739      0t0  TCP 100.115.92.195:2222->100.115.92.25:41452 (ESTABLISHED)
```

### SSH Penetration Testing (Port 22)
https://www.hackingarticles.in/ssh-penetration-testing-port-22/

Some Markdown text with <span style="color:red">some *red* text</span>

Some Markdown text with <span style="color:green">some *green* text</span>

Some Markdown text with <span style="color:yellow">some *yellow* text</span>

Some Markdown text with <span style="color:magenta">some *magenta* text</span>


## openssh-server
### SSH Penetration Testing (Port 22) 
https://www.hackingarticles.in/ssh-penetration-testing-port-22/
```bash
connorstom@penguin:~/aprojects/network-traffic$ sudo apt install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version (1:7.9p1-10+deb10u2).
openssh-server set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
```



### edit /etc/ssh/sshd_config
```bash
Logging
SyslogFacility AUTH

LogLevel VERBOSE

https://manpages.debian.org/testing/openssh-server/sshd_config.5.en.html
LogLevel INFO  -- this was the default original value
Gives the verbosity level that is used when logging messages from sshd(8). The possible values are: QUIET, FATAL, ERROR, INFO, VERBOSE, DEBUG, DEBUG1, DEBUG2, and DEBUG3. The default is INFO. DEBUG and DEBUG1 are equivalent. DEBUG2 and DEBUG3 each specify higher levels of debugging output. Logging with a DEBUG level violates the privacy of users and is not recommended.
```


# Misc
### ls -al /proc/
```bash
# ls -al /proc/
ls -al /proc/

Most reliable way is to look at the /proc dir for the process. Each process has a /proc/<pid>/ directory where it keeps information like:

`cwd` link to the current working directory
`fd` a dir with links to the open files (file descriptors)
`cmdline` read it to see what command line was used to start the process
`environ` the environment variables for that process
`root` a link to what the process considers its root dir (it will be / unless chrooted)
```

### When did a process first start?   ps -eo pid,lstart,cmd
```bash
ps -eo pid,lstart,cmd

 2177 Sat Dec  5 22:36:48 2020 sshd: connorstom [priv]
 2183 Sat Dec  5 22:36:50 2020 sshd: connorstom@notty
 2184 Sat Dec  5 22:36:50 2020 sshd: connorstom@internal-sftp
 2632 Sun Dec  6 00:18:11 2020 ps -eo pid,lstart,cmd

 # 
connorstom@penguin:/var/log/journal/34f82f01ee4a706f645f9d635f17bfe9$ ps -p 2177 -lF
F S UID        PID  PPID  C PRI  NI ADDR SZ WCHAN    RSS PSR STIME TTY          TIME CMD
4 S root      2177    97  0  80   0 -  4248 -       7916   1 Dec05 ?        00:00:00 sshd: connorstom [priv]
```
## cat /proc/2177/status
```bash
connorstom@penguin:/var/log/journal/34f82f01ee4a706f645f9d635f17bfe9$ cat /proc/2177/status
Name:   sshd
Umask:  0022
State:  S (sleeping)
Tgid:   2177
Ngid:   0
Pid:    2177
PPid:   97
TracerPid:      0
Uid:    0       0       0       0
Gid:    0       0       0       0
FDSize: 64
Groups:  
NStgid: 2177
NSpid:  2177
NSpgid: 2177
NSsid:  2177
VmPeak:    17024 kB
VmSize:    16992 kB
VmLck:         0 kB
VmPin:         0 kB
VmHWM:      8076 kB
VmRSS:      7916 kB
RssAnon:            1116 kB
RssFile:            6800 kB
RssShmem:              0 kB
VmData:     1056 kB
VmStk:       132 kB
VmExe:       496 kB
VmLib:      6724 kB
VmPTE:        72 kB
VmSwap:        0 kB
HugetlbPages:          0 kB
CoreDumping:    0
THP_enabled:    1
Threads:        1
SigQ:   0/11100
SigPnd: 0000000000000000
ShdPnd: 0000000000000000
SigBlk: 0000000000000000
SigIgn: 0000000001001000
SigCgt: 0000000180004003
CapInh: 0000000000000000
CapPrm: 0000003fffffffff
CapEff: 0000003fffffffff
CapBnd: 0000003fffffffff
CapAmb: 0000000000000000
NoNewPrivs:     0
Seccomp:        2
Speculation_Store_Bypass:       thread force mitigated
Cpus_allowed:   3
Cpus_allowed_list:      0-1
Mems_allowed:   1
Mems_allowed_list:      0
voluntary_ctxt_switches:        26
nonvoluntary_ctxt_switches:     118
```



###
```bash

```

###
```bash

```

###
```bash

```

###
```bash

```

###
```bash

```

###
```bash

```

###
```bash

```

###
```bash

```
