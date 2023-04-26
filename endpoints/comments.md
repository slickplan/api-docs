# Sitemap Comments

## Get all comments

* `GET /v1/comments/<sitemap_id>`

### Response
``` json
[
    {
        "id": 2,
        "user_id": 5,
        "comment": "New <a href=\"http:\/\/example.com\">comment<\/a>",
        "date": "2014-08-02T11:52:23+00:00",
        "parent_id": 0,
        "file_id": "f3fsGeB9W7UooVSuXsWk4ntz3iDh04Cf",
        "page_id": "svgdyt34vfijwcrlgoc"
    },
    {
        "id": 3,
        "user_id": 6,
        "comment": "Yes, I agree!",
        "date": "2014-08-04T13:25:47+00:00",
        "parent_id": 2
    },
    {
        "id": 212,
        "user_id": 1,
        "comment": "test",
        "date": "2022-01-14T14:32:47+00:00",
        "type": "page",
        "cell_id": "svgolwjdqghoxfqku9p"
    },
    {
        "id": 213,
        "user_id": 1,
        "comment": "Content Planner comment",
        "date": "2022-01-18T16:14:40+00:00",
        "type": "content",
        "language": "en_US",
        "cell_id": "svgyz6lapiz15hslp41",
        "block_id": "g6qzugdiq"
    },
    {
        "id": 214,
        "user_id": 0,
        "comment": "Comment about mockup",
        "date": "2022-01-18T16:15:27+00:00",
        "type": "file",
        "file_id": "YfGKuaQZleDDuzcCj7Q79hhtuYcfp4xe",
        "cell_id": "svgk74ni0cfenp533zh",
        "guest": {
            "name": "John",
            "email": "john@example.com"
        }
    }
]
```

Possible other [responses](./../sections/responses.md): `403` and `404`.

Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the comment
user_id | integer | Unique identifier of the user, `0` if comment was added by a guest
guest | object | Only present if comment was added by a guest (not registered user), also `user_id` is `0`
comment | string | Comment body
date | string | Comment creation date in Atom format
parent_id | integer | Unique identifier of the parent comment (so this comment is a reply). Set the `hierarchical` parameter to get parent-child response format
type | string | One of: `page`, `file`, `content` or empty if that comment was added globally to a project
cell_id | string | Sitemap's page ID, only present if `type` is set and one of: `page`, `file`, `content`
file_id | string | Design Mockup file ID, only present if `type` is `file`
block_id | string | Content block ID, only present if `type` is `content` and also if `page_id` is present
language | string | Only present if `type` is `content`, determines to which language the comment has been added

## Get all comments (hierarchical)

* `GET /v1/comments/<sitemap_id>?hierarchical=1`

### Response
``` json
[
    {
        "id": 2,
        "user_id": 5,
        "comment": "New <a href=\"http:\/\/example.com\">comment<\/a>",
        "date": "2014-08-02T11:52:23+00:00",
        "replies": [
            {
                "id": 3,
                "user_id": 6,
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

### Response
``` json
{
    "id": 2,
    "user_id": 5,
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
* Requires "write" scope

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
* Requires "write" scope

Will update the comment from the parameters passed and return the JSON representation of the updated comment. Possible other [responses](./../sections/responses.md): `400`, `403` and `404`.

### Sample request
``` json
{
    "comment": "<p><b>Updated<\/b> comment<\/p>"
}
```

## Delete comment

* `DELETE /v1/comments/<sitemap_id>/2`
* Requires "write" scope

Will delete the specified comment and return `204 No Content` if that was successful. Possible other [responses](./../sections/responses.md): `403` and `404`.