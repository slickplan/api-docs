# Account Preferences

## Get all account preferences

* `GET /v1/account/preferences`
* Required scope: `account_preferences_read` or `account_preferences_write`

### Response
``` json
{
    "us_date_formatting": true,
    "sitemap_label_regular_case": true,
    "cells_numbering": true,
    "show_company_header": true,
    "sitemap_cell_default_font_size": "16px",
    "sitemap_cell_default_box_size": "small",
    "always_show_support_chat": false,
    "new_comment_nofity": false,
    "email_notify_content_assigned": true,
    "email_notify_content_unassigned": true,
    "email_notify_content_due_date_updated": false,
    "email_notify_content_status_updated": true,
    "email_invoices": false
}
```

Key | Description
--- | ---
us_date_formatting | US date formatting (m/d/y)
sitemap_label_regular_case | Use regular case text on cells
cells_numbering | Automatically number cells in sitemaps
show_company_header | Show company header on shared sitemaps
sitemap_cell_default_font_size | Default sitemap cell font size, one of: `12px`, `14px`, `16px`
sitemap_cell_default_box_size | Default sitemap cell box size, one of: `small`, `medium`, `large`
always_show_support_chat | `true` to show Slickplan Support chat icon on the lower-right side of the page, `false` otherwise
new_comment_nofity | Email notification of new comments
email_notify_content_assigned | Email notification of content assignement
email_notify_content_unassigned | Email notification of content unassigned
email_notify_content_due_date_updated | Email notification after content due date update
email_notify_content_status_updated | Email notification of content status update
email_invoices | Send invoices via email

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
    "email_invoices": false,
    "us_date_formatting": false,
    "sitemap_label_regular_case": true,
    "cells_numbering": true,
    "sitemap_cell_default_font_size": "12px"
}
```