## Deployment Configuration

The bulk of the configuration is performed by a Postman API Collection:  
https://documenter.getpostman.com/view/1239082/SzS8tkns

**Note:** The collection has a set of default variables defined - to override them, place them in the `postman_vars.json` file.

**Collection Defaults**
| Variable | Description | Default |
| -------- | ----------- | ------- |
| `pfAdminURL` | PingFed Administration URL | https://pingfederate:9999 |
| `pdAdminUrl` | PingDir Administration URL | https://pingdirectory:443 |
| `pfAdmin` | PingFed API Admin Account | `api-admin` |
| `pfAdminPwd` | PingFed API Admin Password| {{globalPwd}} |
| `pdAdmin` | PingFed Admin Account | `cn=dmanager` |
| `pdAdminPwd` | PingDir Admin Password| {{globalPwd}} |
| `pdsAdmin` | PingDataSync Admin Account | `cn=administrator` |
| `pdsAdminPwd`  | PingDataSync Admin Password | {{globalPwd}} |
| `oauthSecret` | PingLogon Client Secret | {{globalPwd}} |
| `globalPwd` | Global Password | 2FederateM0re |

**Required - `postman_vars.json`**  
| Variable | Description | Customer Values |
| -------- | ----------- | ------- |
| `pfBaseURL` | PingFed Runtime URL | https://{{your PF public FQDN}}:9031 |
| `pingId` | PingID Properties  | Your PingID Properties file |
| `adDcHost` | AD Domain Controller | Your AD Domain Controller |
| `adBaseDN` | AD Base DN | Your AD Base DN |
| `adDsServiceAccountDN` | PingFed AD Service Account | PF Service Account Full DN |
| `adServicePwd` | PingFed AD Service Password | PF Service Account Password |
| `pingCentralHost` | PingCentral Host (CORS setting) | Your PingCentral Host |