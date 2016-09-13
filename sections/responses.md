# Sample responses

## Success responses

### `200 OK`

Default succesfull `GET` and `PUT` methods response, it always have a JSON data.

### `201 Created`

Default successful `POST` method response. Mostly, it does not have any data in the response, but it can sometimes return JSON, for example when creating new [color palette](./../endpoints/palettes.md):

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

### `204 No Content`

Default successful `DELETE` method response. It does not return any content.

## Error responses

### `400 Validation Errors`

When there are some validation errors with input data.

``` json
{
    "message": "Validation errors",
    "status_code": 400,
    "errors": {
        "name": "Name must not be empty",
        "colors": "At least one color is required"
    }
}
```

### `401 Unauthorized`

Unauthorized request, possible reason - incorrect API key.

``` json
{
    "message": "401 Unauthorized",
    "status_code": 401
}
```

### `403 Access Denied`

When an user has insufficient scope - required scopes are returned in `errors > required` array, if there is more than one scope the extra parameter `operator` is returned, it tells if all scopes are required (`and`) or just one of them (`or`).

``` json
{
    "message": "Insufficient scope",
    "status_code": 403,
    "errors": {
        "required": [
            "sitemaps_color_palettes_read",
            "sitemaps_color_palettes_write"
        ],
        "operator": "or"
    },
}
```

When an user does not have permissions to perform an action, for example if viewer tries to update sitemap structure.

``` json
{
    "message": "Access denied",
    "status_code": 403
}
```

### `404 Not Found`

If a requested element does not exist, for example when someone tries to read a structure of deleted sitemap, `message` tells you what the error is about.

``` json
{
    "message": "Sitemap not found",
    "status_code": 404
}
```