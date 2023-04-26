# Sitemap Content Planner

## Get a list of sitemap content templates

* `GET /v1/sitemaps/<sitemap_id>/content/templates`

### Response
``` json
[
    {
        "id": "w1hVhDqh",
        "name": "Text page",
        "pages": []
    },
    {
        "id": "VBp9SbVp",
        "name": "Gallery",
        "pages": [
            "svgradlb18n6oy3up9y",
            "svgl6i0xe3d3g01oyl2"
        ]
    }
]
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
id | string | Unique template ID
name | string | Template name
pages | array | Pages IDs where template is assigned

## Get a single content template details

* `GET /v1/sitemaps/<sitemap_id>/content/templates/<template_id>`

### Response
``` json
{
    "id": "w1hVhDqh",
    "name": "ALL ELEMENTS 2",
    "pages": [
        "svgkq5zepcgr4l9r9l1"
    ],
    "body": [],
    "metadatas": {
        "title": "",
        "description": "",
        "keywords": ""
    }
}
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
id | string | Unique template ID
name | string | Template name
pages | array | Pages IDs where template is assigned
body | array | Content body, please see `body` element in [`GET /v1/sitemaps/<sitemap_id>/page/<page_id>/content` endpoint](./page.md#get-a-single-page-content) for details
metadatas | array | SEO meta datas: `title`, `description`, `keywords`

## Get a list of workflow statuses

* `GET /v1/sitemaps/<sitemap_id>/content/workflow`

### Response
``` json
[
    {
        "id": "complete",
        "name": "Complete",
        "color": "#59bc6d",
        "readonly": true,
        "description": "Completed pages"
    },
    {
        "id": "draft",
        "name": "Draft",
        "color": "#f5a623",
        "readonly": false
    },
    {
        "id": "~",
        "name": "Unassigned",
        "color": "#e2e6f0"
    }
]
```

Possible other [responses](./../../sections/responses.md): `403`.

Key | Type | Description
--- | --- | ---
id | string | Unique status ID
name | string | Status name
color | string | Assigned status color in hex format
readonly | boolean | `true` if status makes pages read-only, optional
description | string | Optional status short description

## Get site settings

* `GET /v1/sitemaps/<sitemap_id>/site/settings`

### Response
``` json
{

    "title": "Site Title",
    "tagline": "Company slogan",
    "url": "https://example.com/",
    "include_parent_slug": true,
    "default_language": "en_US",
    "languages": ["en_US", "pl_PL"]
}
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
title | string | Site title
tagline | string | Site tagline
url | string | Site URL
include_parent_slug | boolean | Include parents slugs in page URL
default_language | string | Default content language
languages | array | All available content languages