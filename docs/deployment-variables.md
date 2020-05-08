## Deployment Configuration

The bulk of the configuration is performed by a Postman API Collection:  
https://documenter.getpostman.com/view/1239082/SzS8tkns

**Note:** The collection has a set of default variables defined - to override them, place them in the `postman_vars.json` file.

**Collection Defaults**
| Used By | Variable | Description | Default |
| --- | --- | --- | --- |
| PingFederate | `pfAdminURL` | PingFed Administration URL | `https://pingfederate:9999` |
| PingFederate | `pfAdmin` | PingFed API Admin Account | `api-admin` |
| PingFederate | `pfAdminPwd` | PingFed API Admin Password| {{globalPwd}} |
| PingDirectory | `pdAdminUrl` | PingDir Administration URL | `https://pingdirectory:443` |
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

**Sample `postman_vars.json` file**
```
{
	"id": "40199d03-d15c-47e4-b502-8b62f98479d1",
	"name": "Solution-Workforce360",
	"values": [
		{
			"key": "pfBaseURL",
			"value": "https://docker.workforce360.com:9031",
			"enabled": true
		},
		{
			"key": "pingId",
			"value": "#Auto-Generated from PingOne, downloaded by id=[000000] email=[admin0@workforce360.com]\n#Thu May 07 17:31:22 MDT 2020\nuse_base64_key=YourBase64Key=\nuse_signature=true\ntoken=YourToken\nidp_url=https://idpxnyl3m.pingidentity.com/pingid\norg_alias=YourOrgAlias\nadmin_url=https://idpxnyl3m.pingidentity.com/pingid\nauthenticator_url=https://authenticator.pingone.com/pingid/ppm",
			"enabled": true
		},
		{
			"key": "adDcHost",
			"value": "int-ad.solution-wf.ping-eng.com",
			"enabled": true
		},
		{
			"key": "adBaseDN",
			"value": "dc=workforce360,dc=com",
			"enabled": true
		},
		{
			"key": "adServiceAccountDN",
			"value": "cn=PingFederate,ou=ServiceAccounts,dc=workforce360,dc=com",
			"enabled": true
		},
		{
			"key": "adServicePwd",
			"value": "P@ssword99",
			"enabled": true
		},
		{
			"key": "adUserContainer",
			"value": "cn=Users",
			"enabled": true
		},
		{
			"key": "adGroupContainer",
			"value": "ou=Groups",
			"enabled": true
		},
		{
			"key": "pingCentralHost",
			"value": "https://docker.workforce360.com",
			"enabled": true
		}
	],
	"_postman_variable_scope": "environment",
	"_postman_exported_at": "2020-02-24T18:49:30.401Z",
	"_postman_exported_using": "Postman/7.18.1"
}
```