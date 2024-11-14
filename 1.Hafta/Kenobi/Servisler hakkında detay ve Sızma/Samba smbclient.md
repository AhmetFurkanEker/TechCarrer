Samba üzerinde farklı araçlarla enumeratıon yapabiliriz bunların bazıları aşağıda ki gibidir. 

- enum4linux
- smbclient
- nmap

#### nmap 

```
└──╼ #nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse 10.10.30.127
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-10-22 15:19 +03
Nmap scan report for 10.10.30.127
Host is up (0.072s latency).

PORT    STATE SERVICE
445/tcp open  microsoft-ds

Host script results:
| smb-enum-shares: 
|   account_used: guest
|   \\10.10.30.127\IPC$: 
|     Type: STYPE_IPC_HIDDEN
|     Comment: IPC Service (kenobi server (Samba, Ubuntu))
|     Users: 1
|     Max Users: <unlimited>
|     Path: C:\tmp
|     Anonymous access: READ/WRITE
|     Current user access: READ/WRITE
|   \\10.10.30.127\anonymous: 
|     Type: STYPE_DISKTREE
|     Comment: 
|     Users: 0
|     Max Users: <unlimited>
|     Path: C:\home\kenobi\share
|     Anonymous access: READ/WRITE
|     Current user access: READ/WRITE
|   \\10.10.30.127\print$: 
|     Type: STYPE_DISKTREE
|     Comment: Printer Drivers
|     Users: 0
|     Max Users: <unlimited>
|     Path: C:\var\lib\samba\printers
|     Anonymous access: <none>
|_    Current user access: <none>

Nmap done: 1 IP address (1 host up) scanned in 16.97 seconds
```

Nmap ile yaptığımız enumeratıon sonucu üç farklı dizin keşfettik. 
- \\10.10.30.127\print$
- \\10.10.30.127\anonymous
- \\10.10.30.127\IPC$

#### enum4linux

```
└──╼ #enum4linux -a 10.10.30.127
Starting enum4linux v0.9.1 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Tue Oct 22 15:29:28 2024

 =========================================( Target Information )=========================================

Target ........... 10.10.30.127
RID Range ........ 500-550,1000-1050
Username ......... ''
Password ......... ''
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none


 ============================( Enumerating Workgroup/Domain on 10.10.30.127 )============================


[+] Got domain/workgroup name: WORKGROUP


 ================================( Nbtstat Information for 10.10.30.127 )================================

Looking up status of 10.10.30.127
	KENOBI          <00> -         B <ACTIVE>  Workstation Service
	KENOBI          <03> -         B <ACTIVE>  Messenger Service
	KENOBI          <20> -         B <ACTIVE>  File Server Service
	..__MSBROWSE__. <01> - <GROUP> B <ACTIVE>  Master Browser
	WORKGROUP       <00> - <GROUP> B <ACTIVE>  Domain/Workgroup Name
	WORKGROUP       <1d> -         B <ACTIVE>  Master Browser
	WORKGROUP       <1e> - <GROUP> B <ACTIVE>  Browser Service Elections

	MAC Address = 00-00-00-00-00-00

 ===================================( Session Check on 10.10.30.127 )===================================


[+] Server 10.10.30.127 allows sessions using username '', password ''


 ================================( Getting domain SID for 10.10.30.127 )================================

Domain Name: WORKGROUP
Domain Sid: (NULL SID)

[+] Can't determine if host is part of domain or part of a workgroup


 ===================================( OS information on 10.10.30.127 )===================================


[E] Can't get OS info with smbclient


[+] Got OS info for 10.10.30.127 from srvinfo: 
	KENOBI         Wk Sv PrQ Unx NT SNT kenobi server (Samba, Ubuntu)
	platform_id     :	500
	os version      :	6.1
	server type     :	0x809a03


 =======================================( Users on 10.10.30.127 )=======================================

Use of uninitialized value $users in print at ./enum4linux.pl line 972.
Use of uninitialized value $users in pattern match (m//) at ./enum4linux.pl line 975.

Use of uninitialized value $users in print at ./enum4linux.pl line 986.
Use of uninitialized value $users in pattern match (m//) at ./enum4linux.pl line 988.

 =================================( Share Enumeration on 10.10.30.127 )=================================


	Sharename       Type      Comment
	---------       ----      -------
	print$          Disk      Printer Drivers
	anonymous       Disk      
	IPC$            IPC       IPC Service (kenobi server (Samba, Ubuntu))
Reconnecting with SMB1 for workgroup listing.

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
	WORKGROUP            KENOBI

[+] Attempting to map shares on 10.10.30.127

//10.10.30.127/print$	Mapping: DENIED Listing: N/A Writing: N/A
//10.10.30.127/anonymous	Mapping: OK Listing: OK Writing: N/A

[E] Can't understand response:

NT_STATUS_OBJECT_NAME_NOT_FOUND listing \*
//10.10.30.127/IPC$	Mapping: N/A Listing: N/A Writing: N/A

 ============================( Password Policy Information for 10.10.30.127 )============================



[+] Attaching to 10.10.30.127 using a NULL share

[+] Trying protocol 139/SMB...

[+] Found domain(s):

	[+] KENOBI
	[+] Builtin

[+] Password Info for Domain: KENOBI

	[+] Minimum password length: 5
	[+] Password history length: None
	[+] Maximum password age: 37 days 6 hours 21 minutes 
	[+] Password Complexity Flags: 000000

		[+] Domain Refuse Password Change: 0
		[+] Domain Password Store Cleartext: 0
		[+] Domain Password Lockout Admins: 0
		[+] Domain Password No Clear Change: 0
		[+] Domain Password No Anon Change: 0
		[+] Domain Password Complex: 0

	[+] Minimum password age: None
	[+] Reset Account Lockout Counter: 30 minutes 
	[+] Locked Account Duration: 30 minutes 
	[+] Account Lockout Threshold: None
	[+] Forced Log off Time: 37 days 6 hours 21 minutes 



[+] Retieved partial password policy with rpcclient:


Password Complexity: Disabled
Minimum Password Length: 5


 =======================================( Groups on 10.10.30.127 )=======================================


[+] Getting builtin groups:


[+]  Getting builtin group memberships:


[+]  Getting local groups:


[+]  Getting local group memberships:


[+]  Getting domain groups:


[+]  Getting domain group memberships:


 ==================( Users on 10.10.30.127 via RID cycling (RIDS: 500-550,1000-1050) )==================


[I] Found new SID: 
S-1-22-1

[I] Found new SID: 
S-1-5-32

[I] Found new SID: 
S-1-5-32

[I] Found new SID: 
S-1-5-32

[I] Found new SID: 
S-1-5-32

[+] Enumerating users using SID S-1-22-1 and logon username '', password ''

S-1-22-1-1000 Unix User\kenobi (Local User)

[+] Enumerating users using SID S-1-5-21-55073928-793008161-2116500600 and logon username '', password ''

S-1-5-21-55073928-793008161-2116500600-501 KENOBI\nobody (Local User)
S-1-5-21-55073928-793008161-2116500600-513 KENOBI\None (Domain Group)

[+] Enumerating users using SID S-1-5-32 and logon username '', password ''

S-1-5-32-544 BUILTIN\Administrators (Local Group)
S-1-5-32-545 BUILTIN\Users (Local Group)
S-1-5-32-546 BUILTIN\Guests (Local Group)
S-1-5-32-547 BUILTIN\Power Users (Local Group)
S-1-5-32-548 BUILTIN\Account Operators (Local Group)
S-1-5-32-549 BUILTIN\Server Operators (Local Group)
S-1-5-32-550 BUILTIN\Print Operators (Local Group)

 ===============================( Getting printer info for 10.10.30.127 )===============================

No printers returned.


enum4linux complete on Tue Oct 22 15:34:59 2024

```


`enum4linux` aracı kullanılarak, belirtilen IP adresinin `WORKGROUP` içinde olduğu, Samba sunucusunun `KENOBI` adında olduğu, Ubuntu 6.1 üzerinde çalıştığı, `print$`, `anonymous` ve `IP$` paylaşımlarının bulunduğu tespit edilmiştir. Ayrıca, `print$` paylaşımına erişimin reddedildiği, `anonymous` paylaşımına ise erişim sağlandığı ve içeriğin listelendiği belirlenmiştir.

#### smbclient

enum4linux ile zaten anonymous paylaşıma erişebilmiştik. smbclient ile bağlantı sağlayarak paylaşım içerisinde  log.txt dosyasını yerel klasörümüze get komutu ile indirdik.

![[Kenobismbclient.png]]