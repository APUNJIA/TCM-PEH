Overview:

1) Its is a tool used to view and steal credentials, generate kerberos tickets and leverage attacks
2) Dump credentials stored in memory
3) Just a few attacks: Credential Dumping, Pass-The-Hash, Over-Pass-The-Hash, Pass-The-Ticket, Silver Ticket and Golden Ticket

How to run Mimikatz

Its a very powerful tool and it is picked up by pretty much any antivirus out there so someone has to be super dumb to run this in the first place. 

So first things first, we have to ensure mimikatz is on his system and then we use the command prompt to run the application on the target machine. 

Once we run it, we run this command:

```
privilege::debug
sekurlsa::logonPasswords
```

![[Pasted image 20240829123956.png]]

Thats the password of the Domain Controller.