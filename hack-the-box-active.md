---
description: 2022.5.14
---

# Hack the box - Active

{% embed url="https://www.youtube.com/watch?t=623s&v=jUc1J31DNdw" %}

在本视频的9分12秒处，IPPsec 在用smbmap枚举share的时候用的指令是：

`smbmap -R Replication -H 10.10.10.100`

估计是因为smbmap更新的原因，现在smbmap在枚举share的时候多了默认的搜索深度，现在默认深度为5

现在如果在kali上smbmap需要加上--depth 6 才能看到Groups.xml文件

`smbmap -R Replication -H 10.10.10.100 --depth 6`
