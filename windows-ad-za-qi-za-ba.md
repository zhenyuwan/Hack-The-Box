# Windows AD 杂七杂八

## .xml 文件

Windows server 2008 之前的系统会用xml文件格式储存GPO，也就是group policy object。这个文件是不被加密的，也就是说有权限更改权限的人可以更改GPO。



## Service Principle Name

A service principal name (SPN) is a **unique identifier** of a service instance. SPNs are used by **Kerberos authentication** to associate a service instance with a service logon account. This allows a client application to request service to authenticate an account even if the client does not have the account name.
