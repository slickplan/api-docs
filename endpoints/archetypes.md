# Sitemap Page Types

## Get all page types

* `GET /v1/archetypes`
* Required scope: `sitemaps_read` or `sitemaps_page_types_read` or `sitemaps_page_types_write`

### Response
``` json
[
    {
        "id": "_form",
        "name": "Form",
        "icon": "",
        "description": "(...)"
    },
    {
        "id": "_listing",
        "name": "Listing",
        "icon": "",
        "description": "(...)"
    },
    {
        "id": "nrjnfxutxwpitsv",
        "name": "Deleted",
        "icon": "fa-ban",
        "description": ""
    },
    {
        "id": "zfazcrkdhsvna",
        "name": "Custom page type",
        "icon": "C",
        "description": "(...)"
    }
]
```

Possible other [responses](./../sections/responses.md): `403`.

Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the page type, read-only are prefixed with `_`
name | string | Page type name
icon | string | Page type icon - a single letter or [FontAwesome 4.7](https://fontawesome.com/v4.7.0/icons/) CSS class name
description | string | Page type description

## Get single page type

* `GET /v1/archetypes/<id>` (ex. `GET /v1/archetypes/_external`)
* Required scope: `sitemaps_read` or `sitemaps_page_types_read` or `sitemaps_page_types_write`

### Response
``` json
{
    "id": "_external",
    "name": "External",
    "icon": "",
    "description": "(...)"
}
```

Possible other [responses](./../sections/responses.md): `403` and `404`.

## Create new page type

* `POST /v1/archetypes`
* Required scope: `sitemaps_page_types_write`

Will create a new custom page type from the parameters passed and return the JSON representation of the created custom page type. Possible other [responses](./../sections/responses.md): `400`, `403`.

### Sample request
``` json
{
    "name": "My page type",
    "icon": "fa-database",
    "description": "This is my custom page type with FontAwesome icon"
}
```

## Update page type

* `PUT /v1/archetypes/<id>` (ex. `PUT /v1/archetypes/nrjnfxutxwpitsv`)
* Required scope: `sitemaps_page_types_write`

Will update the custom page type from the parameters passed and return the JSON representation of the custom page type. Possible other [responses](./../sections/responses.md): `400`, `403` and `404`.

Only custom page types can be edited, read-only page types IDs are prefixed with `_`.

### Sample request
``` json
{
    "name": "New page type name"
}
```

## Delete page type

* `DELETE /v1/archetypes/<id>`
* Required scope: `sitemaps_page_types_write`

Will delete the specified page type and return `204 No Content` if that was successful. Possible other [responses](./../sections/responses.md): `403` and `404`.