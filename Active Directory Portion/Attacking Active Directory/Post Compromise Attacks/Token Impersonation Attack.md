What are tokens?

They are temporary keys that allow you access to a system/network without having to provide credentials each time you access a file. Think cookies for computers.

There are two types of tokens:

1) Delegate: Created for logging into a machine or using Remote Desktop
2) Impersonate: 'non-interactive' such as attaching a network drive or a domain logon script.

Why is it bad?

![[Pasted image 20240829100843.png]]

Pop a shell and load incognito

![[Pasted image 20240829100930.png]]

Impersonate our domain user

![[Pasted image 20240829101004.png]]

Attempt to dump hashes as non-Domain Admin

Alright, but what if a domain admin was available?

![[Pasted image 20240829101111.png]]

Identify Domain Administrator

![[Pasted image 20240829101200.png]]

Impersonate our Domain Administrator

![[Pasted image 20240829101240.png]]

Attempt to dump hashes as Domain Admin. Here, we're using a tool called mimikatz.

![[Pasted image 20240829101324.png]]

Win!!

Here's a better example:

![[Pasted image 20240829101435.png]]

Attempt to add a new user as Domain Admin

![[Pasted image 20240829101517.png]]

Compromise the DC!

Mitigation:

1) Limit user/group token creation permission
2) Account tiering
3) Local admin restriction

![[Pasted image 20240829102909.png]]

