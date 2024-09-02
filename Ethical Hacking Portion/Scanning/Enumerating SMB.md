SMB is basically a file sharing protocol(which is huge btw). It runs on port 139. 

Best way to deal with any sort of vulnerability is to use metasploit. 

For totally professional reasons, certs like OSCP do not allow the use of tools like metasploit. But since metasploit is used by professional pentesters and since this is a practical course, we would be using this tool as we speak.

You can start metasploit by the following command:

```bash
$ msfconsole
```

Then if you want to search for a certain protocol, you can do that by the following command:

```msfconsole
msf5 > search smb
```

We know that auxiliary modules are for enumeration so we can search auxiliary modules. So we can choose the option from the given results and then we can go to that by the following command:

```msfconsole
msf5 > use <module name>
```

Then make sure you run *info* to know how to use that particular thing.

Note: RHOSTS stands for Remote Hosts and LHOSTS stands for Local Hosts

Then you can run the following commands one after the another to do SMB enumeration:

```msfconsole
set RHOSTS <ip_address_of_target>
run
```

We now use a tool called smbclient. What this does is it tries to connect to the fileshare with anonymous access. We can try this with the following command:

```
smbclient -L \\\\<ip_address>\\
```

It is important to have atleast 2 backslashes at the beginning of the command. If you have 4 backslashes, you need to have 2 backslashes at the end and if you have 2 in the beginning, you dont have to have any in the end.

-L lists the fileshares in the target

We can connect to a fileshare by removing the -L and adding the name of the fileshare after the 2 backslashes in the previous command. 

```
smbclient \\\\<ip_address>\\IPC$
```
