## Get the current User

Use this endpoint to get information about the currently authenticated user.

* `GET /v1/me.json`

### Response
``` json
{
  "id": 1,
  "email": "ian@example.com",
  "username": "ian_lawson",
  "first_name": "Ian",
  "last_name": "Lawson",
  "last_login": "2014-07-29T07:47:32-04:00",
  "signed_up": "2012-03-28T00:30:01-04:00"
}
```
Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the User
email | string | Email address of the User.
username | string | Username of the User.
first_name | string | First name of the User.
last_name | string | Last name of the User.
last_login | string | Last login date in ISO 8601 format.
signed_up | string | Signed up date in ISO 8601 format.