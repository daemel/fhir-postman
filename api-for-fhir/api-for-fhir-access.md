# Sample Postman Environments and Collections 

## API for FHIR access


Your FHIR server URL, for example, https://MYACCOUNT.azurehealthcareapis.com

The identity provider Authority for your FHIR server, for example, https://login.microsoftonline.com/{TENANT-ID}

The configured audience that is usually the URL of the FHIR server, for example, https://<FHIR-SERVER-NAME>.azurehealthcareapis.com or https://azurehealthcareapis.com.

The client_id or application ID of the confidential client application used for accessing the FHIR service.

The client_secret or application secret of the confidential client application.



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