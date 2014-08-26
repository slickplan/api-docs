## Get the current User

Use this endpoint to get information about the currently authenticated user.

* `GET /v1/me`
* Required scope: `user_read` (default)

### Response
``` json
{
    "id": 1,
    "email": "john@example.com",
    "username": "john_smith",
    "first_name": "John",
    "last_name": "Smith",
    "timezone": "",
    "last_login": "2014-07-29T08:47:32-04:00",
    "signed_up": "2012-03-28T10:30:01-04:00",
    "account_uri": "http://example.slickplan.com/",
    "user_plan": "premium",
    "user_type": "owner",
    "is_active": true
}
```
Key | Type | Description
--- | --- | ---
id | integer | Unique identifier of the user
email | string | Email address of the user.
username | string | Username of the user.
first_name | string | First name of the user.
last_name | string | Last name of the user.
timezone | string | User timezone, [check the supported list of timezones](http://php.net/manual/en/timezones.php).
last_login | string | Last login date in ISO 8601 format.
signed_up | string | Signed up date in ISO 8601 format.
account_uri | string | Account URI with trailing slash or empty if account has not been activated yet.
user_plan | string | User plan, check the table below.
user_type | string | User type, check the table below.
is_active | boolean | `true` if account is active, `false` otherwise.

## Update current user data

* `PUT /v1/me`
* Required scope: `user_write`

Will update the currently authenticated user information from the parameters passed and return the JSON representation of the user.

### Sample request
``` json
{
    "email": "john@example.com",
    "username": "john_smith",
    "first_name": "John",
    "last_name": "Smith",
    "timezone": "Europe\/Warsaw"
}
```

## User plans

Name | Description
--- | ---
`free` | Free user
`basic` | Basic plan user
`premium` | Premium plan user
`unlimited` | Unlimited plan user

## User types

Name | Description
--- | ---
`owner` | Account owner
`admin` | An admin account
`contributor` | A contributor account