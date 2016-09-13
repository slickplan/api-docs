# Sitemap diagrams

**Note:** it’s not possible to fetch archived sitemaps’ diagrams, you will get `HTTP 403 Sitemap archived` response.

## Get a list of diagrams

* `GET /v1/sitemaps/<sitemap_id>/diagrams`
* Required scope: `sitemaps_diagrams_read` or `sitemaps_diagrams_write`

### Response
``` json
[
    {
        "id": "svgdiagramp7xn1dhejrq7fznb",
        "name": "Test"
    },
    {
        "id": "svgdiagrampmkryv9ixxk0th9z",
        "name": "Untitled"
    },
    {
        "id": "svgdiagramfbevytik65zzew67",
        "name": "Website structure UML"
    }
]
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
id | string | Unique diagram ID
name | string | Diagram name

## Get single diagram data

* `GET /v1/sitemaps/<sitemap_id>/diagrams/<diagram_id>`
* Required scope: `sitemaps_diagrams_read` or `sitemaps_diagrams_write`

### Response
``` json
{
    "bbox": {
        "x": 7.5,
        "y": 5,
        "width": 1363.5,
        "height": 315
    },
    "elements": [
        {
            "type": "file",
            "label": "Test file element",
            "id": "svggpymec2fypkzc47ov",
            "matrix": [1, 0, 0, 1, 11.5, 8.5]
        },
        {
            "type": "halfcircle",
            "id": "svggxkmpgkwzaikgcjse",
            "matrix": [1, 0, 0, 1, 1269.5, 134.5]
        },
        {
            "type": "page",
            "label": "Page label",
            "cell_id": "svge2nmmk1wis05l9x5",
            "id": "svgghejv3fd2fasa3kyg",
            "matrix": [1, 0, 0, 1, 1101.5, 70.5]
        },
        {
            "type": "file",
            "label": "Another file",
            "id": "svggnrjy51mnokjmffny",
            "matrix": [1, 0, 0, 1, 1238.5, 208.5]
        },
        {
            "type": "group",
            "label": "Grouped elements",
            "id": "svggae668ocq25ym7l01",
            "matrix": [1, 0, 0, 1, 1061.5, 22.5],
            "width": 305,
            "height": 293
        }
    ],
    "connections": [
        {
            "from-direction": "right",
            "from-element": "svggpymec2fypkzc47ov",
            "to-direction": "up",
            "to-element": "svgghejv3fd2fasa3kyg",
            "type": "arrowtoblock",
            "id": "svgpolylinevw8tforwvyna5utf",
            "points": "111,45 1151,45 1151,68"
        },
        {
            "from-direction": "up",
            "from-element": "svggxkmpgkwzaikgcjse",
            "to-direction": "right",
            "to-element": "svgghejv3fd2fasa3kyg",
            "type": "arrownone",
            "id": "svgpolylinebrmrbkme2nxb6a59",
            "points": "1288,135 1288,107 1201,107"
        },
        {
            "from-direction": "down",
            "from-element": "svggxkmpgkwzaikgcjse",
            "to-direction": "up",
            "to-element": "svggnrjy51mnokjmffny",
            "type": "arrowboth",
            "id": "svgpolylineuwopvfubpnwklm02",
            "points": "1288,156 1288,206"
        }
    ]
}
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
bbox | array | Diagram container size and coordinates of a first element
elements | array | List of diagrams elements
connections | array | List of diagrams elements’ connection lines