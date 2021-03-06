# Sitemap options

**Note:** it’s not possible to fetch archived sitemaps, you will get `HTTP 403 Sitemap archived` response.

## Get the sitemap options

* `GET /v1/sitemaps/<sitemap_id>/options`
* Required scope: `sitemaps_read` or `sitemaps_write`

### Response
``` json
{
    "svgmainsection": {
        "template": "horizontal",
        "design": "gradient",
        "color_scheme": "default",
        "text_shadow": true,
        "id": "svgmainsection"
    },
    "svgtvberlfm9etj2iqp": {
        "template": "horizontal",
        "design": "gradient",
        "color_scheme": {
            "default": "#abcdef",
            "home": "#aabbcc",
            "level1": "#bbccdd",
            "level2": "#123abc"
        },
        "text_shadow": true,
        "id": "svgtvberlfm9etj2iqp"
    }
}
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
id | string | Sitemap section ID
template | string | Sitemap orientation: `horizontal` or `vertical`
design | string | Sitemap pages design type: `gradient` or `flat`
color_scheme | string/array | Sitemap color scheme: `default` or an array of colors
text_shadow | boolean | `true` if there should be a text shadow on pages

#### `color_scheme` Array
Key | Description
--- | ---
default | Default page color
home | Home page color
util | Utility page color
foot | Footer page color
lines | Connection lines color
text | Text color
levelN | Specified level’s page color where `N` is an integer

## Get the specified section options

* `GET /v1/sitemaps/<sitemap_id>/options/<section_id>`
* Required scope: `sitemaps_read` or `sitemaps_write`

### Response
``` json
{
    "template": "horizontal",
    "design": "gradient",
    "color_scheme": {
        "default": "#abcdef",
        "home": "#aabbcc",
        "level1": "#bbccdd",
        "level2": "#123abc"
    },
    "text_shadow": true,
    "id": "svgtvberlfm9etj2iqp"
}
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

## Update section options

* `PUT /v1/sitemaps/<sitemap_id>/options/<section_id>`
* Required scope: `sitemaps_write`; `sitemaps_color_palettes_write` for `design`, `color_scheme` and `text_shadow` modification

Will update the sitemap options from the parameters passed and return the JSON representation of the updated sitemap. Possible other [responses](./../../sections/responses.md): `400`, `403` and `404`.

### Sample request
``` json
{
    "template": "vertical",
    "design": "flat",
    "color_scheme": {
        "default": "#aabbcc",
        "home": "#555",
        "lines": "#000000"
    },
    "text_shadow": false
}
```