This attack takes advantage of service accounts. What happens:

![[Pasted image 20240829094549.png]]

For more info about kerberoasting, you can use this blogpost:

https://medium.com/@Shorty420/kerberoasting-9108477279cc

This can be done with a script called GetUserSPNs.py

To run it, use the following command:

```bash
sudo GetUserSPNs.py <DC>/<user>:<Password> -dc-ip <IP_Address> -request
```

At the end, it will spit out a hash, we will save that hash into krb.txt

Then use hashcat to crack the hash

Mitigation:

1) Strong Passwords
2) Least Privilege

![[Pasted image 20240829095842.png]]
