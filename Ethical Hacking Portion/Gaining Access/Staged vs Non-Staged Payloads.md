A payload is basically what we're going to run as an exploit. 

A staged payload, as the name suggests, sends the payload in stages. It is smaller in size than the non-staged payload and as a result can be less stable.

Eg: windows/meterpreter/reverse_tcp

A non-staged payload is one which sends all the exploit shellcode all at once. It is larger in size as compared to the staged payload and it doesn't always work. 

Eg: windows/meterpreter_reverse_tcp

If you look at the examples carefully, you will notice that the staged payload has its own directory called meterpreter whereas the non-staged payload does not. This is important to note when we're using a tool like metasploit.

If your current payload method fails, try the other payload style. It might just work.