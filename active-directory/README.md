---
cover: >-
  https://miro.medium.com/v2/resize:fit:1320/format:webp/1*4fn2P_4lwgx6c6ImyKrvRA.jpeg
coverY: 0
layout:
  cover:
    visible: true
    size: hero
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Active Directory

\


<table><thead><tr><th width="269">Tool</th><th>Description</th></tr></thead><tbody><tr><td>PowerView/SharpView</td><td>A PowerShell tool and a .NET port of the same used to gain situational awareness in AD. These tools can be used as replacements for various Windows net* commands and more. PowerView and SharpView can help us gather much of the data that BloodHound does, but it requires more work to make meaningful relationships among all of the data points. These tools are great for checking what additional access we may have with a new set of credentials, targeting specific users or computers, or finding some "quick wins" such as users that can be attacked via Kerberoasting or ASREPRoasting.</td></tr><tr><td>BloodHound</td><td>Used to visually map out AD relationships and help plan attack paths that may otherwise go unnoticed. Uses the SharpHound PowerShell or C# ingestor to gather data to later be imported into the BloodHound JavaScript (Electron) application with a Neo4j database for graphical analysis of the AD environment.</td></tr><tr><td>SharpHound</td><td>The C# data collector to gather information from Active Directory about varying AD objects such as users, groups, computers, ACLs, GPOs, user and computer attributes, user sessions, and more. The tool produces JSON files which can then be ingested into the BloodHound GUI tool for analysis.</td></tr><tr><td>BloodHound.py</td><td>A Python-based BloodHound ingestor based on the Impacket toolkit. It supports most BloodHound collection methods and can be run from a non-domain joined attack host. The output can be ingested into the BloodHound GUI for analysis.</td></tr><tr><td>Kerbrute</td><td>A tool written in Go that uses Kerberos Pre-Authentication to enumerate Active Directory accounts, perform password spraying, and brute-forcing.</td></tr><tr><td>Impacket toolkit</td><td>A collection of tools written in Python for interacting with network protocols. The suite of tools contains various scripts for enumerating and attacking Active Directory.</td></tr><tr><td>Responder</td><td>Responder is a purpose-built tool to poison LLMNR, NBT-NS, and MDNS, with many different functions.</td></tr><tr><td>Inveigh.ps1</td><td>Similar to Responder, a PowerShell tool for performing various network spoofing and poisoning attacks.</td></tr><tr><td>C# Inveigh (InveighZero)</td><td>The C# version of Inveigh with a semi-interactive console for interacting with captured data such as username and password hashes.</td></tr><tr><td>rpcinfo</td><td>The rpcinfo utility is used to query the status of an RPC program or enumerate the list of available RPC services on a remote host. The "-p" option is used to specify the target host. For example the command "rpcinfo -p 10.0.0.1" will return a list of all the RPC services available on the remote host, along with their program number, version number, and protocol. Note that this command must be run with sufficient privileges.</td></tr><tr><td>rpcclient</td><td>A part of the Samba suite on Linux distributions that can be used to perform a variety of Active Directory enumeration tasks via the remote RPC service.</td></tr><tr><td>CrackMapExec (CME)</td><td>CME is an enumeration, attack, and post-exploitation toolkit which can help us greatly in enumeration and performing attacks with the data we gather. CME attempts to "live off the land" and abuse built-in AD features and protocols like SMB, WMI, WinRM, and MSSQL.</td></tr><tr><td>Rubeus</td><td>Rubeus is a C# tool built for Kerberos Abuse.</td></tr><tr><td>GetUserSPNs.py</td><td>Another Impacket module geared towards finding Service Principal names tied to normal users.</td></tr><tr><td>Hashcat</td><td>A great hash cracking and password recovery tool.</td></tr><tr><td>enum4linux</td><td>A tool for enumerating information from Windows and Samba systems.</td></tr><tr><td>enum4linux-ng</td><td>A rework of the original Enum4linux tool that works a bit differently.</td></tr><tr><td>ldapsearch</td><td>Built-in interface for interacting with the LDAP protocol.</td></tr><tr><td>windapsearch</td><td>A Python script used to enumerate AD users, groups, and computers using LDAP queries. Useful for automating custom LDAP queries.</td></tr><tr><td>DomainPasswordSpray.ps1</td><td>DomainPasswordSpray is a tool written in PowerShell to perform a password spray attack against users of a domain.</td></tr><tr><td>LAPSToolkit</td><td>The toolkit includes functions written in PowerShell that leverage PowerView to audit and attack Active Directory environments that have deployed Microsoft's Local Administrator Password Solution (LAPS).</td></tr><tr><td>smbmap</td><td>SMB share enumeration across a domain.</td></tr><tr><td>psexec.py</td><td>Part of the Impacket toolkit, it provides us with Psexec-like functionality in the form of a semi-interactive shell.</td></tr><tr><td>wmiexec.py</td><td>Part of the Impacket toolkit, it provides the capability of command execution over WMI.</td></tr><tr><td>Snaffler</td><td>Useful for finding information (such as credentials) in Active Directory on computers with accessible file shares.</td></tr><tr><td>smbserver.py</td><td>Simple SMB server execution for interaction with Windows hosts. Easy way to transfer files within a network.</td></tr><tr><td>setspn.exe</td><td>Adds, reads, modifies and deletes the Service Principal Names (SPN) directory property for an Active Directory service account.</td></tr><tr><td>Mimikatz</td><td>Performs many functions. Notably, pass-the-hash attacks, extracting plaintext passwords, and Kerberos ticket extraction from memory on a host.</td></tr><tr><td>secretsdump.py</td><td>Remotely dump SAM and LSA secrets from a host.</td></tr><tr><td>evil-winrm</td><td>Provides us with an interactive shell on a host over the WinRM protocol.</td></tr><tr><td>mssqlclient.py</td><td>Part of the Impacket toolkit, it provides the ability to interact with MSSQL databases.</td></tr><tr><td>noPac.py</td><td>Exploit combo using CVE-2021-42278 and CVE-2021-42287 to impersonate DA from standard domain user.</td></tr><tr><td>rpcdump.py</td><td>Part of the Impacket toolset, RPC endpoint mapper.</td></tr><tr><td>CVE-2021-1675.py</td><td>Printnightmare PoC in python.</td></tr><tr><td>ntlmrelayx.py</td><td>Part of the Impacket toolset, it performs SMB relay attacks.</td></tr><tr><td>PetitPotam.py</td><td>PoC tool for CVE-2021-36942 to coerce Windows hosts to authenticate to other machines via MS-EFSRPC EfsRpcOpenFileRaw or other functions.</td></tr><tr><td>gettgtpkinit.py</td><td>Tool for manipulating certificates and TGTs.</td></tr><tr><td>getnthash.py</td><td>This tool will use an existing TGT to request a PAC for the current user using U2U.</td></tr><tr><td>adidnsdump</td><td>A tool for enumerating and dumping DNS records from a domain. Similar to performing a DNS Zone transfer.</td></tr><tr><td>gpp-decrypt</td><td>Extracts usernames and passwords from Group Policy preferences files.</td></tr><tr><td>GetNPUsers.py</td><td>Part of the Impacket toolkit. Used to perform the ASREPRoasting attack to list and obtain AS-REP hashes for users with the 'Do not require Kerberos preauthentication' set. These hashes are then fed into a tool such as Hashcat for attempts at offline password cracking.</td></tr><tr><td>lookupsid.py</td><td>SID bruteforcing tool.</td></tr><tr><td>ticketer.py</td><td>A tool for creation and customization of TGT/TGS tickets. It can be used for Golden Ticket creation, child to parent trust attacks, etc.</td></tr><tr><td>raiseChild.py</td><td>Part of the Impacket toolkit, It is a tool for automated child to parent domain privilege escalation.</td></tr><tr><td>Active Directory Explorer</td><td>Active Directory Explorer (AD Explorer) is an AD viewer and editor. It can be used to navigate an AD database and view object properties and attributes. It can also be used to save a snapshot of an AD database for offline analysis. When an AD snapshot is loaded, it can be explored as a live version of the database. It can also be used to compare two AD database snapshots to see changes in objects, attributes, and security permissions.</td></tr><tr><td>PingCastle</td><td>Used for auditing the security level of an AD environment based on a risk assessment and maturity framework (based on CMMI adapted to AD security).</td></tr><tr><td>Group3r</td><td>Group3r is useful for auditing and finding security misconfigurations in AD Group Policy Objects (GPO).</td></tr><tr><td>ADRecon</td><td>A tool used to extract various data from a target AD environment. The data can be output in Microsoft Excel format with summary views and analysis to assist with analysis and paint a picture of the environment's overall security state.</td></tr></tbody></table>

### Checking the Status of Defender with Get-MpComputerStatus

Checking the Status of Defender with Get-MpComputerStatus

```powershell
PS C:\htb> Get-MpComputerStatus

AMEngineVersion : 1.1.17400.5
AMProductVersion : 4.10.14393.0
AMServiceEnabled : True
AMServiceVersion : 4.10.14393.0
AntispywareEnabled : True
AntispywareSignatureAge : 1
AntispywareSignatureLastUpdated : 9/2/2020 11:31:50 AM
AntispywareSignatureVersion : 1.323.392.0
AntivirusEnabled : True
AntivirusSignatureAge : 1
AntivirusSignatureLastUpdated : 9/2/2020 11:31:51 AM
AntivirusSignatureVersion : 1.323.392.0
BehaviorMonitorEnabled : False
ComputerID : 07D23A51-F83F-4651-B9ED-110FF2B83A9C
ComputerState : 0
FullScanAge : 4294967295
FullScanEndTime :
FullScanStartTime :
IoavProtectionEnabled : False
LastFullScanSource : 0
LastQuickScanSource : 2
NISEnabled : False
NISEngineVersion : 0.0.0.0
NISSignatureAge : 4294967295
NISSignatureLastUpdated :
NISSignatureVersion : 0.0.0.0
OnAccessProtectionEnabled : False
QuickScanAge : 0
QuickScanEndTime : 9/3/2020 12:50:45 AM
QuickScanStartTime : 9/3/2020 12:49:49 AM
RealTimeProtectionEnabled : True
RealTimeScanDirection : 0
PSComputerName :
```

### AppLocker

An application whitelist is a list of approved software applications or executables that are allowed to be present and run on a system. The goal is to protect the environment from harmful malware and unapproved software that does not align with the specific business needs of an organization. [AppLocker](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-defender-application-control/applocker/what-is-applocker) is Microsoft's application whitelisting solution and gives system administrators control over which applications and files users can run. It provides granular control over executables, scripts, Windows installer files, DLLs, packaged apps, and packed app installers. It is common for organizations to block cmd.exe and PowerShell.exe and write access to certain directories, but this can all be bypassed. Organizations also often focus on blocking the `PowerShell.exe` executable, but forget about the other [PowerShell executable locations](https://www.powershelladmin.com/wiki/PowerShell\_Executables\_File\_System\_Locations) such as `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe` or `PowerShell_ISE.exe`. We can see that this is the case in the `AppLocker` rules shown below. All Domain Users are disallowed from running the 64-bit PowerShell executable located at:\
`%SystemRoot%\system32\WindowsPowerShell\v1.0\powershell.exe`\
So, we can merely call it from other locations. Sometimes, we run into more stringent `AppLocker` policies that require more creativity to bypass. These ways will be covered in other modules.

### Using Get-AppLockerPolicy cmdlet

Using Get-AppLockerPolicy cmdlet

\


{% code overflow="wrap" lineNumbers="true" fullWidth="true" %}
```powershell
PS C:\htb> Get-AppLockerPolicy -Effective | select -ExpandProperty RuleCollections
PathConditions : {%SYSTEM32%\WINDOWSPOWERSHELL\V1.0\POWERSHELL.EXE}
PathExceptions : {}
PublisherExceptions : {}
HashExceptions : {}
Id : 3d57af4a-6cf8-4e5b-acfc-c2c2956061fa
Name : Block PowerShell
Description : Blocks Domain Users from using PowerShell on workstations
UserOrGroupSid : S-1-5-21-2974783224-3764228556-2640795941-513
Action : Deny
PathConditions : {%PROGRAMFILES%\*}
PathExceptions : {}
PublisherExceptions : {}
HashExceptions : {}
Id : 921cc481-6e17-4653-8f75-050b80acca20
Name : (Default Rule) All files located in the Program Files folder
Description : Allows members of the Everyone group to run applications that are located in the Program Files folder.
UserOrGroupSid : S-1-1-0
Action : Allow
PathConditions : {%WINDIR%\*}
PathExceptions : {}
PublisherExceptions : {}
HashExceptions : {}
Id : a61c8b2c-a319-4cd0-9690-d2177cad7b51
Name : (Default Rule) All files located in the Windows folder
Description : Allows members of the Everyone group to run applications that are located in the Windows folder.
UserOrGroupSid : S-1-1-0
Action : Allow
PathConditions : {*}
PathExceptions : {}
PublisherExceptions : {}
HashExceptions : {}
Id : fd686d83-a829-4351-8ff4-27c7de5755d2
Name : (Default Rule) All files
Description : Allows members of the local Administrators group to run all applications.
UserOrGroupSid : S-1-5-32-544
Action : Allow
```
{% endcode %}



### PowerShell Constrained Language Mode

PowerShell [Constrained Language Mode](https://devblogs.microsoft.com/powershell/powershell-constrained-language-mode/) locks down many of the features needed to use PowerShell effectively, such as blocking COM objects, only allowing approved .NET types, XAML-based workflows, PowerShell classes, and more. We can quickly enumerate whether we are in Full Language Mode or Constrained Language Mode.

#### Enumerating Language Mode

Enumerating Language Mode

```powershell
PS C:\htb> $ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

### LAPS

The Microsoft [Local Administrator Password Solution (LAPS)](https://www.microsoft.com/en-us/download/details.aspx?id=46899) is used to randomize and rotate local administrator passwords on Windows hosts and prevent lateral movement. We can enumerate what domain users can read the LAPS password set for machines with LAPS installed and what machines do not have LAPS installed. The [LAPSToolkit](https://github.com/leoloobeek/LAPSToolkit) greatly facilitates this with several functions. One is parsing `ExtendedRights` for all computers with LAPS enabled. This will show groups specifically delegated to read LAPS passwords, which are often users in protected groups. An account that has joined a computer to a domain receives `All Extended Rights` over that host, and this right gives the account the ability to read passwords. Enumeration may show a user account that can read the LAPS password on a host. This can help us target specific AD users who can read LAPS passwords.

### Using Find-LAPSDelegatedGroups

Using Find-LAPSDelegatedGroups

```powershell
PS C:\htb> Find-LAPSDelegatedGroups
OrgUnit Delegated Groups
------- ----------------
OU=Servers,DC=INLANEFREIGHT,DC=LOCAL INLANEFREIGHT\Domain Admins
OU=Servers,DC=INLANEFREIGHT,DC=LOCAL INLANEFREIGHT\LAPS Admins
OU=Workstations,DC=INLANEFREIGHT,DC=LOCAL INLANEFREIGHT\Domain Admins
OU=Workstations,DC=INLANEFREIGHT,DC=LOCAL INLANEFREIGHT\LAPS Admins
OU=Web Servers,OU=Servers,DC=INLANEFREIGHT,DC=LOCAL INLANEFREIGHT\Domain Admins
OU=Web Servers,OU=Servers,DC=INLANEFREIGHT,DC=LOCAL INLANEFREIGHT\LAPS Admins
OU=SQL Servers,OU=Servers,DC=INLANEFREIGHT,DC=LOCAL INLANEFREIGHT\Domain Admins
OU=SQL Servers,OU=Servers,DC=INLANEFREIGHT,DC=LOCAL INLANEFREIGHT\LAPS Admins
OU=File Servers,OU=Servers,DC=INLANEFREIGHT,DC=L... INLANEFREIGHT\Domain Admins
OU=File Servers,OU=Servers,DC=INLANEFREIGHT,DC=L... INLANEFREIGHT\LAPS Admins
OU=Contractor Laptops,OU=Workstations,DC=INLANEF... INLANEFREIGHT\Domain Admins
OU=Contractor Laptops,OU=Workstations,DC=INLANEF... INLANEFREIGHT\LAPS Admins
OU=Staff Workstations,OU=Workstations,DC=INLANEF... INLANEFREIGHT\Domain Admins
OU=Staff Workstations,OU=Workstations,DC=INLANEF... INLANEFREIGHT\LAPS Admins
OU=Executive Workstations,OU=Workstations,DC=INL... INLANEFREIGHT\Domain Admins
OU=Executive Workstations,OU=Workstations,DC=INL... INLANEFREIGHT\LAPS Admins
OU=Mail Servers,OU=Servers,DC=INLANEFREIGHT,DC=L... INLANEFREIGHT\Domain Admins
OU=Mail Servers,OU=Servers,DC=INLANEFREIGHT,DC=L... INLANEFREIGHT\LAPS Admins
```

The `Find-AdmPwdExtendedRights` checks the rights on each computer with LAPS enabled for any groups with read access and users with "All Extended Rights." Users with "All Extended Rights" can read LAPS passwords and may be less protected than users in delegated groups, so this is worth checking for.

### Using Find-AdmPwdExtendedRights

Using Find-AdmPwdExtendedRights\
`PS C:\htb> Find-AdmPwdExtendedRights`

`ComputerName Identity Reason`\
`------------ -------- ------`\
`EXCHG01.INLANEFREIGHT.LOCAL INLANEFREIGHT\Domain Admins Delegated`\
`EXCHG01.INLANEFREIGHT.LOCAL INLANEFREIGHT\LAPS Admins Delegated`\
`SQL01.INLANEFREIGHT.LOCAL INLANEFREIGHT\Domain Admins Delegated`\
`SQL01.INLANEFREIGHT.LOCAL INLANEFREIGHT\LAPS Admins Delegated`\
`WS01.INLANEFREIGHT.LOCAL INLANEFREIGHT\Domain Admins Delegated`\
`WS01.INLANEFREIGHT.LOCAL INLANEFREIGHT\LAPS Admins Delegated`

We can use the `Get-LAPSComputers` function to search for computers that have LAPS enabled when passwords expire, and even the randomized passwords in cleartext if our user has access.

### Using Get-LAPSComputers

Using Get-LAPSComputers\
`PS C:\htb> Get-LAPSComputers`

`ComputerName Password Expiration`\
`------------ -------- ----------`\
`DC01.INLANEFREIGHT.LOCAL 6DZ[+A/[]19d$F 08/26/2020 23:29:45`\
`EXCHG01.INLANEFREIGHT.LOCAL oj+2A+[hHMMtj, 09/26/2020 00:51:30`\
`SQL01.INLANEFREIGHT.LOCAL 9G#f;p41dcAe,s 09/26/2020 00:30:09`\
`WS01.INLANEFREIGHT.LOCAL TCaG-F)3No;l8C 09/26/2020 00:46:04`
