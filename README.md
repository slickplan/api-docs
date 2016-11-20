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
* `5xx` Slickplan is having trouble

## Endpoints

### Account
* Account
  * [Company](./endpoints/account/company.md)
  * [Invoices](./endpoints/account/invoices.md)
  * [Messages](./endpoints/account/messages.md)
  * [Preferences](./endpoints/account/preferences.md)
* [Me](./endpoints/me.md)
* [Users](./endpoints/users.md)

### Sitemaps
* [Color Palettes](./endpoints/palettes.md)
* [Comments](./endpoints/comments.md)
* [Page Types](./endpoints/archetypes.md)
* [Sitemaps](./endpoints/sitemaps.md)
  * [Diagrams](./endpoints/sitemaps/diagrams.md)
  * [Options](./endpoints/sitemaps/options.md)
  * [Page Details/Content](./endpoints/sitemaps/page.md)
  * [Structure](./endpoints/sitemaps/structure.md)

## Sections

* [Authentication](./sections/authentication.md)
* [Sample Responses](./sections/responses.md)
* [Scopes](./sections/scopes.md)
* [User Plans](./endpoints/me.md#user-plans)
* [User Types](./endpoints/me.md#user-types)

## Changes

**2016-11-11**
* Updated [Color Palettes](./endpoints/account/messages.md) `colors` array format - each item is now an object with `background` (background color), `text` (text color) and `level` (assigned sitemap page level) attributes
* Added `email_invoices` setting to ([Preferences](./endpoints/account/preferences.md))

**2016-09-12**
* Added new endpoints:
  * Account > [Preferences](./endpoints/account/preferences.md)
* Added new [scopes](./sections/scopes.md):
  * `account_preferences_read`
  * `account_preferences_write`
* Added [Sample Responses](./sections/responses.md) page
* Updated [email messages](./endpoints/account/messages.md):
  * removed deprecated messages: `forgotten_password`, `forgotten_username`, `register_confirmation`, `user_invitation_sitemap`, `user_invitation_sitemap_exists`
  * added new messages: `user_invitation_role`, `user_invitation_permission`, `user_invitation_role_permission`, `approved_sitemap`, `request_unlock`, `sitemap_unlocked`
* Removed `warn_before_leaving_page` setting since it is always enabled on all accounts ([Preferences](./endpoints/account/preferences.md))
  
**2015-12-21**
* All dates are now in UTC timezone, Atom format
* Value of `version` in sitemap structures is now a string instead of integer
* Removed `childs` key from sitemap structures, you can use `parent` to build hierarchy
* Added new endpoints:
  * Sitemaps > [Diagrams](./endpoints/sitemaps/diagrams.md)
  * Sitemaps > [Page](./endpoints/sitemaps/page.md)
* Added new [scopes](./sections/scopes.md):
  * `sitemaps_files_read`
  * `sitemaps_files_write`
  * `sitemaps_diagrams_read`
  * `sitemaps_diagrams_write`
  * `sitemaps_content_read`
  * `sitemaps_content_write`
  
**2015-08-05**
* Added new [grouped scopes](./sections/scopes.md):
  * `sitemaps_all_read`
  * `sitemaps_all_write`
  * `all_read`
  * `all_write`

## Support

Having trouble with this API? Contact us directly via email [help@slickplan.com](mailto:help@slickplan.com).