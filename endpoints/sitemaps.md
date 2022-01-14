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
        "is_approved": false,
        "is_locked": false,
        "can_view": true,
        "can_edit": true,
        "can_approve": true,
        "can_lock": true,
        "can_manage": true,
        "contributors": [
            {
                "user_id": 4,
                "role": "editor"
            },
            {
                "user_id": 8,
                "role": "editor"
            }
        ],
        "versions": [
            {
                "id": 3,
                "version": "1.0",
                "uri_alias": "abcdxyz",
                "date_created": "2014-07-17T04:47:44+00:00",
                "date_modified": "2014-08-04T10:55:06+00:00"
            }
        ]
    },
    {
        "id": 2,
        "created_by": 5,
        "title": "Another sitemap",
        "is_archived": false,
        "is_approved": false,
        "is_locked": false,
        "can_view": true,
        "can_edit": true,
        "can_approve": false,
        "can_lock": false,
        "can_manage": false,
        "contributors": [],
        "versions": [
            {
                "id": 2,
                "version": "1.0",
                "uri_alias": "abcdef",
                "date_created": "2014-04-07T11:34:21+00:00",
                "date_modified": "2014-07-16T12:59:56+00:00"
            },
            {
                "id": 4,
                "version": "2.0",
                "uri_alias": "fedcba",
                "date_created": "2014-05-16T13:30:55+00:00",
                "date_modified": "2014-05-16T13:30:55+00:00"
            }
        ]
    }
]
```

Possible other [responses](./../sections/responses.md): `403`.

Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the sitemap’s first version
created_by | integer | Unique identifier of the user who created the sitemap
title | string | Sitemap title
is_archived | boolean | `true` if sitemap is archived, `false` if it is active
is_approved | boolean | `true` if sitemap is approved, `false` if it is active
is_locked | boolean | `true` if sitemap is locked, `false` if it is unlocked
can_view | boolean | *Deprecated*, always `true` for backwards compatibility
can_edit | boolean | *Deprecated*, always `true` for backwards compatibility
can_approve | boolean | `true` if current user can approve specified project, `false` if otherwise
can_lock | boolean | `true` if current user can lock specified project, `false` if otherwise
can_manage | boolean | `true` if current user can manage specified project, `false` if otherwise
contributors | string | Array of sitemap’s contributors
versions | string | Array of sitemap’s versions

#### Contributors array
Key | Type | Description
--- | --- | ---
user_id | integer | Unique identifier of the user who created the sitemap
role | string | *Deprecated*, always `editor` for backwards compatibility

#### Sitemap versions array
Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the sitemap version
version | string | Version number
uri_alias | string | A sitemap alias for sitemap preview: `https://example.slickplan.com/<alias>`
date_created | string | Sitemap creation date in Atom format
date_modified | string | Last modification date in Atom format

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
    "is_approved": false,
    "is_locked": false,
    "version": "1.0",
    "uri_alias": "abcxyz",
    "date_created": "2015-08-10T19:13:36+00:00",
    "date_modified": "2015-08-18T17:10:53+00:00",
    "can_view": true,
    "can_edit": true,
    "can_approve": true,
    "can_lock": true,
    "can_manage": true,
    "contributors": [
        {
            "user_id": 4,
            "role": "editor"
        },
        {
            "user_id": 8,
            "role": "editor"
        }
    ],
    "versions": [
        {
            "id": 3,
            "version": "1.0",
            "uri_alias": "abcxyz",
            "date_created": "2015-08-10T19:13:36+00:00",
            "date_modified": "2015-08-18T17:10:53+00:00"
        },
        {
            "id": 30,
            "version": "2.0",
            "uri_alias": "xyzabc",
            "date_created": "2015-08-18T17:11:25+00:00",
            "date_modified": "2015-08-18T17:11:50+00:00"
        },
    ]
}
```

Possible other [responses](./../sections/responses.md): `403` and `404`.

## Create a new sitemap

* `POST /v1/sitemaps`
* Required scope: `sitemaps_write`

### Request
``` json
{
    "title": "New sitemap",
    "version": "1.0",
    "contributors": [
        {
            "user_id": 4
        }
    ]
}
```

This will return `201 Created` with the current JSON representation of the sitemap if the creation was successful. Current user will always be added as a contributor with `manage` permission. Possible other [responses](./../sections/responses.md): `400` and `403`.

## Update a sitemap

* `PUT /v1/sitemaps/3`
* Required scope: `sitemaps_write`

Will update the sitemap from the parameters passed and return the JSON representation of the updated sitemap. Possible other [responses](./../sections/responses.md): `400`, `403` and `404`.

### Sample request
``` json
{
    "title": "New sitemap name",
    "contributors": [
        {
            "user_id": 4
        }
    ]
}
```

## Delete a sitemap

* `DELETE /v1/sitemaps/3`
* Required scope: `sitemaps_write`

Will delete the specified sitemap and return `204 No Content` if that was successful. Possible other [responses](./../sections/responses.md): `403` and `404`.