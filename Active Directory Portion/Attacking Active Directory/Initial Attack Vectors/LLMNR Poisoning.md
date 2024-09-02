What is LLMNR?

It stands for Link Local Multi-Cast Name Resolution.  It is used to identify hosts when DNS fails to do so. It was previously called NBT-NS. Key flaw is that the services utilize a user's username and NTLMv2 hash when appropriately responded to.

![[Pasted image 20240827003632.png]]

Overview:

![[Pasted image 20240827003740.png]]

How to do LLMNR poisoning? 

Step 1: Run Responder

```bash
sudo responder -I eth0 -dwPv
```

Here, -d is for DHCP requests. -w is for wpad rogue proxy server. -P is for forced NTLM authentication for the proxy. -v is for verbosity.

Step 2: An event occurs...

![[Pasted image 20240827004019.png]]

We then have to connect to our attacker machine.

Step 3: Get the hashes!!

![[Pasted image 20240827004045.png]]

Step 4: Crack the hashes using Tools like [[Cracking Hashes using Hashcat|Hashcat]]:

```bash
hashcat -m 5600 hashes.txt rockyou.txt
```

Where hashes.txt is your input file and rockyou.txt is the wordlist file.

Mitigation:

The best defense in this case is to disable LLMNR and NBT-NS.
1) To disable LLMNR, select "Turn OFF Multicast Name Resolution" under Local Computer Policy > Computer Configuration > Administrative Templates > Network > DNS Client in the Group Policy Editor
2) To disable NBT-NS, navigate to Network Connections > Network Adapter Properties > TCP/IPv4 Properties > Advanced Tab > WINS tab and select "Disable NetBIOS over TCP/IP".

If a company must use or cannot disable LLMNR/NBT-NS, the best course of action is to:
1) Require Network Access Control
2) Require strong user passwords(eg., >14 characters in length and limit common word usage.) The more complex and long the password, the harder it is for an attacker to crack the hash.