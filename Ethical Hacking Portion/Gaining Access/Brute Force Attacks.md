We usually do a brute-force attack for an ssh connection. We do this for 3 reasons:

1) To see the password strength of the computer
2) To see if you can log in with a weak password or even a default password
3) Or to see if the Blue Team can detect that someone has connected onto their system without them knowing.

We can use bruteforcing with either hydra or metasploit. We already covered metasploit, so we will cover hydra here. The syntax for hydra is: 

```
$ hydra -l root -P /usr/share/wordlists/metasploit/unix_passwords.txt ssh://<ip_address>:22 -t 4 -V 
```

-t basically means the speed at which we want it to run, same as nmap, -V is for verbosity.



