### Users
If you are using the AD Configuration in this repo, the following users can be used to test with:

*Active Directory*
* `pinguser1` / `2FederateM0re`  
* `pinguser2` / `2FederateM0re`

*PingDirectory*
* `user.[0-4]` / `2FederateM0re`

**Note:**  
* AD Users should be synced into PingDirectory, with the Pass-Through Authentication plug-in used to both authenticate against AD and to synchronize passwords into PD.
* Kerberos is done directly to AD
* HTML Form \ ID-First are both using PD for their LDAP