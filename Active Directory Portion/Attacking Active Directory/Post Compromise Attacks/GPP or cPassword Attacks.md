Overview:

1) Group Policy Preferences(GPP) allowed admins to create policies using embedded credentials
2) These credentials were encrypted and placed in a "cPassword"
3) The key was accidentally released(whoops) 
4) Patched in MS14-025, but it doesnt prevent previous uses
5) Still very relevant on Pentests.

![[Pasted image 20240829120327.png]]

![[Pasted image 20240829120305.png]]

Mitigation:

1) PATCH!! Fixed in KB2962486
2) In reality: delete the old GPP xml files stored in the SYSVOL