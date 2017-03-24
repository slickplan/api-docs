# Sitemap page details

See how to get a sitemap's pages list on the (structure endpoint)[./structure.md]. **Note:** it’s not possible to fetch archived sitemaps, you will get `HTTP 403 Sitemap archived` response.

## Get a single page details

* `GET /v1/sitemaps/<sitemap_id>/page/<page_id>`
* Required scope: `sitemaps_read` or `sitemaps_write`

### Response
``` json
{
    "id": "svgz1wxw28i5deh25tt",
    "level": 1,
    "text": "Level 1",
    "order": 1000,
    "color": "#57aa34",
    "archetype": "exrrliyswugymjz",
    "url": [
        {
            "type": "external",
            "label": "Link to Slickplan",
            "url": "http:\/\/slickplan.com\/"
        },
        {
            "type": "internal",
            "page": "svga5c8wc1b9t2dwppi"
        }
    ],
    "section": "svgnq3nac4e1dzr8z0l",
    "has_diagrams": false,
    "has_files": false,
    "has_content": false
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
has_diagrams | boolean | `true` if page has diagrams
has_files | boolean | `true` if page has design mockups
has_content | boolean | `true` if page has content

## Get a single page diagrams list

* `GET /v1/sitemaps/<sitemap_id>/page/<page_id>/diagrams`
* Required scope: `sitemaps_diagrams_read` or `sitemaps_diagrams_write`

See the [diagrams](./diagrams.md) endpoint for details on how to get diagrams structures.

### Response
``` json
[
    "svgdiagrampmkryv9ixxk0th9z",
    "svgdiagramfbevytik65zzew67"
]
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

## Get a single page files list

* `GET /v1/sitemaps/<sitemap_id>/page/<page_id>/files`
* Required scope: `sitemaps_files_read` or `sitemaps_files_write`

### Response
``` json
[
    {
        "id": "f3fsGeB9W7UooVSuXsWk4ntz3iDh04Cf",
        "date": "2015-04-23T15:40:28+00:00",
        "filename": "IMG_9785.jpg",
        "filesize": 338531,
        "type": "image",
        "url": "https:\/\/example.slickplan.com\/file\/get/(...)"
    },
    {
        "id": "ihiIk4ntz3iDDw89hDh04CfOHPdwuXsW",
        "date": "2015-05-23T10:30:10+00:00",
        "filename": "Video_9786.mov",
        "filesize": 128716,
        "type": "video",
        "url": "https:\/\/example.slickplan.com\/file\/get/(...)"
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

## Get a single page content

* `GET /v1/sitemaps/<sitemap_id>/page/<page_id>/content`
* Required scope: `sitemaps_content_read` or `sitemaps_content_write`

### Response
``` json
{
    "url_slug": "about-us",
    "template": "",
    "status": "draft",
    "assignee": 82929,
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
                "url": "https:\/\/www.google.com\/images\/srpr\/logo11w.png",
                "alt": "Google Logo",
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
template | string | Content template used
status | string | Current status of this page
assignee | integer/array | A person assigned to this page or an array of assigned people
body | array | Content body

#### Content body

Key | Type | Description
--- | --- | ---
id | string | Unique element ID
type | string | Element type, one of: `wysiwyg`, `text`, `image`, `video`, `file`, `table`
content | string/array | Element content
options | array | Element options, one of: `label`, `tag`, `tag_class`, `tag_id`, `tag_html_before`, `tag_html_after`