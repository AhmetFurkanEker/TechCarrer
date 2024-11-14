```
└──╼ #nmap -A 10.10.190.146
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-29 17:01 +03
Nmap scan report for 10.10.190.146
Host is up (0.12s latency).
Not shown: 991 closed tcp ports (reset)
PORT      STATE SERVICE      VERSION
135/tcp   open  msrpc        Microsoft Windows RPC
139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds Windows 7 Professional 7601 Service Pack 1 microsoft-ds (workgroup: WORKGROUP)
3389/tcp  open  tcpwrapped
|_ssl-date: 2024-10-29T14:03:24+00:00; 0s from scanner time.
| rdp-ntlm-info: 
|   Target_Name: JON-PC
|   NetBIOS_Domain_Name: JON-PC
|   NetBIOS_Computer_Name: JON-PC
|   DNS_Domain_Name: Jon-PC
|   DNS_Computer_Name: Jon-PC
|   Product_Version: 6.1.7601
|_  System_Time: 2024-10-29T14:03:09+00:00
| ssl-cert: Subject: commonName=Jon-PC
| Not valid before: 2024-10-28T13:56:35
|_Not valid after:  2025-04-29T13:56:35
49152/tcp open  msrpc        Microsoft Windows RPC
49153/tcp open  msrpc        Microsoft Windows RPC
49154/tcp open  msrpc        Microsoft Windows RPC
49158/tcp open  msrpc        Microsoft Windows RPC
49160/tcp open  msrpc        Microsoft Windows RPC
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.94SVN%E=4%D=10/29%OT=135%CT=1%CU=40195%PV=Y%DS=2%DC=T%G=Y%TM=67
OS:20EB2C%P=x86_64-pc-linux-gnu)SEQ(SP=103%GCD=1%ISR=10A%TI=I%CI=I%II=I%SS=
OS:S%TS=7)SEQ(SP=103%GCD=1%ISR=10A%TI=I%CI=RD%II=I%SS=S%TS=7)SEQ(SP=104%GCD
OS:=1%ISR=10A%TI=I%CI=I%II=I%SS=S%TS=7)OPS(O1=M508NW8ST11%O2=M508NW8ST11%O3
OS:=M508NW8NNT11%O4=M508NW8ST11%O5=M508NW8ST11%O6=M508ST11)WIN(W1=2000%W2=2
OS:000%W3=2000%W4=2000%W5=2000%W6=2000)ECN(R=Y%DF=Y%T=80%W=2000%O=M508NW8NN
OS:S%CC=N%Q=)T1(R=Y%DF=Y%T=80%S=O%A=S+%F=AS%RD=0%Q=)T2(R=Y%DF=Y%T=80%W=0%S=
OS:Z%A=S%F=AR%O=%RD=0%Q=)T3(R=Y%DF=Y%T=80%W=0%S=Z%A=O%F=AR%O=%RD=0%Q=)T4(R=
OS:Y%DF=Y%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T5(R=Y%DF=Y%T=80%W=0%S=Z%A=O%F=AR
OS:%O=%RD=0%Q=)T5(R=Y%DF=Y%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=
OS:80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T6(R=Y%DF=Y%T=80%W=0%S=O%A=O%F=R%O=%RD=0%Q
OS:=)T7(R=Y%DF=Y%T=80%W=0%S=Z%A=O%F=AR%O=%RD=0%Q=)T7(R=Y%DF=Y%T=80%W=0%S=Z%
OS:A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=80%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%
OS:RUCK=G%RUD=G)IE(R=Y%DFI=N%T=80%CD=Z)

Network Distance: 2 hops
Service Info: Host: JON-PC; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb-os-discovery: 
|   OS: Windows 7 Professional 7601 Service Pack 1 (Windows 7 Professional 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1:professional
|   Computer name: Jon-PC
|   NetBIOS computer name: JON-PC\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2024-10-29T09:03:09-05:00
|_clock-skew: mean: 59m59s, deviation: 2h14m09s, median: 0s
|_nbstat: NetBIOS name: JON-PC, NetBIOS user: <unknown>, NetBIOS MAC: 02:7b:51:48:ed:75 (unknown)
| smb2-time: 
|   date: 2024-10-29T14:03:09
|_  start_date: 2024-10-29T13:56:34
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2:1:0: 
|_    Message signing enabled but not required

TRACEROUTE (using port 53/tcp)
HOP RTT       ADDRESS
1   153.32 ms 10.11.0.1
2   153.41 ms 10.10.190.146

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 120.87 seconds
```
