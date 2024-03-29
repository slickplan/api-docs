# Sitemap page details

See how to get a sitemap's pages list on the [structure endpoint](./structure.md). **Note:** it’s not possible to fetch archived sitemaps, you will get `HTTP 403 Sitemap archived` response.

## Get a single page details

* `GET /v1/sitemaps/<sitemap_id>/page/<page_id>`

### Response
``` json
{
    "id": "svgz1wxw28i5deh25tt",
    "level": 1,
    "text": "Level 1 page",
    "order": 1000,
    "color": "#57aa34",
    "archetype": "exrrliyswugymjz",
    "url": [
        {
            "type": "external",
            "label": "Link to Slickplan",
            "url": "https:\/\/slickplan.com\/"
        },
        {
            "type": "internal",
            "page": "svga5c8wc1b9t2dwppi"
        }
    ],
    "section": "svgnq3nac4e1dzr8z0l",
    "diagrams": false,
    "has_files": false,
    "has_mockups": false,
    "has_content": { "en_US": true, "pl_PL": false }
}
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
id | string | Sitemap unique page ID
level | string/integer | Page level: `home`, `util`, `foot` or an integer
text | string | Page label
order | integer | Page level order, to use with `ORDER BY`
color | string | Page background color
textcolor | string | Page text color
archetype | string | Page type ID
parent | string | Parent page ID
desc | string | Page note
url | array | Array of page's links
section | string | Page's subsection ID
diagrams | array/boolean | Array of diagrams ids or `false` if page has no diagrams
has_files | array/boolean | Array of files ids or `false` if page has no files attached
has_mockups | array/boolean | Array of files ids or `false` if page has no mockups attached
has_content | object/boolean | Object or `false` if page has no contents

## Get a single page diagrams list

* `GET /v1/sitemaps/<sitemap_id>/page/<page_id>/diagrams`

See the [diagrams](./diagrams.md) endpoint for details on how to get diagrams structures.

### Response

Please see [GET /diagrams](./../diagrams.md#get-list-of-diagrams) endpoint. Response is a list of diagrams assigned to `page_id` in `sitemap_id`.

Possible other [responses](./../../sections/responses.md): `403` and `404`.

## Get a single page files list

* `GET /v1/sitemaps/<sitemap_id>/page/<page_id>/files`

### Response
``` json
[
    {
        "id": "f3fsGeB9W7UooVSuXsWk4ntz3iDh04Cf",
        "date": "2015-04-23T15:40:28+00:00",
        "filename": "IMG_9785.jpg",
        "filesize": 338531,
        "type": "image",
        "url": "https:\/\/example.slickplan.com\/file\/get/(...)",
        "file_type": "mockup"
    },
    {
        "id": "ihiIk4ntz3iDDw89hDh04CfOHPdwuXsW",
        "date": "2015-05-23T10:30:10+00:00",
        "filename": "Video_9786.mov",
        "filesize": 128716,
        "type": "video",
        "url": "https:\/\/example.slickplan.com\/file\/get/(...)",
        "file_type": "file"
    }
]
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
id | string | Unique file ID
date | string | File uploaded date in Atom format
filename | string | Original file name
filesize | integer | File size in bytes
type | string | File type, one of: `image`, `video`, `file`
url | string | An URL to download file from, the link expires after 24 hours
file_type | string | One of: `file`, `mockup`

## Get a single page content

* `GET /v1/sitemaps/<sitemap_id>/page/<page_id>/content`  
or  
`GET /v1/sitemaps/<sitemap_id>/page/<page_id>/content/<language>`

### Response
``` json
{
    "url_slug": "about-us",
    "meta_title": "About Us - Our Website",
    "meta_description": "This page is about us.",
    "meta_keywords": "sample, keywords",
    "template": "",
    "status": "draft",
    "assignee": [82929],
    "language": "en_US",
    "body": [
        {
            "id": "tkhccdtv3n3qxayk",
            "type": "wysiwyg",
            "content": "<h1>This is a HTML content.<\/h1>",
            "options": {
                "label": "Please enter content here",
                "tag": "span"
            }
        },
        {
            "id": "k6531vbj1iabe2jn",
            "type": "text",
            "content": "Plain text",
            "options": {
                "tag": "html",
                "tag_html_before": "<hr><strong>Text:<\/strong><br>",
                "tag_html_after": "<br>"
            }
        },
        {
            "id": "tsmak6jhhb17z1go",
            "type": "image",
            "content": {
                "url": "https:\/\/example.slickplan.com\/file\/download/(...)",
                "filename": "project-logo.jpg",
                "alt": "Project Logo",
                "title": ""
            }
        },
        {
            "id": "hr35smebutiq1nhw",
            "type": "video",
            "content": {
                "url": "https:\/\/vimeo.com\/37623598",
                "description": "New videoclip!"
            }
        },
        {
            "id": "jhhq1nh35smebutw",
            "type": "file"
        },
        {
            "id": "a98nhacva13oju9u",
            "type": "file",
            "content": {
                "url": "http:\/\/example.com\/invoice.pdf",
                "description": "Invoice - september"
            }
        },
        {
            "id": "ge12dejhuno4eb8l",
            "type": "table",
            "content": {
                "rows": "3",
                "cols": "4",
                "data": [
                    [
                        "a single cell data",
                        "",
                        "",
                        ""
                    ],
                    [
                        "",
                        "another cell",
                        "",
                        ""
                    ],
                    [
                        "",
                        "",
                        "",
                        "last cell of the table"
                    ]
                ]
            }
        }
    ]
}
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
url_slug | string | Page's URL slug
meta_title | string | Metadata: title
meta_description | string | Metadata: description
meta_keywords | string | Metadata: keywords
template | string | Content template used
status | string | Current status of this page
assignee | integer/array | A person assigned to this page or an array of assigned people
language | string | Content language
body | array | Content body

#### Content body

Key | Type | Description
--- | --- | ---
id | string | Unique element ID
type | string | Element type, one of: `wysiwyg`, `text`, `image`, `video`, `file`, `table`
content | string/array | Element content
options | array | Element options, one of: `label`, `tag`, `tag_class`, `tag_id`, `tag_html_before`, `tag_html_after`

**Note:** If you have added multiple languages - this will return only the default's language content. To get content in other languages please add its identifier to the URL: `GET /v1/sitemaps/<sitemap_id>/page/<page_id>/content/<language>`. The list of available languages can be obtained [from the Site Settings](./content.md#get-site-settings).