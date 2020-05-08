## Deployment Configuration

The bulk of the configuration is performed by a Postman API Collection:  
https://documenter.getpostman.com/view/1239082/SzS8tkns

**Note:** The collection has a set of default variables defined - to override them, place them in the `postman_vars.json` file.

**Collection Defaults**
| Used By | Variable | Description | Default |
| --- | --- | --- | --- |
| PingFederate | `pfAdminURL` | PingFed Administration URL | https://pingfederate:9999 |
| PingFederate | `pfAdmin` | PingFed API Admin Account | `api-admin` |
| PingFederate | `pfAdminPwd` | PingFed API Admin Password| {{globalPwd}} |
| PingDirectory | `pdAdminUrl` | PingDir Administration URL | https://pingdirectory:443 |
| PingDirectory | `pdAdmin` | PingFed Admin Account | `cn=dmanager` |
| PingDirectory | `pdAdminPwd` | PingDir Admin Password| {{globalPwd}} |
| PingDataSync | `pdsAdminURL` | PingDataSync Config API URL | `https://pingdatasync:2443` |
| PingDataSync | `pdsAdmin` | PingDataSync Admin Account | `cn=administrator` |
| PingDataSync | `adUserContainer` | AD Container for Users | `cn=Users` |
| PingDataSync | `adGroupContainer` | AD Container for Groups | `ou=Groups` |
| PingDataSync | `pdsAdminPwd`  | PingDataSync Admin Password | {{globalPwd}} |
| All | `globalPwd` | Global Password | 2FederateM0re |

**Required - `postman_vars.json`**  
| Used By | Variable | Description | Customer Values |
| --- | --- | --- | --- |
| PingFederate | `pfBaseURL` | PingFed Runtime URL | https://{{your PF public FQDN}}:9031 |
| PingFederate | `pingId` | PingID Properties  | Your PingID Properties file |
| PingFederate | `adDcHost` | AD Domain Controller | Your AD Domain Controller |
| PingFederate | `adBaseDN` | AD Base DN | Your AD Base DN |
| PingFederate | `adDsServiceAccountDN` | PingFed AD Service Account | PF Service Account Full DN |
| PingFederate | `adServicePwd` | PingFed AD Service Password | PF Service Account Password |
| PingCentral | `pingCentralHost` | PingCentral Host (CORS setting) | Your PingCentral Host |