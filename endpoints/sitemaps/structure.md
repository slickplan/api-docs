# Sitemap structure

## Get the sitemap structure

* `GET /v1/sitemaps/<sitemap_id>/structure`
* Required scope: `sitemaps_read` or `sitemaps_write`

### Response
``` json
{
    "svgmainsection": [
        {
            "color": "#5a5151",
            "level": "home",
            "text": "Homepage",
            "order": 1,
            "id": "svgmld3kg61tyrrcjzb"
        },
        {
            "color": "#57aa34",
            "archetype": "exrrliyswugymjz",
            "level": 1,
            "text": "Level 1",
            "order": 1000,
            "childs": [
                "svgqxnn3tmdii95t73c",
                "svgxzpp9elez3eryp8w",
                "svgp4vknyywt8euw3nu",
                "svgwovrvtucyrdzhl8e",
                "svgjvn9o7hzzz1586h4"
            ],
            "id": "svgz1wxw28i5deh25tt"
        },
        (...)
        {
            "color": "#fbcdaf",
            "level": "foot",
            "text": "Example",
            "order": 5000,
            "id": "svgvcqzzz9gpzegqypa"
        }
    ],
    "svgtvberlfm9etj2iqp": [
        {
            "level": "home",
            "text": "Section Home",
            "order": 1,
            "id": "svgedzxjgdut1yndneo"
        },
        (...)
    ]
}
```
Key | Type | Description
--- | --- | ---
id | string | Sitemap unique page ID.
level | string | Page level: `home`, `util`, `foot` or an integer.
text | string | Page label.
order | integer | Page level order, to use with `ORDER BY`.
color | string | Page background color.
textcolor | string | Page text color.
archetype | string | Page type ID.
parent | string | Parent page ID.
childs | array | Children pages IDs.
desc | string | Page note.
url | string | Page link.

## Get the specified section structure

* `GET /v1/sitemaps/<sitemap_id>/structure/<section_id>`
* Required scope: `sitemaps_read` or `sitemaps_write`

### Response
``` json
[
    {
        "color": "#5a5151",
        "level": "home",
        "text": "Homepage",
        "order": 1,
        "id": "svgmld3kg61tyrrcjzb"
    },
    {
        "color": "#57aa34",
        "archetype": "exrrliyswugymjz",
        "level": 1,
        "text": "Level 1",
        "order": 1000,
        "childs": [
            "svgqxnn3tmdii95t73c",
            "svgxzpp9elez3eryp8w",
            "svgp4vknyywt8euw3nu",
            "svgwovrvtucyrdzhl8e",
            "svgjvn9o7hzzz1586h4"
        ],
        "id": "svgz1wxw28i5deh25tt"
    },
    (...)
    {
        "color": "#fbcdaf",
        "level": "foot",
        "text": "Example",
        "order": 5000,
        "id": "svgvcqzzz9gpzegqypa"
    }
]
```