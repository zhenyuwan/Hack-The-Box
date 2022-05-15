# SMB 枚举

`smbmap -H IP_ADDR`

使用smbmap枚举靶机的smb share

**-H** 指靶机地址



`smbmap -H IPADDR -R smb_share_name --depth 5`

**-R** 可以用smbmap去枚举smb share里的中所有的文件

**--depth** 指定smbmap搜索深度

**注意**：smbmap默认的搜索深度是5



`smbmap -d DOMAIN_NAME -u USER_NAME -p PASSWORD -H IP_ADDR`

此命令可以枚举该用户对smb share的权限



