# Users

## Get list of account's users

* `GET /v1/users`

### Response
``` json
[
    {
        "id": 1,
        "email": "elton@example.com",
        "username": "elton",
        "first_name": "Elton",
        "last_name": "John",
        "last_login": "2014-06-20T08:49:20-04:00",
        "created": "2013-10-11T11:32:01-04:00",
        "is_active": false,
        "is_admin": false
    },
    {
        "id": 2,
        "email": "tracy@example.com",
        "username": "tracy",
        "first_name": "Tracy",
        "last_name": "Chapman",
        "last_login": "2014-07-15T09:17:04-04:00",
        "created": "2013-10-11T12:01:15-04:00",
        "is_active": true,
        "is_admin": false
    },
    {
        "id": 3,
        "email": "justin@example.com",
        "username": "justint",
        "first_name": "Justin",
        "last_name": "Timberlake",
        "last_login": "2014-07-24T17:40:29-04:00",
        "created": "2013-11-18T19:52:59-05:00",
        "is_active": true,
        "is_admin": true
    }
]
```
Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the user
email | string | Email address of the user.
username | string | Username of the user.
first_name | string | First name of the user.
last_name | string | Last name of the user.
last_login | string | Last login date in ISO 8601 format.
created | string | User creation date in ISO 8601 format.
is_active | boolean | `true` if user is active, `false` otherwise.
is_admin | boolean | `true` if user has admin rights, `false` otherwise.

## Get the specified user

* `GET /v1/users/2`

### Response
``` json
{
    "id": 1,
    "email": "elton@example.com",
    "username": "elton",
    "first_name": "Elton",
    "last_name": "John",
    "last_login": "2014-06-20T08:49:20-04:00",
    "created": "2013-10-11T11:32:01-04:00",
    "is_active": false,
    "is_admin": false
}
```
Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the user
email | string | Email address of the user.
username | string | Username of the user.
first_name | string | First name of the user.
last_name | string | Last name of the user.
last_login | string | Last login date in ISO 8601 format.
created | string | User creation date in ISO 8601 format.
is_active | boolean | `true` if user is active, `false` otherwise.
is_admin | boolean | `true` if user has admin rights, `false` otherwise.

## Create an user

* `POST /v1/users`

### Request
``` json
{
    "email": "elton@example.com",
    "username": "elton",
    "first_name": "Elton",
    "last_name": "John",
    "active": true,
    "admin": false
}
```

This will return `201 Created` with the current JSON representation of the user if the creation was successful. If the user does not have access to update the contributor, you'll see `403 Forbidden`.

## Update an user

* `PUT /v1/users/2` will update the user from the parameters passed and return the JSON representation of the updated user. If the user does not have access to update the contributor, you'll see `403 Forbidden`.

## Delete an user

* `DELETE /v1/users/2` will delete the specified user and return `204 No Content` if that was successful. If the user does not have access to delete the contributor, you'll see `403 Forbidden`.