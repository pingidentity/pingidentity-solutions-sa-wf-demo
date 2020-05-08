### **Windows Client - Integrated Authentication (Kerberos)**  
If you want to demo Kerberos:

* Point your Windows OS DNS Client to the Domain Controller IP Address
* Join the Windows client to your Domain
* Logon to the Windows Client with a Domain User
* Add your PingFed host to the Intranet Zone of IE 
  * (You can do this with Powershell -- [100-Configure-IntranetSites-in-IE.ps](ActiveDirectory/100-Configure-IntranetSites-in-IE.ps))
* If you want to use Edge -- Import the IE settings (Settings --> Import --> IE)
* Set your PF Connection --> Extended Properties to `Kerberos`
* If you see a pop-up -- you've missed a step in the configuration
* **Note:** Things look to be a little odd with untrusted certificates - you end up in a Kerb --> PingID loop, and PF doesn't pass you properly through the `resumePath`. 
   * Either trust the PF cert in the browser as an Exception, or add a proper cert to `SSL Certificates` in PingFed