It is also a sort of relay attack but is much more reliable as it uses IPv6

So, when we have a machine, we usually use IPv4. Chances are, the network doesnt even use IPv6. So the question arises, if we are using IPv4 and IPv6 is turned on, who is doing DNS for IPv6? Its usually nobody

So a hacker machine will listen to all the IPv6 messages and tell the machine that it is the DNS. So the machine will send all of the IPv6 traffic to the hacker.

The problem with this is, we can get authentication to the domain controller via LDAP or SMB. So when the user gives his credentials somewhere, it comes back to us with NTLM just like SMB relay and then we relay this using LDAP relay to the Domain Controller

All of this can be done with a tool called MITM6(man in the Middle 6)

It should be installed by default in your Kali machine but if not, you can install it by going to /opt/mitm6 and running this command

```bash
sudo pip2 install .
```

Once mitm6 is downloaded, you can run it by: (but we wont run it yet, we first have to set up an ntlm relay) 

```bash
sudo mitm6 -d <domain_name>
```

To set up an NTLM relay with this method, you can use th following command:

```bash
ntlmrealyx.py -6 -t ldaps:/<ip_of_domain_controller> -wh fakewpad.marvel -l lootme
```

-6 is for IPv6 and -t is for target, -wh is going to be for our wpad and -l is for loop

First you run the ntlm relay and then you run mitm6

Note: dont just run mitm and walk away, because it may cause a network outage. You should technically run it for only 5-10 mins.

Once an event occurs on your AD, there will be a folder called lootme(refer the command) in our home folder which contains all the information for the active directory

One other thing that can happen is that if a person logs in to one of this active directory, it creates an account and a password which then we can use to access it as well.

Mitigation:

1) IPv6 poisoning abuses the fact that Windows queries for an IPv6 address even in IPv4-only environments. If you do not use IPv6 internally, the safest way to prevent mitm6 is to block DHCPv6 traffic and incoming router advertisements in Windows Firewall via Group Policy. Disabling IPv6 entirely may have unwanted side effects. Setting the following predefined rules to Block instead of Allow prevents the attack from working:
	1) (Inbound) Core Networking- Dynamic Host Configuration Protocol for IPv6(DHCPv6-In).
	2) (Inbound) Core Networking- Router Advertisement(ICMPv6-In).
	3) (Outbound) Core Networking- Dynamic Host Configuration Protocol for IPv6(DHCPv6-Out).
2) If WPAD is not in use internally, disable it via Group Policy and by disabling the WinHttpAutoProxySvc Service.
3) Relaying to LDAP can only be mitigated by enabling both LDAP signing and LDAP channel binding.
4) Consider Administrative users to the Protected Users group or marking them as Account is sensitive and cannot be delegated, which will prevent any impersonation of that user via delegation.