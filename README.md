# Sample Postman Environments and Collections 

## Overview 
A client application can access the Azure API for FHIR through a REST API. To send requests, view responses, and debug your application as it is being built, use an API testing tool of your choice. This repo provides examples and samples necessary for accessing the Azure FHIR server using [Postman](https://www.postman.com/).

A Tutorial with Postman is available on [docs.microsoft.com](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/access-fhir-postman-tutorial)

These environments and collections are designed to work with and have been tested with Postman v8 (online and desktop client).

## Prerequisites
A FHIR endpoint in Azure.  To deploy the Azure API for FHIR (a managed service), you can use the [Azure portal](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/fhir-paas-portal-quickstart), [PowerShell](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/fhir-paas-powershell-quickstart), or [Azure CLI](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/fhir-paas-cli-quickstart).

A registered [confidential client application](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/register-confidential-azure-ad-client-app) to access the FHIR service.

__NOTE__ Ensure your client application has a registered reply URL of https://www.getpostman.com/oauth2/callback

You have granted permissions to the confidential client application and your user account, for example, "FHIR Data Contributor", to access the FHIR service. For more information, see [Configure Azure RBAC for FHIR](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/configure-azure-rbac).

## Auth - AAD and Tokens 
The FHIR service is secured by Azure AD. The default authentication can't be disabled. To access the FHIR service, you must get an Azure AD access token first. For more information, see [Microsoft identity platform access tokens](https://docs.microsoft.com/en-us/azure/active-directory/develop/access-tokens).

The POST request AuthorizeGetToken has the following:

URL: https://login.microsoftonline.com/{{tenantid}}/oauth2/token

Body tab set to x-www-form-urlencoded and key value pairs:
- grant_type: Client_Credentials
- client_id: {{clientid}}
- client_secret: {{clientsecret}}
- resource: {{fhirurl}}

Test to set the bearerToken variable
```json
var jsonData = JSON.parse(responseBody);
postman.setEnvironmentVariable("bearerToken", jsonData.access_token);
```
On clicking Send you should see a response with the Azure AD access token, which is saved to the variable accessToken automatically. You can then use it in all FHIR service API requests.

See [FHIR-CALLS](./docs/fhirCalls.md) for additional information avaliable in this Postman collection. 
 
## API for FHIR access
To access the FHIR service, we'll need to create or update the following variables.

- fhirurl – The FHIR service full URL. For example, https://xxx.azurehealthcareapis.com. It's located from the FHIR service overview menu option.
- bearerToken – The variable to store the Azure Active Directory (Azure AD) access token in the script. Leave it blank.
- FHIR server URL, for example, https://MYACCOUNT.azurehealthcareapis.com
- Identity provider Authority for your FHIR server, for example, https://login.microsoftonline.com/{TENANT-ID}
- Audience that is usually the URL of the FHIR server, for example, https://<FHIR-SERVER-NAME>.azurehealthcareapis.com or https://azurehealthcareapis.com.
- client_id or application ID of the confidential client application used for accessing the FHIR service.
- client_secret or application secret of the confidential client application.

Postman Env variable | Azure Setting          | Variable Type 
---------------------|------------------------|--------------
tenantId             | Azure AD Tenant ID     | GUID 
clientId             | Azure AD Client ID     | GUID
clientSecret         | Azure AD Client Secret | Secret 
bearerToken          | Auto-Populated         | Token
resource             | FHIR Endpoint          | URL
fhirurl              | FHIR Endpoint          | URL

## API for FHIR access via Microsoft FHIR-Proxy 
Creating Postman collections for [Microsoft's FHIR-Proxy](https://github.com/microsoft/fhir-proxy) and its various components can be daunting when starting from nothing.  The fhir-proxy directory contains a sample Postman Environment to help users get started. 

Details for 

FHIR-Proxy Keyvault

Postman Env variable | Azure Setting          | Variable Type 
---------------------|------------------------|--------------
tenantId             | Azure AD Tenant ID     | GUID 
clientId             | Azure AD Client ID     | GUID
clientSecret         | Azure AD Client Secret | Secret 
bearerToken          | Auto-Populated         | Token
resource             | Azure AD Client ID     | GUID


testing relese