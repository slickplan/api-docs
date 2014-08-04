# Sitemap Color Palettes

## Get all color palettes

* `GET /v1/palettes`
* Required scope: `sitemaps_read` or `sitemaps_color_palettes_read` or `sitemaps_color_palettes_write`

### Response
``` json
[
    {
        "id": 1407165182,
        "name": "Sample Palette",
        "colors": [
            "#ddcbd7",
            "#de3355",
            "#2835a6",
            "#e6d62b"
        ]
    },
    {
        "id": "ajkqosjh",
        "name": "Blues",
        "colors": [
            "#5f2be6",
            "#342be6",
            "#2b61e6",
            "#2ba2e6",
            "#2bd3e6"
        ]
    }
]
```
Key | Type | Description
--- | --- | ---
id | integer/string | Unique identifier of the color palette.
name | string | Color palette name.
colors | array | Array of colors in HEX format, max. 10 colors.

## Get single color palette

* `GET /v1/palettes/<key>` (ex. `GET /v1/palettes/ajkqosjh`)
* Required scope: `sitemaps_read` or `sitemaps_color_palettes_read` or `sitemaps_color_palettes_write`

### Response
``` json
{
    "id": "ajkqosjh",
    "name": "Blues",
    "colors": [
        "#5f2be6",
        "#342be6",
        "#2b61e6",
        "#2ba2e6",
        "#2bd3e6"
    ]
}
```

## Create new color palette

* `POST /v1/palettes`
* Required scope: `sitemaps_color_palettes_write`

Will create a new color palette from the parameters passed and return the JSON representation of the created palette. If the user does not have access to create color palettes you'll see `403 Forbidden`. Validations messages return with `400` HTTP code.

### Sample request
``` json
{
    "name": "Red-ish",
    "colors": [
        "#e66e2b",
        "#e63c2b",
        "#e62b45",
        "#e62b77"
    ]
}
```

## Update color palette

* `PUT /v1/palettes/<key>` (ex. `PUT /v1/palettes/ajkqosjh`)
* Required scope: `sitemaps_color_palettes_write`

Will update the new color palette from the parameters passed and return the JSON representation of the updated palette. If the user does not have access to update color palette you'll see `403 Forbidden`. Validations messages return with `400` HTTP code.

### Sample request
``` json
{
    "name": "All kind of red",
    "colors": [
        "#e66e2b",
        "#e63c2b",
        "#e62b45",
        "#e62b77"
    ]
}
```

## Delete color palette

* `DELETE /v1/palettes/<key>` (ex. `PUT /v1/palettes/ajkqosjh`)
* Required scope: `sitemaps_color_palettes_write`

Will delete the specified color palette and return `204 No Content` if that was successful. If the user does not have access to delete the color palette you'll see `403 Forbidden`.