## Post-Deployment Steps
It's not possible to fully automate the implementation of this Solution. There are additional steps needed to be performed manually after things are running:

---
### Active Directory
This Profile is configured to use an Active Directory instance that has been pre-built and hosted Ping's Scalr \ AWS environment.  

If you'd like to use your own AD Forest, you will need to change the `Datastore` and `Password Credential Validator` to reflect your information.  

If you would like to **build** your own, you can use the Commands listed in the [ActiveDirectory](../ActiveDirectory) section of this repo. 

---
### PingOne for Enterprise
In order to connect this PF instance to PingOne for Enterprise, you will need a P14E tenant. This process is somewhat automated through a Wizard, but cannot be automated in this Solution Profile.

In PF, go to `System --> Connect to PingOne for Enterprise` and select the `Sign on to PingOne to get your activation key` link (https://admin.pingone.com/web-portal/cas/config/idpng/pingFedActivate).  

Logon to PingOne for Enterprise and copy the Activation Key that should be presented. This key should be pasted into PF to begin the integration process.

**Notes:**
* When prompted to for a Directory Server, Select `Yes` and press the `Begin` button to connect the one that is created as part of this Solution
* Uncheck the `Outbound Provisioning` checkbox if you don't want to configure this.
* For the Extended Properties -- type `Basic` or `Passwordless` (depending on what journey you want a User Authentication to take)
* Use the `Default Policy Contract` to Map values into the Connection

---
### Enable LDAPS to PingDirectory
This Solution leverages **unsecured** LDAP between PingFederate and PingDirectory as it launches.  

To enabled LDAPS, follow these steps:

**Command Line**
1. Export the PingDirectory certificate
* Compose -- 
  * `docker-compose exec pingdirectory /opt/out/instance/bin/manage-certificates export-certificate --keystore /opt/out/instance/config/keystore --keystore-password-file /opt/out/instance/config/keystore.pin --alias server-cert --output-file server-cert.crt --output-format PEM`
* Kubernetes -- 
  * Connect to the Service -- `kubectl exec -it service/pingdirectory /bin/sh`
  * Execute this command -- `/opt/out/instance/bin/manage-certificates export-certificate --keystore /opt/out/instance/config/keystore --keystore-password-file /opt/out/instance/config/keystore.pin --alias server-cert --output-file server-cert.crt --output-format PEM`
1. Copy the certificate from the PingDirectory container
* Compose --
  * Get the Container names -- `docker container ls` - retrieve the Container IDs for PingDirectory and PingFederate
  * `docker cp {{pingdirectoryId}}:/opt/server-cert.crt ./server-cert.crt`
* Kubernetes -- 
  * Get the Container names -- `kubectl get pods` - retrieve the Container IDs for PingDirectory and PingFederate
  * `kubectl cp {{pingdirectoryId}}:/opt/server-cert.crt ./server-cert.crt`
  
**PingFederate Admin Console**
1. Import the PingDirectory certificate into PingFederate
* Open the Trusted CA store
  * `Security` --> `Trusted CAs`
* Import the `server-cert.crt` file

1. Edit the PingDirectory DataStore
* `System` --> `External Systems -- DataStores` --> `PingDirectory` --> `LDAP Configuration`
* Check the `Use LDAPS` box
* Test the Connection

**Disable LDAP on PingDirectory**
* Compose -- 
  * `docker-compose exec pingdirectory /opt/out/instance/bin/dsconfig set-connection-handler-prop --handler-name "LDAP Connection Handler" --set enabled:false --no-prompt`
* Kubernetes -- 
  * `kubectl exec service/pingdirectory /opt/out/instance/bin/dsconfig set-connection-handler-prop --handler-name "LDAP Connection Handler" --set enabled:false --no-prompt`