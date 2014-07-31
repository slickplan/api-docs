# Company Settings

## Get all settings

* `GET /v1/account/company`
* Required scope: `company_settings_read` or `company_settings_write`

### Response
``` json
{
    "company_name": "Slickplan Company",
    "company_name_2": "Flowchart Software",
    "subdomain": "slickplan",
    "site_color": "#008DF5",
    "use_dark_font": false
}
```
Key | Type | Description
--- | --- | ---
company_name | string | Company name.
company_name_2 | string | Company name, second line.
subdomain | string | Account's subdomain (<subdomain>.slickplan.com).
site_color | string | Account branding color in HEX format or `false` if no account branding is available for current user's plan.
use_dark_font | string | Account branding font color - `true` for dark gray, `false` for white.

## Update setting

* `PUT /v1/account/company` or `POST /v1/account/company`
* Required scope: `company_settings_write`

Will update the company settings from the parameters passed and return the JSON representation of the settings. If the user does not have access to update company settings you'll see `403 Forbidden`. Validations messages return with `400` HTTP code.
 
### Sample request
``` json
{
    "company_name": "Another Company",
    "company_name_2": "Our new slogan",
    "subdomain": "slickplan2",
    "site_color": "#FF3366",
    "use_dark_font": true
}