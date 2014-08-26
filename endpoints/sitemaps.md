# Sitemaps

## Get list of sitemaps

* `GET /v1/sitemaps`
* Required scope: `sitemaps_read` or `sitemaps_write`

### Response
``` json
[
    {
        "id": 3,
        "created_by": 5,
        "title": "My Sitemap",
        "is_archived": false,
        "contributors": [
            {
                "user_id": 4,
                "role": "editor"
            },
            {
                "user_id": 8,
                "role": "viewer"
            }
        ],
        "versions": [
            {
                "id": 3,
                "version": 1,
                "uri_alias": "abcxyz",
                "date_created": "2014-07-17T04:47:44-04:00",
                "date_modified": "2014-08-04T10:55:06-04:00"
            }
        ]
    },
    {
        "id": 2,
        "created_by": 5,
        "title": "Another sitemap",
        "is_archived": true,
        "contributors": [],
        "versions": [
            {
                "id": 2,
                "version": 1,
                "uri_alias": "abcdef",
                "date_created": "2014-04-07T11:34:21-04:00",
                "date_modified": "2014-07-16T12:59:56-04:00"
            },
            {
                "id": 4,
                "version": 2,
                "uri_alias": "fedcba",
                "date_created": "2014-05-16T13:30:55-04:00",
                "date_modified": "2014-05-16T13:30:55-04:00"
            }
        ]
    }
]
```
Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the sitemap's first version.
created_by | integer | Unique identifier of the user who created the sitemap.
title | string | Sitemap title.
is_archived | boolean | `true` if sitemap is archived, `false` if it is active.
contributors | string | Array of sitemap's contributors.
versions | string | Array of sitemap's versions.

#### Contributors array
Key | Type | Description
--- | --- | ---
user_id | integer | Unique identifier of the user who created the sitemap.
role | string | `editor` or `viewer`.

#### Sitemap versions array
Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the sitemap version.
version | integer/float | Version name.
uri_alias | string | A sitemap alias for sitemap preview: `http://slickplan.com/<alias>`
date_created | string | Sitemap creation date in ISO 8601 format.
date_modified | string | Last modification date in ISO 8601 format.

## Get the specified sitemap

* `GET /v1/sitemaps/3`
* Required scope: `sitemaps_read` or `sitemaps_write`

### Response
``` json
{
    "id": 3,
    "created_by": 5,
    "title": "My Sitemap",
    "is_archived": false,
    "contributors": [
        {
            "user_id": 4,
            "role": "editor"
        },
        {
            "user_id": 8,
            "role": "viewer"
        }
    ],
    "version": 1,
    "uri_alias": "abcxyz",
    "date_created": "2014-07-17T04:47:44-04:00",
    "date_modified": "2014-08-04T10:55:06-04:00"
}
```

## Create a new sitemap

* `POST /v1/sitemaps`
* Required scope: `sitemaps_write`

### Request
``` json
{
    "title": "New sitemap",
    "contributors": [
        {
            "user_id": 4,
            "role": "viewer"
        }
    ]
}
```

This will return `201 Created` with the current JSON representation of the sitemap if the creation was successful. If the user does not have access to create a sitemap you'll see `403 Forbidden`. Validations messages return with `400` HTTP code.

## Update a sitemap

* `PUT /v1/sitemap/3`
* Required scope: `sitemaps_write`

Will update the sitemap from the parameters passed and return the JSON representation of the updated sitemap. If the user does not have access to update the sitemap you'll see `403 Forbidden`. Validations messages return with `400` HTTP code.

### Sample request
``` json
{
    "title": "New sitemap name",
    "contributors": [
        {
            "user_id": 4,
            "role": "viewer"
        }
    ]
}
```

## Delete a sitemap

* `DELETE /v1/sitemap/3`
* Required scope: `sitemaps_write`

Will delete the specified sitemap and return `204 No Content` if that was successful. If the user does not have access to delete the sitemap you'll see `403 Forbidden`.