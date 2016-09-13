# Users

## Get list of account’s users

* `GET /v1/users`
* Required scope: `contributors_read` or `contributors_write`

### Response
``` json
[
    {
        "id": 1,
        "email": "elton@example.com",
        "username": "elton",
        "first_name": "Elton",
        "last_name": "John",
        "last_login": "2014-06-20T08:49:20+00:00",
        "created": "2013-10-11T11:32:01+00:00",
        "is_active": false,
        "user_type": "admin",
        "extra_privileges": [
            "view_invoices",
            "payment"
        ]
    },
    {
        "id": 2,
        "email": "tracy@example.com",
        "username": "tracy",
        "first_name": "Tracy",
        "last_name": "Chapman",
        "last_login": "2014-07-15T09:17:04+00:00",
        "created": "2013-10-11T12:01:15+00:00",
        "is_active": true,
        "user_type": "contributor"
    },
    {
        "id": 3,
        "email": "justin@example.com",
        "username": "justint",
        "first_name": "Justin",
        "last_name": "Timberlake",
        "last_login": "2014-07-24T17:40:29+00:00",
        "created": "2013-11-18T19:52:59-05:00",
        "is_active": true,
        "user_type": "contributor"
    }
]
```

Possible other [responses](./../sections/responses.md): `403`.

Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the user
email | string | Email address of the user
username | string | Username of the user
first_name | string | First name of the user
last_name | string | Last name of the user
last_login | string | Last login date in Atom format
created | string | User creation date in Atom format
is_active | boolean | `true` if user is active, `false` otherwise
user_type | string | User type, check the table in [Me endpoint](./me.md#user-types)
extra_privileges | array | Administrator extra permissions - `view_invoices` is self-explanatory, `payment` - user can manage payment settings

## Get the specified user

* `GET /v1/users/2`
* Required scope: `contributors_read` or `contributors_write`

### Response
``` json
{
    "id": 2,
    "email": "elton@example.com",
    "username": "elton",
    "first_name": "Elton",
    "last_name": "John",
    "last_login": "2014-06-20T08:49:20+00:00",
    "created": "2013-10-11T11:32:01+00:00",
    "is_active": false,
    "user_type": "contributor"
}
```

Possible other [responses](./../sections/responses.md): `403` and `404`.

## Create an user

* `POST /v1/users`
* Required scope: `contributors_write`

### Request
``` json
{
    "email": "elton@example.com",
    "username": "elton",
    "first_name": "Elton",
    "last_name": "John",
    "is_active": true,
    "user_type": "admin"
}
```

This will return `201 Created` with the current JSON representation of the user if the creation was successful. Possible other [responses](./../sections/responses.md): `400` and `403`.

## Update an user

* `PUT /v1/users/2`
* Required scope: `contributors_write`

Will update the user from the parameters passed and return the JSON representation of user’s properties. Possible other [responses](./../sections/responses.md): `400`, `403` and `404`.

## Delete an user

* `DELETE /v1/users/2`
* Required scope: `contributors_write`

Will delete the specified user and return `204 No Content` if that was successful. Possible other [responses](./../sections/responses.md): `403` and `404`.