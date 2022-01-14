# Standalone Diagrams

## Get list of diagrams

* `GET /v1/diagrams`
* Required scope: `diagrams_read` or `diagrams_write`

### Response
``` json
[
    {
        "id": "bannarepfupfrmm9",
        "name": "Website Architecture",
        "created_by": 1,
        "modified_by": 1,
        "date_created": "2016-01-13T14:59:55+00:00",
        "date_modified": "2016-01-13T14:59:55+00:00",
        "is_archived": false,
        "is_locked": false
    },
    {
        "id": "rh6aureonafbcw2v",
        "name": "Test",
        "created_by": 2,
        "modified_by": 1,
        "date_created": "2016-01-11T14:27:35+00:00",
        "date_modified": "2017-01-23T11:29:47+00:00",
        "is_archived": false,
        "is_locked": false
    },
    {
        "id": "hfggkylr7vq9s88o",
        "name": "My Diagram",
        "created_by": 2,
        "modified_by": 2,
        "date_created": "2017-01-02T02:17:30+00:00",
        "date_modified": "2017-01-20T22:28:02+00:00",
        "is_archived": false,
        "is_locked": false
    }
]
```

Possible other [responses](./../sections/responses.md): `403`.

Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the diagram
name | string | Diagram name
created_by | integer | Unique identifier of the user who created the diagram
modified_by | integer | Unique identifier of the user who recently edited the diagram
date_created | string | Diagram creation date in Atom format
date_modified | string | Last modification date in Atom format
is_archived | boolean | `true` if diagram is archived, `false` if it is active
is_locked | boolean | `true` if sitemap is locked, `false` if it is unlocked

## Get a single diagram

* `GET /v1/diagrams/<id>`
* Required scope: `diagrams_read` or `diagrams_write`

### Response
``` json
{
    "id": "bannarepfupfrmm9",
    "name": "Website Architecture",
    "created_by": 1,
    "modified_by": 1,
    "date_created": "2016-01-13T14:59:55+00:00",
    "date_modified": "2016-01-13T14:59:55+00:00",
    "is_locked": false,
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
            "matrix": [1, 0, 0, 1, 11.5, 8.5],
            "order": 1
        },
        {
            "type": "halfcircle",
            "id": "svggxkmpgkwzaikgcjse",
            "matrix": [1, 0, 0, 1, 1269.5, 134.5],
            "order": 3
        },
        {
            "type": "page",
            "label": "Page label",
            "cell_id": "svge2nmmk1wis05l9x5",
            "id": "svgghejv3fd2fasa3kyg",
            "matrix": [1, 0, 0, 1, 1101.5, 70.5],
            "order": 2
        },
        {
            "type": "file",
            "label": "Another file",
            "id": "svggnrjy51mnokjmffny",
            "matrix": [1, 0, 0, 1, 1238.5, 208.5],
            "order": 4
        },
        {
            "type": "group",
            "label": "Grouped elements",
            "id": "svggae668ocq25ym7l01",
            "matrix": [1, 0, 0, 1, 1061.5, 22.5],
            "width": 305,
            "height": 293,
            "order": 5
        }
    ],
    "connections": [
        {
            "from-direction": "right",
            "from-element": "svggpymec2fypkzc47ov",
            "to-direction": "up",
            "to-element": "svgghejv3fd2fasa3kyg",
            "type": "dashed-none-arrow",
            "id": "svgpolylinevw8tforwvyna5utf",
            "points": "111,45 1151,45 1151,68"
        },
        {
            "from-direction": "up",
            "from-element": "svggxkmpgkwzaikgcjse",
            "to-direction": "right",
            "to-element": "svgghejv3fd2fasa3kyg",
            "type": "double-pointer-arrow",
            "id": "svgpolylinebrmrbkme2nxb6a59",
            "points": "1288,135 1288,107 1201,107"
        },
        {
            "from-direction": "down",
            "from-element": "svggxkmpgkwzaikgcjse",
            "to-direction": "up",
            "to-element": "svggnrjy51mnokjmffny",
            "type": "solid-circle-stop",
            "id": "svgpolylineuwopvfubpnwklm02",
            "points": "1288,156 1288,206"
        }
    ],
    "items_data": {
        "svggae668ocq25ym7l01": {
            "magnetize": "1"
        },
        "svgghejv3fd2fasa3kyg": {
            "fill_color": "#cd2525",
            "fill_opacity": "75",
            "border_color": "#1eea1e",
            "text_color": "#8e7ae0"
        }
    }
}
```

Possible other [responses](./../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
bbox | array | Diagram container size and margin from the first elements
elements | array | List of diagram’s elements
connections | array | List of connection lines between elements
items_data | object | List of additional data for elements and connectors

## Create a new diagram

* `POST /v1/diagrams`
* Required scope: `diagrams_write`

### Request
``` json
{
    "name": "New diagram"
}
```

This will return `201 Created` with the current JSON representation of the diagram if the creation was successful. Possible other [responses](./../sections/responses.md): `400` and `403`.

Key | Type | Description
--- | --- | ---
sitemap_id | integer | Unique identifier of the sitemap (optional)
cell_id | string | Unique identifier of a page in sitemap, that the diagram should be assigned to (optional)

## Update a diagram

* `PUT /v1/diagrams/bannarepfupfrmm9`
* Required scope: `diagrams_write`

Will update the diagram from the parameters passed and return the JSON representation of the updated diagram. Possible other [responses](./../sections/responses.md): `400`, `403` and `404`.

### Sample request
``` json
{
    "name": "New diagram name"
}
```

## Delete a diagram

* `DELETE /v1/diagrams/bannarepfupfrmm9`
* Required scope: `diagrams_write`

Will delete the specified diagram and return `204 No Content` if that was successful. Possible other [responses](./../sections/responses.md): `403` and `404`.