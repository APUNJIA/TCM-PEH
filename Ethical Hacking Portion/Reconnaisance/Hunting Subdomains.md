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

Once you've downloaded amass, you can enumerate subdomains using the following command:

```bash
amass -enum -d <website>
```

We used to find subdomains with a tool called sublister but assetfinder is somewhat better at doing this and sublist3r is kinda old.

So we can look at the subdomain of any website using this syntax:

```bash
assetfinder <website>
```

Now this tool is exteremely fast and also gives out websites that are affiliated with the website given as an argument which are not necessarily subdomains. So, you can filter them out using:

```bash
assetfinder --subs-only <website>
```

One thing about amass is that, you have to sort the results that you get after running this. You can do this by saving the initial results into a file and then sort them like so:

```bash
assetfinder --subs-only <website> >> report.txt
sort -u report.txt
```

You can then run a script like so which can give you results from assetfinder, put it in a separate directory and removes all the affiliates and only has subdomains listed.

```bash
#!/bin/bash

url=$1

if [ ! -d "$url" ]; then
	mkdir $url
fi

if [ ! -d "$url/recon" ]; then 
	mkdir $url/recon
fi

echo "[+] Harvesting subdomains with assetfinder..."
assetfinder $url >> $url/recon/assets.txt
cat $url/recon/assets.txt | grep $1 >> $url/recon/final.txt
rm $url/recon/assets.txt
```

Once we have enumerated the website for subdomains, we can use a tool like httprobe to see what all domains are alive.

If we take the same script for assetfinder above, which saves the file with all the subdomains at $url/recon/final.txt, we can run httprobe on this file using the following command:

```bash
cat $url/recon/final.txt | httprobe -s -p https:443
```

-s removes all the default ports and we are looking specifically for https which is on port 443. For that, we add -p

Then we can automate this entire thing by updating the assetfinder script to the following script:

```bash
#!/bin/bash

url=$1

if [ ! -d "$url" ]; then
	mkdir $url
fi

if [ ! -d "$url/recon" ]; then 
	mkdir $url/recon
fi

echo "[+] Harvesting subdomains with assetfinder..."
assetfinder $url >> $url/recon/assets.txt
cat $url/recon/assets.txt | grep $1 >> $url/recon/final.txt
rm $url/recon/assets.txt

echo "[+] Probing for alive domains..."
cat $url/recon/final.txt | sort -u | httprobe -s -p 443 | sed 's/https\?:\/\///' | tr -d ':443' >> $url/recon/alive.txt
```

We can then look at the alive subdomains of a website and take screenshots of those websites using a tool called gowitness.

Before downloading gowitness from github, you have to install this patch which will take care of the dependancies while downloading gowitness:

```bash
go get -u gorm.io/gorm
```

Then you can run the command which takes a single screenshot of a website you ask it to.

```bash 
gowitness single https://<website>
```

It will then save the screenshot in your screenshots folder.

The best part about this is, we can actually automate this entire thing using a bash script. 

https://github.com/thatonetester/sumrecon

You can also use this modified script by TCM himself:

https://pastebin.com/MhE6zXVt

Youtube Videos for more resources:

The Bug Hunter's Methodology:
https://www.youtube.com/watch?v=uKWu6yhnhbQ

Nahamsec Recon Playlist:
https://www.youtube.com/watch?v=MIujSpuDtFY&list=PLKAaMVNxvLmAkqBkzFaOxqs3L66z2n8LA