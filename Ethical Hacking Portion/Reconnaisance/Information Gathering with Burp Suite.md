How to setup BurpSuite on your Kali Machine:

1) Open BurpSuite(it should be pre installed on Kali)

![[Pasted image 20240811220004.png]]

2) Go on FireFox and open settings > network settings > configure how firefox connects to the internet 

![[Pasted image 20240811220054.png]]

3) Manual Proxy Configuration. Put HTTP Proxy to 127.0.0.1 and port to 8080. Tick the check-box to use this proxy for HTTPS as well.

![[Pasted image 20240811220119.png]]

4) New tab, go to https://burp and hit accept to go to the burpsuite page and click CA Certificate. It should download a certificate file. 

![[Pasted image 20240811220155.png]]

5) Now go to settings > privacy and security > certificates > view certificates. And then import your recently downloaded certificate. Once done, it will show you 2 checkboxes, check both of them and click done. 

![[Pasted image 20240811220241.png]]

![[Pasted image 20240811220321.png]]

6) Boom, done!

If you don't like this method of setup, you can use a tool called FoxyProxy.

How to setup FoxyProxy with BurpSuite:

1) Google FoxyProxy and go to firefox addons and install the FoxyProxy extension.
2) Open the extension and go to options > add. Name it BurpSuite, proxy type HTTP, proxy IP Address 127.0.0.1, port 8080, and hit save.
3) Then go to FoxyProxy again and turn the proxy on and now you have BurpSuite connected.