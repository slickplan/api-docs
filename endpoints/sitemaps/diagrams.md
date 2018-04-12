# Sitemap diagrams

**Note:** it’s not possible to fetch diagrams from archived sitemaps, you will get `HTTP 403 Sitemap archived` response.

## Get list of diagrams in a sitemap

* `GET /v1/sitemaps/<sitemap_id>/diagrams`
* Required scope: `sitemaps_diagrams_read` or `sitemaps_diagrams_write`

### Response

Please see [GET /diagrams](./../diagrams.md#get-list-of-diagrams) endpoint for details.

## Get single sitemap diagram data

* `GET /v1/sitemaps/<sitemap_id>/diagrams/<diagram_id>`
* Required scope: `sitemaps_diagrams_read` or `sitemaps_diagrams_write`

### Response

Please see [GET /diagrams/<id>](./../diagrams.md#get-a-single-diagram) endpoint for details.