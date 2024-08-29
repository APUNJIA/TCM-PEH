It was an internal network in a large US hospital. It was well funded and had invested Millions in security measures.

Defenses: IPv6 Disabled(so no mitm6), Intrusion Detection and Prevention(IDS/IPS), CyberArk(Privilege Access Management), and Systematic Endpoint Security on all devices.

Because of these defenses, we cannot run LLMNR and IPv6 attacks, but we can run SMB relay attacks. And it worked.

Once they gained access on the machine, they were able to dump the SAM hashes on the machine. It showed that the AD had 3 users: "techsupport", "TechSupport2", "\_\_admin" . If we look at the hash information, we can see that the Administrator user and both tech support users have the same hash, which means all 3 users have the same password.

They can then pass the hash around in the environment(pass-the-hash attack) to see what all domains they can gain access to 

Once they got the access to all the machines, they logged into various machines and dumped the hash data. Eventually one of the hashes worked on the DC.

Lessons Learnt:

1) Enable SMB signing (and disable LLMNR)
2) Least Privilege
3) Account Tiering
4) DONT REUSE YOUR PASSWORDS

https://tcm-sec.com/pentest-tales-001-you-spent-how-much-on-security