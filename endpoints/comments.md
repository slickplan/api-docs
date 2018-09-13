# Sitemap Comments

## Get all comments

* `GET /v1/comments/<sitemap_id>`
* Required scope: `sitemaps_comments_read` or `sitemaps_comments_write`

### Response
``` json
[
    {
        "id": 2,
        "user_id": 5,
        "username": "elton",
        "first_name": "Elton",
        "last_name": "John",
        "email": "elton@example.com",
        "comment": "New <a href=\"http:\/\/example.com\">comment<\/a>",
        "date": "2014-08-02T11:52:23+00:00",
        "parent_id": 0,
        "file_id": "f3fsGeB9W7UooVSuXsWk4ntz3iDh04Cf",
        "page_id": "svgdyt34vfijwcrlgoc"
    },
    {
        "id": 3,
        "user_id": 6,
        "username": "tracy",
        "first_name": "Tracy",
        "last_name": "Chapman",
        "email": "tracy@example.com",
        "comment": "Yes, I agree!",
        "date": "2014-08-04T13:25:47+00:00",
        "parent_id": 2
    }
]
```

Possible other [responses](./../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the comment
user_id | integer | Unique identifier of the user
username | string | Username of the user
first_name | string | First name of the user
last_name | string | Last name of the user
email | string | Email address of the user
comment | string | Comment’s content
date | string | Comment creation date in Atom format
parent_id | integer | Unique identifier of the parent comment (so this comment is a reply). Set the `hierarchical` parameter to get parent-child response format
file_id | string | Design Mockup file ID
page_id | string | Only if `file_id` is set; sitemap’s page ID where the Design Mockup was uploaded

## Get all comments (hierarchical)

* `GET /v1/comments/<sitemap_id>?hierarchical=1`
* Required scope: `sitemaps_comments_read` or `sitemaps_comments_write`

### Response
``` json
[
    {
        "id": 2,
        "user_id": 5,
        "username": "elton",
        "first_name": "Elton",
        "last_name": "John",
        "email": "elton@example.com",
        "comment": "New <a href=\"http:\/\/example.com\">comment<\/a>",
        "date": "2014-08-02T11:52:23+00:00",
        "file_id": "f3fsGeB9W7UooVSuXsWk4ntz3iDh04Cf",
        "page_id": "svgdyt34vfijwcrlgoc",
        "replies": [
            {
                "id": 3,
                "user_id": 6,
                "username": "tracy",
                "first_name": "Tracy",
                "last_name": "Chapman",
                "email": "tracy@example.com",
                "comment": "Yes, I agree!",
                "date": "2014-08-04T13:25:47+00:00"
            }
        ]
    }
]
```

Possible other [responses](./../sections/responses.md): `403` and `404`.

## Get single comment

* `GET /v1/comments/<sitemap_id>/2`
* Required scope: `sitemaps_comments_read` or `sitemaps_comments_write`

### Response
``` json
{
    "id": 2,
    "user_id": 5,
    "username": "elton",
    "first_name": "Elton",
    "last_name": "John",
    "email": "elton@example.com",
    "comment": "New <a href=\"http:\/\/example.com\">comment<\/a>",
    "date": "2014-08-02T11:52:23+00:00",
    "parent_id": 0,
    "file_id": "f3fsGeB9W7UooVSuXsWk4ntz3iDh04Cf",
    "page_id": "svgdyt34vfijwcrlgoc"
}
```

Possible other [responses](./../sections/responses.md): `403` and `404`.

## Create new comment

* `POST /v1/comments/<sitemap_id>`
* Required scope: `sitemaps_comments_write`

Will create a new comment from the parameters passed and return the JSON representation of the created comment. Possible other [responses](./../sections/responses.md): `400`, `403` and `404`.

### Sample request
``` json
{
    "comment": "New comment",
    "parent_id": 2
}
```

## Update a comment

* `PUT /v1/comments/<sitemap_id>/<comment_id>`
* Required scope: `sitemaps_comments_write`

Will update the comment from the parameters passed and return the JSON representation of the updated comment. Possible other [responses](./../sections/responses.md): `400`, `403` and `404`.

### Sample request
``` json
{
    "comment": "<p><b>Updated<\/b> comment<\/p>"
}
```

## Delete comment

* `DELETE /v1/comments/<sitemap_id>/2`
* Required scope: `sitemaps_color_comments_write`

Will delete the specified comment and return `204 No Content` if that was successful. Possible other [responses](./../sections/responses.md): `403` and `404`.