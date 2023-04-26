# Sitemap options

**Note:** it’s not possible to fetch archived sitemaps, you will get `HTTP 403 Sitemap archived` response.

## Get the sitemap options

* `GET /v1/sitemaps/<sitemap_id>/options`

### Response
``` json
{
    "svgmainsection": {
        "template": "horizontal",
        "color_scheme": "default"
    },
    "svgtvberlfm9etj2iqp": {
        "template": "tree",
        "default_color": "#fdfdfe",
        "lines_color": "#dbdbdd",
        "text_color": "#404040",
        "color_scheme": {
            "home": {
                "text": null,
                "background": "#aabbcc"
            },
            "level1": {
                "text": "#000000",
                "background": "#bbccdd"
            },
            "level2": {
                "text": "#000000",
                "background": "#123abc"
            },
            "archetype-kxoajsij": {
                "text": "#ff0000",
                "background": null
            }
        }
    }
}
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
id | string | Sitemap section ID
template | string | Sitemap orientation: `horizontal`, `vertical` or `tree`
color_scheme | string/array | Sitemap color scheme: `default` or an array of colors
default_color | string | Default cell box color
text_color | string | Default cell text color
lines_color | string | Default sitemap connection lines color
design | string | *Removed*
text_shadow | boolean | *Removed*

#### `color_scheme` Array
Key | Description
--- | ---
home | Home page color
util | Utility page color
foot | Footer page color
levelN | Specified level’s page color where `N` is an integer
archetype-X | Specified color for pages with assigned `X` archetype

## Get the specified section options

* `GET /v1/sitemaps/<sitemap_id>/options/<section_id>`

### Response
``` json
{
    "template": "horizontal",
    "color_scheme": "default"
}
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

## Update section options

* `PUT /v1/sitemaps/<sitemap_id>/options/<section_id>`
* Requires "write" scope

Will update the sitemap options from the parameters passed and return the JSON representation of the updated sitemap. Possible other [responses](./../../sections/responses.md): `400`, `403` and `404`.

### Sample request
``` json
{
    "template": "vertical",
    "color_scheme": "default"
}
```