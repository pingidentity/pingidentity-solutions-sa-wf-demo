### Active Directory
The Configuration API Collection is configured to allow you to use an existing AD environment. You will need to supply the following information in the Postman Environment:

| Variable | Description | Customer Values |
| -------- | ----------- | ------- |
| `adDcHost` | AD Domain Controller | Your AD Domain Controller |
| `adBaseDN` | AD Base DN | Your AD Base DN |
| `adDsServiceAccountDN` | PingFed AD Service Account | PF Service Account Full DN |
| `adServicePwd` | PingFed AD Service Password | PF Service Account Password |
 
If your AD is not yet configured to allow PingFederate to use Kerberos, follow the steps outlined here:
* [Configuring your AD Environment](https://docs.pingidentity.com/bundle/pingfederate-100/page/zoj1564002979045.html)

If you would like to **build** your own, you can use the Commands listed in the [ActiveDirectory](../ActiveDirectory) section of this repo.