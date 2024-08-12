For any website there is out there, we first need to find what all subdomains that websites has. One tool you can use is called sublist3r. Its on the apt package manager for Kali Linux.

Syntax to run it for any domain is as follows:

```
sublist3r -d <domain>
```

You can also use a website called crt.sh. It does the same thing for you if you're not on linux(why?). 

Syntax:

```
%.<domain>
```

What you are doing here, is doing certificate fingerprinting.

One advantage of crt.sh is that you can find sub-subdomains of sites if there are any that sublist3r doesn't do.

You can also use OWASP Amass Project.

Link: https://github.com/owasp-amass/amass

The one problem with Amass is that it takes a lot of time to run(even longer than sublist3r) but it uncovers a lot more subdomains than crt.sh so its worth trying out. But, with that being said, Amass is the defacto tool for hunting subdomains for a lot of professionals.






