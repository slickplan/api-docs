# Company Settings

## Get all settings

* `GET /v1/account/company`

### Response
``` json
{
    "company_name": "Slickplan Company",
    "company_name_2": "Flowchart Software",
    "subdomain": "example",
    "site_color": "#008DF5",
    "use_dark_font": false,
    "billing_address": ""
}
```

Possible other [responses](./../../sections/responses.md): `403`.

Key | Type | Description
--- | --- | ---
company_name | string | Company name
company_name_2 | string | Company name, second line
subdomain | string | Account’s subdomain (`<subdomain>`.slickplan.com)
site_color | string | Account branding color in HEX format or `false` if no account branding is available for current user’s plan
use_dark_font | string | Account branding font color - `true` for dark gray, `false` for white
billing_address | string | Billing address for invoices (available only if a user has „Allow changing payment settings” permission) 

## Update setting

* `PUT /v1/account/company`
* Requires "write" scope

Will update the company settings from the parameters passed and return the JSON representation of the current settings. Possible other [responses](./../../sections/responses.md): `400` and `403`.

### Sample request
``` json
{
    "company_name": "Another Company",
    "company_name_2": "Our new slogan",
    "subdomain": "example2",
    "site_color": "#FF3366",
    "use_dark_font": true,
    "billing_address": "PO Box 123"
}
```
