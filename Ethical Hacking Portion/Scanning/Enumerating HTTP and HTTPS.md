Port 80 corresponds to HTTP and Port 443 corresponds to HTTPS. Both of these protocols are used for web-apps/websites. 

Lets say you're doing a vulnhub machine and you see an open http/https port, go to:

```
http/https://<your ip address>
```

What happens with webapps is that you can find different subdirectories within this website. This is called directory busting.

Note: If a web-service is using Apache, it should also be using PHP. Maybe a LAMP Stack.

Nikto is a web vulnerability scanner. You should be able to use this tool for solving CTFs but lets say if the security architecture of the website is good, there's a chance that it will not allow you to run nikto. You can run this tool with the following syntax:

```
$ nikto -h http://<ip address>
```

Where -h stands for host.

Next, we can start with directory busting. This can be done by a tool called dirbuster. You can also use gobuster as well. These tools should be pre-installed in your Kali machine. 

Once you open dirbuster, its going to open this interface:



We can then put our domain as:

```
http://<ip address>:80/
```

Pro tip: check the go faster checkbox

And then click on browse. The file we would be using most commonly should be in this path:

```
/usr/share/wordlists/dirbuster/directory-list-2.3-small.txt
```

In the file extension, we can add different file extensions that we might find useful. So something like php, txt, zip, etc. Just know that the more file extensions you add, the more time it will take to scan each and every thing.

Then click Start.

Fun Fact: You can also use BurpSuite to do some directory busting. 

Also, when you're working with dirbuster, you need to know the response codes. If it shows 200 that usually means its all okay, but if it shows 403, it means there's some problem