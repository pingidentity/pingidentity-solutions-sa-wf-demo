## Authentication Authorority (PingFederate) Configuration
To access the Admin UI for PF go to:  
<https://{{PF_HOSTNAME}}:9999/pingfederate>

Default Credentials:  
`Administrator` / `2FederateM0re`

This configuration includes:

### IDP Adapters
* HTML Form
* Identifier-First (Passwordless)
* Kerberos
* PingID

### Authentication Policy
Extended Property Selector
  * Basic (HTML Form --> PingID)
  * Kerberos (Kerberos --> PingID)
  * Passwordless (ID-First --> PingID)

### Extended Properties
* `Basic` (Plain HTML Form --> PingID)
* `Kerberos` (Kerberos --> PingID)
* `Passwordless` (ID-First --> PingID)

### Authentication Policy Contract
A single Policy Contract is defined with the following attributes:

* `subject`
* `ImmutableID`
* `mail`
* `givenName`
* `sn`
* `memberOf`

The Authentication Policy decision is controlled by setting the `Extended Properties` on the Application.  

### Applications
Example applications are pre-wired:

**SAML**  
*Identity Provider --> SP Connections (SAML)*  
<https://${PF_BASE_URL}/idp/startSSO.ping?PartnerSpId=Dummy-SAML>

**OAuth / OIDC**   
`Issuer` == ${PF_BASE_URL}  

*AuthZ Code \ Implicit*  
`client_id` == PingLogon  
`client_secret` == 2FederateM0re

*Client Credentials*  
`client_id` == `pingservices`  
`client_secret` == 2FederateM0re

*Introspect*  
`client_id` == PingIntrospect  
`client_secret` == 2FederateM0re