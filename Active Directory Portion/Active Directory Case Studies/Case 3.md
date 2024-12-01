This one was different. This company was doing a lot of things right they had llmnr enabled, they were cracking passwords left and right but they weren't getting anywhere. This is because they were running Lapse, this tool created unique local admin password for every user account

Then they kept digging and digging and eventually, they didn't get access to a domain admin, but they got access to the fileshares and the fileshares were everyone's file shares. This also showed all the different users who were a part of the Active Directory, so naturally, they started to look for the domain admins.

Here, they found a Macbook Pro Setup Procedure and a PC setup Procedure. After looking at the Macbook Setup Procedure, they found a user called 'admin' with a password in cleartext(Jesus Christ). Then they passed the password and one machine got cracked. 

Then they ran secretsdump on the machine and they found a cleartext password in the secretsdump.

Lessons Learnt:

*Enumerate, Enumerate, Enumerate*