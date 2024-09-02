What if IPv6 is not possible in the network and we do end up compromising the account? This is where ldapdomaindump comes in. It comes pre-installed in kali.

First we start by making a directory and cd-ing into it

```bash
mkdir marvel.local
cd marvel.local
```

run ldapdomaindump as admin

```bash
sudo ldapdomaindump ldaps://<ip_address> -u '<DC>\<username>' -p <Password>
```

and then it gives you the output like you got in an IPv6 relay attack using mitm6.

