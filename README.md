# Slickplan API

This is a REST-style API that uses JSON for serialization and OAuth 2 for authentication.

## Making Requests

### The Base URL

All requests start with the `https://slickplan.com/api/v1/` base URL.

* All requests are done via **SSL only**.
* All responses are in JSON.
* The API expects all data to be UTF-8 encoded.

## Authentication

In order to make authorized calls to Slickplan's API, your application must first obtain an OAuth access token. To register your app go to https://slickplan.com/api/v1/register.

Slickplan implements OAuth2 with the authentication code flow. Read our [OAuth2 authentication guide](./sections/authentication.md) to get started.

Once you have authenticated, you can get information about the authenticated user by calling `GET https://slickplan.com/api/v1/me.json`. More details about the request and response are available on the [endpoint page](./endpoints/me.md).

## Rate Limiting

You can perform up to 25 requests per 10 second period on an account with one OAuth token. If you exceed this limit, you'll get a 403 Rate Limit Exceeded response for subsequent requests. Check the Retry-After header to see how many seconds to wait before retrying the request.

## Response Codes

* `200` OK
* `201` Created
* `204` No Content
* `400` Bad Request
* `401` Unauthorized
* `403` Forbidden
* `404` Not Found
* `5xx` Slickplan is having trouble

## Endpoints

* Account
  * [Company](./endpoints/account/company.md)
  * [Invoices](./endpoints/account/invoices.md)
  * [Messages](./endpoints/account/messages.md)
* [Me](./endpoints/me.md)
* [Sitemaps](./endpoints/sitemaps.md)
  * [Color Palettes](./endpoints/sitemaps/palettes.md)
  * [Comments](./endpoints/sitemaps/comments.md)
  * [Page Types](./endpoints/sitemaps/archetypes.md)
* [Users](./endpoints/users.md)

## Sections

* [Authentication](./sections/authentication.md)
* [Scopes](./sections/scopes.md)
* [User Plans](./endpoints/me.md#user-plans)
* [User Types](./endpoints/me.md#user-types)