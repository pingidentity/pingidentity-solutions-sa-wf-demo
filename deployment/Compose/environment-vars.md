Ping Docker Images allow values to be injected as the containers start up - allowing you to adapt the container configuration to the specifics of your environment.

In the `docker-compose.yaml` file, these are imported via the `env_vars` file.

**`env_vars`**
| Product | Variable | Description | Customer Values |
| --- | --- | --- | --- |
| All | `PING_IDENTITY_ACCEPT_EULA` | Ping Identity EULA | YES |
| PingFederate | `PF_LOG_LEVEL` | PingFed Logging Level | INFO or DEBUG |
| PingDirectory | `USER_BASE_DN` | Root of the LDAP tree | dc=example.com |
| PingFederate | `PF_USER_PWD` | Password for PF Service Account (LDAP) | `pfAdminPwd` |
| PingFederate | `AD_DC_HOST` | Domain Controller | {{Your Domain Controller}} |
| PingFederate | `AD_BASE_DN` | Your AD Base DN | dc=example.dc=com |
| PingCentral | `PING_CENTRAL_BLIND_TRUST` | Allow Blind Trust | `true` / `false` |
| PingCentral | `PING_CENTRAL_VERIFY_HOSTNAME` | Verify SSL Hostname | `true` / `false` |
| PingCentral | `MYSQL_USER` | PingCentral MySQL User | `root` |
| PingCentral | `MYSQL_PASSWORD` | PingCentral MySQL Password| `2Federate` |
| PingCentral | `PING_CENTRAL_OIDC_ENABLED` | PingCentral OIDC AuthN | `true` / `false` |
| PingCentral | `PING_CENTRAL_CLIENT_ID` | PingCentral OIDC Client | PingCentral |
| PingCentral | `PING_CENTRAL_CLIENT_SECRET` | PingCentral OIDC Client Secret | 2FederateM0re |
| PingCentral | `PF_ISSUER` | PingFed OIDC Issuer | {{Your PF Issuer}} |

**Sample `env_vars` file**

```
# Acceptance of the Ping EULA
PING_IDENTITY_ACCEPT_EULA=YES

# PF Logging Level
PF_LOG_LEVEL=DEBUG

# Password Used to bind to PingDirectory in ldap.properties
PF_USER_PWD=2FederateM0re

# PD Variables
USER_BASE_DN=dc=workforce360.com

# AD Variables
# Used in the PF AD Datastore \ PCV && PingDataSync
AD_DC_HOST=int-ad.solution-wf.ping-eng.com
AD_BASE_DN=dc=workforce360,dc=com

# PingCentral Variables
# These values are placed into the `application.properties` file
PING_CENTRAL_BLIND_TRUST=true
PING_CENTRAL_VERIFY_HOSTNAME=false
MYSQL_USER=root
MYSQL_PASSWORD=2Federate
MYSQL_ROOT_PASSWORD=2Federate
PING_CENTRAL_OIDC_ENABLED=true
PING_CENTRAL_CLIENT_ID=PingCentral
PING_CENTRAL_CLIENT_SECRET=2FederateM0re
PF_ISSUER=https://docker.workforce360.com:9031
```