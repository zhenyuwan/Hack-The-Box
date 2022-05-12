# Nmap 使用心得

`nmap -p- --min-rate 10000 IP_ADDR > nmap.txt`

用nmap快速扫描靶机地址，并将结果导入nmap.txt文档

\-p- 表示扫描所有端口

\--min-rate 每秒最少发送包的数量

`cat nmap.txt | awk '{print $1}' | sed 's/[^0-9]*//g' | sed '/^$/d' > ports.txt`

awk '{print $1}' 会打印第一列的数据

sed 's/\[^0-9]\*//g' 将第一列的数据只保留数字，也就是端口
