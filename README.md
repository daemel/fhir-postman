# Sample Postman Environments and Collections 

## Overview 
A client application can access the Azure API for FHIR through a REST API. To send requests, view responses, and debug your application as it is being built, use an API testing tool of your choice. This repo provides examples and samples necessary for accessing the Azure FHIR server using [Postman](https://www.postman.com/).

A Tutorial with Postman is available on [docs.microsoft.com](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/access-fhir-postman-tutorial)


## Prerequisites
A FHIR endpoint in Azure.  To deploy the Azure API for FHIR (a managed service), you can use the [Azure portal](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/fhir-paas-portal-quickstart), [PowerShell](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/fhir-paas-powershell-quickstart), or [Azure CLI](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/fhir-paas-cli-quickstart).

A registered [confidential client application](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/register-confidential-azure-ad-client-app) to access the FHIR service.

__NOTE__ Ensure your client application has a registered reply URL of https://www.getpostman.com/oauth2/callback


You have granted permissions to the confidential client application and your user account, for example, "FHIR Data Contributor", to access the FHIR service. For more information, see [Configure Azure RBAC for FHIR](https://docs.microsoft.com/en-us/azure/healthcare-apis/azure-api-for-fhir/configure-azure-rbac).


 
## API for FHIR access




## API for FHIR access via Microsoft FHIR-Proxy 
Creating Postman collections for [Microsoft's FHIR-Proxy](https://github.com/microsoft/fhir-proxy) and its various components can be daunting when starting from nothing.  This repo provides both instructions and samples for creating Postman Environments to help Microsoft FHIR-Proxy users get started. 

These environments and collections are designed to work with and have been tested with Postman v8 (online and desktop client).


## Getting Started 
Using Postman Environments with Microsoft FHIR-Proxy requires the following configuration information mapped to Postman Environment Variables  

FHIR-Proxy Keyvault

Postman Env variable | Azure Setting          | Variable Type 
---------------------|------------------------|--------------
tenantId             | Azure AD Tenant ID     | GUID 
clientId             | Azure AD Client ID     | GUID
clientSecret         | Azure AD Client Secret | Secret 
bearerToken          | Auto-Populated         | Token
resource             | Azure AD Client ID     | GUID


testing relese