# Windows AD 杂七杂八

## .xml 文件

Windows server 2008 之前的系统会用xml文件格式储存GPO，也就是group policy object。这个文件是不被加密的，也就是说有权限更改权限的人可以更改GPO。



## Service Principle Name

{% embed url="https://docs.microsoft.com/en-us/windows/win32/ad/service-principal-names" %}

<mark style="color:red;">**没看懂，以后补充**</mark>

<mark style="color:red;">****</mark>

## **Kerberos TGS**

The goal of Kerberoasting is to harvest TGS tickets for services that run on behalf of user accounts in the AD, not computer accounts. Thus, part of these TGS tickets are encrypted with keys derived from user passwords. As a consequence, their credentials could be cracked offline.
