## PingCentral
To access the Admin UI for PC go to:  
<https://{{PF_HOSTNAME}}:9022>

PingCentral is configured to use OIDC (from PingFederate) for authentication for both Admins and Application Owners. 

Access Control is managed using claims in an OIDC Policy that is mapping LDAP `employeeType` --> OIDC `PingCentral-Role` (This claim is defined in the `application.properties` file):

| PingCentral Role | Claim Value |
| --- | --- |
| Administrator | `IAM-Admin` |
| Application Owner | `AppOwner` |

### Reference Users (PingDirectory)

**Administrator**
* `administrator` / `2FederateM0re`

**Application Owner**
* `appowner.0` / `2FederateM0re`
* `appowner.1` / `2FederateM0re`

### Post-Deployment
PingCentral will stand up connected to a PF OIDC provider, but not configured for any Environments.

Follow the `Add Environment` wizard to connect to a PingFederate instance.

* PingFederate Admin -- `pingfederate:9999`
* PingFederate Admin User -- `api-admin`
* PingFederate Admin Pwd -- `2FederateMore`

The pre-configured applications will be presented and can be used to create Application templates.