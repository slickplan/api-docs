# Sitemap structure

**Note:** it’s not possible to fetch archived sitemaps, you will get `HTTP 403 Sitemap archived` response.

## Get the sitemap structure

* `GET /v1/sitemaps/<sitemap_id>/structure`

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
            "diagrams": ["cjh2q933fowximgl"],
            "has_note": false,
            "has_url": false,
            "has_content": { "en_US": true },
            "has_files": ["4uDPRO9GKSZeudO0mePrjpl3tFkMST98", "KVzP7fr458Bl3VwIMz6mRTuHMxCQRGdk"],
            "has_mockups": ["9UmqgnSmA8UsWfVkOeUd6wgEcguAfXNe"]
        },
        {
            "color": "#57aa34",
            "archetype": "exrrliyswugymjz",
            "level": 1,
            "text": "Level 1",
            "order": 1000,
            "id": "svgz1wxw28i5deh25tt",
            "diagrams": false,
            "has_note": false,
            "has_url": false,
            "has_files": false,
            "has_mockups": false,
            "has_content": { "en_US": false, "pl_PL": true }
        },
        {
            "level": 2,
            "text": "Level 2",
            "order": 1000,
            "id": "svgzcqzw2zegdehrliy",
            "parent": "svgz1wxw28i5deh25tt",
            "has_note": false,
            "has_url": true,
            "has_files": false,
            "has_mockups": false,
            "has_content": { "en_US": true }
        },
        {
            "color": "#cc2e2e",
            "textcolor": "#eacdcd",
            "level": "foot",
            "text": "Example",
            "order": 5000,
            "id": "svgvcqzzz9gpzegqypa",
            "has_note": true,
            "has_url": false,
            "has_files": false,
            "has_mockups": ["9UmqgnSmA8UsWfVkOeUd6wgEcguAfXNe", "61dYvYaor8xyBARljLfCMxaWUhTVQp9g"],
            "has_content": { "en_US": true }
        }
    ],
    "svgtvberlfm9etj2iqp": [
        {
            "level": "home",
            "text": "Section Home",
            "order": 1,
            "id": "svgedzxjgdut1yndneo",
            "has_note": false,
            "has_url": false,
            "has_files": false,
            "has_mockups": false,
            "has_content": { "en_US": true }
        }
    ]
}
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

See the description of a single page details on the (page endpoint)[./page.md].

## Get the specified section structure

* `GET /v1/sitemaps/<sitemap_id>/structure/<section_id>`

### Response
``` json
[
    {
        "color": "#5a5151",
        "level": "home",
        "text": "Homepage",
        "order": 1,
        "id": "svgmld3kg61tyrrcjzb",
        "diagrams": ["cjh2q933fowximgl"],
        "has_note": false,
        "has_url": false,
        "has_content": { "en_US": true },
        "has_files": ["4uDPRO9GKSZeudO0mePrjpl3tFkMST98", "KVzP7fr458Bl3VwIMz6mRTuHMxCQRGdk"],
        "has_mockups": ["9UmqgnSmA8UsWfVkOeUd6wgEcguAfXNe", "61dYvYaor8xyBARljLfCMxaWUhTVQp9g"]
    },
    {
        "color": "#57aa34",
        "archetype": "exrrliyswugymjz",
        "level": 1,
        "text": "Level 1",
        "order": 1000,
        "id": "svgz1wxw28i5deh25tt",
        "diagrams": false,
        "has_note": false,
        "has_url": false,
        "has_files": false,
        "has_mockups": false,
        "has_content": { "en_US": true, "pl_PL": true },
    },
    {
        "level": 2,
        "text": "Level 2",
        "order": 1000,
        "id": "svgzcqzw2zegdehrliy",
        "parent": "svgz1wxw28i5deh25tt",
        "has_note": false,
        "has_url": true,
        "has_files": false,
        "has_mockups": false,
        "has_content": { "en_US": false },
    },
    {
        "color": "#cc2e2e",
        "textcolor": "#eacdcd",
        "level": "foot",
        "text": "Example",
        "order": 5000,
        "id": "svgvcqzzz9gpzegqypa",
        "has_note": true,
        "has_url": false,
        "has_files": false,
        "has_mockups": false,
        "has_content": { "en_US": true },
    }
]
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.