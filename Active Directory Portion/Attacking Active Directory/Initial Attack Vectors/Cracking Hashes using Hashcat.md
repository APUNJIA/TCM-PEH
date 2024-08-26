Since we know that we would be cracking an NTLM hash, we can run the following command first:

```
hashcat | grep NTLM
```

Then once we know that we want to run NTLMv2 hash, we can run the following command:

```
hashcat -m 5600 hashes.txt /usr/share/wordlists/rockyou.txt
```

Lets say you already cracked this password and it is now stored in your potfile, you can then run this command:

```
hashcat -m 5600 hashes.txt /usr/share/wordlists/rockyou.txt --show
```

This is because you dont have to crack every single password every single time.

You can use --force if your hashcat didnt work on your VM. You can also do -O for optimize.

There are also better wordlists that you can use like rockyou2021. But its like 91GB 

You can also use -r OneRule. (Look it up)