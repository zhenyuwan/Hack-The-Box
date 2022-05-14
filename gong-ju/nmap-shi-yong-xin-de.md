# Nmap 使用笔记

`nmap -p- --min-rate 10000 IP_ADDR > nmap.txt`

用nmap快速扫描靶机地址，并将结果导入nmap.txt文档

**-p-** 表示扫描所有端口

**--min-rate** 每秒最少发送包的数量

**IP\_ADDR** 这是指靶机地址

``

`cat nmap.txt | awk '{print $1}' | sed 's/[^0-9]*//g' | sed '/^$/d' | paste -s -d, - > ports.txt`

**awk '{print $1}'** 会打印第一列的数据

**sed 's/\[^0-9]\*//g'** 将第一列的数据只保留数字，也就是端口

**sed '/^$/d'** 将第一列数据的空行去掉

**paste -s -d, -** 这个工具可以把一列数据转换成CSV文件

&#x20;**> ports.txt** 将处理过的数据保存进入ports.txt文件



`nmap -sC -sV -p $(cat ports.txt) IP_ADDR`

**-sC** 是指使用nmap默认script扫描靶机

**-sV** 是指扫描靶机地址上运行程序的版本

**$(cat ports.txt)** 是将cat ports.txt的结果当做一个数据输入指令

## 寻找NSE脚本

`locate -r  '\.nse$'`

**-r** 让locate 读取正则表达式

**$** 指寻找任何一行以.nse后缀结尾的文件



在找的具体的文件后，可以使用 grep 抓取nse script类别信息

`locate -r '\.nse$' | xargs grep categories`

xargs 的作用在于将 locate 指令返回的信息输入grep.

比方说 locate 里有一个nse脚本位置是 /usr/share/nmap/scripts/alp-brute.nse

xargs 会执行 grep categories /usr/share/nmap/scripts/alp-brute.nse 这个指令
