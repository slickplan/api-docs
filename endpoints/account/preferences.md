# Account Preferences

## Get all account preferences

* `GET /v1/account/preferences`
* Required scope: `account_preferences_read` or `account_preferences_write`

### Response
``` json
{
    "new_comment_nofity": true,
    "us_date_formatting": false,
    "sitemap_label_regular_case": true,
    "cells_numbering": false,
    "show_company_header": true
}
```

Key | Description
new_comment_nofity | Email notification of new comments
us_date_formatting | US date formatting (m/d/y)
sitemap_label_regular_case | Use regular case text on cells
cells_numbering | Automatically number cells
show_company_header | Show company header on shared sitemaps

Possible other [responses](./../../sections/responses.md): `403`.

## Update setting

* `PUT /v1/account/preferences`
* Required scope: `account_preferences_write`

Will update the account preferences from the parameters passed and return the JSON representation of current settings. Possible other [responses](./../../sections/responses.md): `403`.

**Note**: Only account owner and admins can edit: `sitemap_label_regular_case`, `cells_numbering` and `show_company_header`.

### Sample request
``` json
{
    "new_comment_nofity": false,
    "us_date_formatting": false,
    "sitemap_label_regular_case": true,
    "cells_numbering": true,
    "show_company_header": true
}
```