We own the domain, now what?

Provide as much value to the client as possible:
1) Put your blinders on and do it again
2) Dump the NTDS.dit file and crack passwords
3) Enumerate shares for sensitive information

Persistence can be important:
1) What happens if our DA(Domain Admin) access is lost?
2) Creating a DA account can be useful(DO NOT FORGET TO DELETE IT)
3) Creating a Golden Ticket can be useful too

Dumping the NTDS.dit file

What is it?

A database used to store AD data. This data includes:
1) User Information
2) Group Information
3) Security Descriptors 
4) And oh yea, password hashes

We can simply use secretsdump against the DC to perform this attack:

![[Pasted image 20240829153402.png]]


Golden Ticket Attack

What is it?

1) When we compromise the krbtgt account, we own the domain
2) We can request access to any resource or system on the domain
3) Golden tickets == complete access to every machine

We use mimikatz for this attack. We can use this tool to obtain the information necessary to perform this attack.

![[Pasted image 20240829180416.png]]

Once we have the SID(One next to Marvel / in domain) and krbtgt hash(one under Primary in front of NTLM), we can generate a ticket.

![[Pasted image 20240829180458.png]]

With a Golden Ticket, we can now access other machines from the command line.

![[Pasted image 20240829180542.png]]

