# Sitemap Page Types

## Get all page types

* `GET /v1/sitemaps/archetypes`
* Required scope: `sitemaps_read` or `sitemaps_page_types_read` or `sitemaps_page_types_write`

### Response
``` json
[
    {
        "id": "_form",
        "name": "Form",
        "icon": ""
    },
    {
        "id": "_listing",
        "name": "Listing",
        "icon": ""
    },
    {
        "id": "_portal",
        "name": "Portal",
        "icon": ""
    },
    {
        "id": "_consumption",
        "name": "Consumption",
        "icon": ""
    },
    {
        "id": "_consumptionstack",
        "name": "Consumption Stack",
        "icon": ""
    },
    {
        "id": "_gallery",
        "name": "Gallery",
        "icon": ""
    },
    {
        "id": "_dialog",
        "name": "Dialog",
        "icon": ""
    },
    {
        "id": "_process",
        "name": "Process",
        "icon": ""
    },
    {
        "id": "_interactive",
        "name": "Interactive",
        "icon": ""
    },
    {
        "id": "_file",
        "name": "File",
        "icon": ""
    },
    {
        "id": "_fragment",
        "name": "Fragment",
        "icon": ""
    },
    {
        "id": "_external",
        "name": "External",
        "icon": ""
    },
    {
        "id": "nrjnfxutxwpitsv",
        "name": "Deleted",
        "icon": "fa-ban"
    },
    {
        "id": "zfazcrkdhsvna",
        "name": "Custom page type",
        "icon": ""
    }
]
```
Key | Type | Description
--- | --- | ---
id | integer | Page type id, read-only are prefixed with `_`.
name | string | Page type name.
icon | string | Page type icon - default one if empty or [FontAwesome 4.1.0](http://fortawesome.github.io/Font-Awesome/) class name.

## Get single page type

* `GET /v1/sitemaps/archetypes/<key>` (ex. `GET /v1/sitemaps/archetypes/_external`)
* Required scope: `sitemaps_read` or `sitemaps_page_types_read` or `sitemaps_page_types_write`

### Response
``` json
{
    "id": "_external",
    "name": "External",
    "icon": ""
}
```

## Create new page type

* `POST /v1/sitemaps/archetypes`
* Required scope: `sitemaps_page_types_write`

Will create a new custom page type from the parameters passed and return the JSON representation of the created custom page type. If the user does not have access to create page type you'll see `403 Forbidden`. Validations messages return with `400` HTTP code.

### Sample request
``` json
{
    "name": "My page type",
    "icon": "fa-database"
}
```

## Update page type

* `PUT /v1/sitemaps/archetypes/<key>` (ex. `PUT /v1/sitemaps/archetypes/nrjnfxutxwpitsv`)
* Required scope: `sitemaps_page_types_write`

Will update the custom page type from the parameters passed and return the JSON representation of the custom page type. If the user does not have access to update page type you'll see `403 Forbidden`. Validations messages return with `400` HTTP code.

Only custom page types can be edited, read-only page types IDs are prefixed with `_`.

### Sample request
``` json
{
    "name": "New page type name",
    "icon": ""
}
```