# Nmap 使用心得

nmap -p- --min-rate 10000 IP\_ADDR > nmap.txt

cat nmap.txt | awk '{print $1}' | sed 's/\[^0-9]\*//g' | sed '/^$/d' > ports.txt

