# Slickplan API

This is a REST-style API that uses JSON for serialization and OAuth 2 for authentication.

## Making Requests

### The Base URL

All requests start with the `https://slickplan.com/api/v1/` base URL.

* All requests are done via **SSL only**.
* All responses are in JSON.
* The API expects all data to be UTF-8 encoded.

## Authentication

In order to make authorized calls to Slickplan's API, your application must first obtain an OAuth access token. To register your app go to [https://slickplan.com/api/register](https://slickplan.com/api/register) (to modify your existing application details go to `https://slickplan.com/api/register/<client_secret>`).

Slickplan implements OAuth2 with the authentication code flow. Read our [OAuth2 authentication guide](./sections/authentication.md) to get started.

Once you have authenticated, you can get information about the authenticated user by calling `GET https://slickplan.com/api/v1/me`. More details about the request and response are available on the [endpoint page](./endpoints/me.md).

## Rate Limiting

You can perform up to 25 requests per 10 second period on an account with one OAuth token. If you exceed this limit, you'll get a 403 Rate Limit Exceeded response for subsequent requests. Check the Retry-After header to see how many seconds to wait before retrying the request.

## [Response Codes](./sections/responses.md)

* `200` OK
* `201` Created
* `204` No content
* `400` Bad Request / Validation errors
* `401` Unauthorized
* `403` Access denied / Insufficient scope
* `404` Not found
* `5xx` Slickplan is having trouble 🤒

## Endpoints

### Account & Settings
* Account
  * [Company](./endpoints/account/company.md)
  * [Invoices](./endpoints/account/invoices.md)
  * [Messages](./endpoints/account/messages.md)
  * [Preferences](./endpoints/account/preferences.md)
* [Me](./endpoints/me.md)
* [Users](./endpoints/users.md)

### Projects
* [Sitemaps](./endpoints/sitemaps.md)
  * [Diagrams](./endpoints/sitemaps/diagrams.md)
  * [Options](./endpoints/sitemaps/options.md)
  * [Structure](./endpoints/sitemaps/structure.md)
  * [Pages](./endpoints/sitemaps/page.md):
    * [Page Details](./endpoints/sitemaps/page.md#get-a-single-page-details)
    * [Assigned Diagrams](./endpoints/sitemaps/page.md#get-a-single-page-diagrams-list)
    * [Assigned Files/Mockups](./endpoints/sitemaps/page.md#get-a-single-page-files-list)
  * Content Planner:
    * [Page Content](./endpoints/sitemaps/page.md#get-a-single-page-content)
    * [Site Settings](./endpoints/sitemaps/content.md#get-site-settings)
    * [Templates](./endpoints/sitemaps/content.md)
    * [Workflow](./endpoints/sitemaps/content.md#get-a-list-of-workflow-statuses)
* [Diagrams](./endpoints/diagrams.md)
* [Comments](./endpoints/comments.md)
* [Color Palettes](./endpoints/palettes.md)
* [Page Types](./endpoints/archetypes.md)

## Informations

* [Authentication](./sections/authentication.md)
* [Sample Responses](./sections/responses.md)
* [Scopes](./sections/scopes.md)
* [User Plans](./endpoints/me.md#user-plans)
* [User Types](./endpoints/me.md#user-types)

## Support

Having trouble with this API? Contact us directly via email [help@slickplan.com](mailto:help@slickplan.com).