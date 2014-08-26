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
        "date": "2014-08-02T11:52:23-04:00",
        "parent_id": 0
    },
    {
        "id": 3,
        "user_id": 6,
        "username": "tracy",
        "first_name": "Tracy",
        "last_name": "Chapman",
        "email": "tracy@example.com",
        "comment": "Yes, I agree!",
        "date": "2014-08-04T13:25:47-04:00",
        "parent_id": 2
    }
]
```
Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the comment.
user_id | integer | Unique identifier of the user.
username | string | Username of the user.
first_name | string | First name of the user.
last_name | string | Last name of the user.
email | string | Email address of the user.
comment | string | Comment.
date | string | Comment creation date in ISO 8601 format.
parent_id | integer | Unique identifier of the parent comment (so this comment is a reply). Set the `hierarchical` parameter to get parent-child response format.

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
        "date": "2014-08-02T11:52:23-04:00",
        "parent_id": 0,
        "replies": [
            {
                "id": 3,
                "user_id": 6,
                "username": "tracy",
                "first_name": "Tracy",
                "last_name": "Chapman",
                "email": "tracy@example.com",
                "comment": "Yes, I agree!",
                "date": "2014-08-04T13:25:47-04:00",
                "parent_id": 2,
                "replies": null
            }
        ]
    }
]
```

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
    "date": "2014-08-02T11:52:23-04:00",
    "parent_id": 0
}
```

## Create new comment

* `POST /v1/comments/<sitemap_id>`
* Required scope: `sitemaps_comments_write`

Will create a new comment from the parameters passed and return the JSON representation of the created comment. If the user does not have access to create comments you'll see `403 Forbidden`. Validations messages return with `400` HTTP code.

### Sample request
``` json
{
    "comment": "New comment",
    "parent_id": 2
}
```

## Delete comment

* `DELETE /v1/comments/<sitemap_id>/2`
* Required scope: `sitemaps_color_comments_write`

Will delete the specified comment and return `204 No Content` if that was successful. If the user does not have access to delete the comment you'll see `403 Forbidden`.