# Sitemap structure

**Note:** it's not possible to fetch archived sitemaps, you will get `HTTP 403 Forbidden` response.

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
            "id": "svgmld3kg61tyrrcjzb",
            "has_diagrams": false,
            "has_files": false,
            "has_content": false
        },
        {
            "color": "#57aa34",
            "archetype": "exrrliyswugymjz",
            "level": 1,
            "text": "Level 1",
            "order": 1000,
            "id": "svgz1wxw28i5deh25tt",
            "has_diagrams": false,
            "has_files": true,
            "has_content": false
        },
        {
            "color": "#fbcdaf",
            "level": "foot",
            "text": "Example",
            "order": 5000,
            "id": "svgvcqzzz9gpzegqypa",
            "has_diagrams": true,
            "has_files": false,
            "has_content": true
        }
    ],
    "svgtvberlfm9etj2iqp": [
        {
            "level": "home",
            "text": "Section Home",
            "order": 1,
            "id": "svgedzxjgdut1yndneo",
            "has_diagrams": false,
            "has_files": false,
            "has_content": true
        }
    ]
}
```

See the description of a single page details on the (page endpoint)[./page.md].

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
        "id": "svgmld3kg61tyrrcjzb",
        "has_diagrams": false,
        "has_files": false,
        "has_content": false
    },
    {
        "color": "#57aa34",
        "archetype": "exrrliyswugymjz",
        "level": 1,
        "text": "Level 1",
        "order": 1000,
        "id": "svgz1wxw28i5deh25tt",
        "has_diagrams": true,
        "has_files": false,
        "has_content": true
    },
    {
        "color": "#fbcdaf",
        "level": "foot",
        "text": "Example",
        "order": 5000,
        "id": "svgvcqzzz9gpzegqypa",
        "has_diagrams": true,
        "has_files": false,
        "has_content": true
    }
]
```