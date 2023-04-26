# Sitemap Color Palettes

## Get all custom color palettes

* `GET /v1/palettes`

### Response
``` json
[
    {
        "id": "kf9ptj",
        "name": "Sample Palette",
        "colors": [
            {
                "level": "default",
                "background": "#ddcbd7",
                "text": "#de3355"
            },
            {
                "level": 1,
                "background": "#2835a6",
                "text": null
            },
            {
                "level": "home",
                "text": "#e6d62b"
            },
            {
                "level": "archetype-_dialog",
                "background": null,
                "text": "#e6d62b"
            }
        ]
    },
    {
        "id": "ajkqosjh",
        "name": "Blues",
        "colors": [
            {
                "level": 1,
                "background": "#2b61e6",
                "text": "#2bd3e6"
            },
            {
                "level": 2,
                "background": "#2835a6",
                "text": null
            },
            {
                "level": "archetype-kjiajhj",
                "background": null,
                "text": "#5f2be6"
            }
        ]
    }
]
```

Possible other [responses](./../sections/responses.md): `403`.

Key | Type | Description
--- | --- | ---
id | integer/string | Unique identifier of the color palette
name | string | Color palette name
colors | array | Array of colors in HEX format - min. 1, max. 16 items

## Get single color palette

* `GET /v1/palettes/<id>` (ex. `GET /v1/palettes/ajkqosjh`)

### Response
``` json
{
    "id": "ajkqosjh",
    "name": "Blues",
    "colors": [
        {
            "level": 1,
            "background": "#2b61e6",
            "text": "#2bd3e6"
        },
        {
            "level": 2,
            "background": "#2835a6",
            "text": null
        },
        {
            "level": "archetype-kjiajhj",
            "background": null,
            "text": "#5f2be6"
        }
    ]
}
```

Possible other [responses](./../sections/responses.md): `403` and `404`.

## Create new color palette

* `POST /v1/palettes`
* Requires "write" scope

Will create a new color palette from the parameters passed, return `201 Created` and the JSON representation of the created palette (same format as `GET /v1/palettes/<id>`). Possible other [responses](./../sections/responses.md): `400` and `403`.

### Sample request
``` json
{
    "name": "Red-ish",
    "colors": [
        {
            "level": 1,
            "background": "#2b61e6",
            "text": "#2bd3e6"
        },
        {
            "level": 2,
            "background": "#2835a6",
            "text": null
        },
        {
            "level": "archetype-kjiajhj",
            "background": null,
            "text": "#5f2be6"
        }
    ]
}
```

## Update color palette

* `PUT /v1/palettes/<id>` (ex. `PUT /v1/palettes/ajkqosjh`)
* Requires "write" scope

Will update the new color palette from the parameters passed and return the JSON representation of the updated palette. Possible other [responses](./../sections/responses.md): `400`, `403` and `404`.

### Sample request
``` json
{
    "name": "All kind of red",
    "colors": [
        {
            "level": 1,
            "background": "#2b61e6",
            "text": "#2bd3e6"
        },
        {
            "level": 2,
            "background": "#2835a6",
            "text": null
        },
        {
            "level": "archetype-kjiajhj",
            "background": null,
            "text": "#5f2be6"
        }
    ]
}
```

## Delete color palette

* `DELETE /v1/palettes/<id>` (ex. `PUT /v1/palettes/ajkqosjh`)
* Requires "write" scope

Will delete the specified color palette and return `204 No Content` if that was successful. Possible other [responses](./../sections/responses.md): `403` and `404`.