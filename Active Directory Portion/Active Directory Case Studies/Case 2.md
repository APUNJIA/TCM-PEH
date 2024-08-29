It was in an internal network in a large US hospital. It was well funded and had invested Millions in security measures.

Defenses: LLMNR and IPv6 Disabled, SMB Signing enabled, Intrusion Detection and Prevention(IDS/IPS), and AntiVirus on all devices. Patching is also current through a solid patch management system.

During the pentest, they bounced around from login portal to login portal on website hosted locally, and was having trouble finding anything with default credentials. Eventually, they found what appeared to be a network application that was being tested out in a dev environment. The application was using default credentials and was on a free-trial license. Within this application, for whatever reason, was a cleartext credential. 

Now, they have a password. They can use a pass the password attack on the entire network and see if they get access to a machine, and they get one.

Then they can run secretsdump.py on the machine to dump any and all information about the AD.

Then from the results of the secretsdump script, they found that the Administrator had the same hash as the local admin, which means the same password. 

They then used a tool called Wdigest which then captured the domain administrator's password in cleartext.

Lessons Learnt:

1) No default creds, please
2) Turn off WDigest
3) Dont give service accounts Domain Admin Access
4) DONT REUSE YOUR PASSWORDS!

https://tcm-sec.com/pentest-tales-002-digging-deep
