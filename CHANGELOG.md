# Slickplan API change log

**2023-04-26**
* Simplified [scopes](./sections/scopes.md)
* Access/refresh tokens expiry times extended.

**2022-01-18**
* Added new endpoints:
  * [Content workflow statuses](./endpoints/sitemaps/content.md#get-a-list-of-workflow-statuses): `GET /v1/sitemaps/<sitemap_id>/content/workflow`
* Updated comments format in [comments listing](./endpoints/comments.md), added `type` attribute

**2022-01-14**
* Added additional data to diagrams lists (`GET /v1/diagrams` and `GET /v1/sitemaps/<sitemap_id>/diagrams`):
  * `is_locked`
* Added additional data to diagram details (`GET /v1/diagrams/<diagram_id>` and `GET /v1/sitemaps/<sitemap_id>/diagrams/<diagram_id>`):
  * `items_data`
  * `elements.*.order`
* Added additional data to sitemap details (`GET /v1/sitemaps` and `GET /v1/sitemaps/<sitemap_id>`):
  * `can_manage`
  * Deprecation notice: `can_view`, `can_edit`, `contributors.*.role`
* Added additional account preferences (`GET /v1/account/preferences`)
* Added additional data to sitemap page files list (`GET /v1/sitemaps/<sitemap_id>/page/<page_id>/files`):
  * `file_type`
* Updated `color_scheme` format in sitemap options (`GET /v1/sitemaps/<sitemap_id>/options`)
* Updated sitemap structure data (`GET /v1/sitemaps/<sitemap_id>/structure` and `GET /v1/sitemaps/<sitemap_id>/page/<page_id>`):
  * updated `has_content`, it's now an object and it includes information about each language
  * updated `has_files`, it's now an array of files ids
  * added `has_mockups` - an array of files ids
  * renamed `has_diagrams` to `diagrams`, it's now an array of diagrams ids,
* Removed `user_invitation_permission` and `request_unlock` message templates (`GET /v1/account/messages`)
* Removed `design` and `text_shadow` sitemap options (`GET /v1/sitemaps/<sitemap_id>/options`)

**2020-02-25**
* Updated `GET /v1/sitemaps/<sitemap_id>/page/<page_id>/content` - added missing metadata to response, and `filename` to returned file details

**2018-04-12**
* Added new endpoints:
  * [Diagrams](./endpoints/diagrams.md)
  * [Site Settings](./endpoints/sitemaps/content.md#get-site-settings)
* Added additional data to diagrams lists (`GET /v1/sitemaps/<sitemap_id>/diagrams` and `GET /v1/sitemaps/<sitemap_id>/diagrams/<diagram_id>`):
  * `created_by`
  * `date_created`
  * `date_modified`
  * `sitemap_id`
* Updated `GET /v1/sitemaps/<sitemap_id>/page/<page_id>/diagrams` response so it has the same format as `GET /v1/diagrams`

**2017-03-25**
* Added new endpoints:
  * [Content Templates](./endpoints/sitemaps/content.md)

**2017-01-28**
* Added new method (`PUT /v1/comments/<sitemap_id>/<comment_id>`) to the [Comments](./endpoints/comments.md#update-a-comment) endpoint
* From today you can assign multiple people to Content Planner page, so the [`assignee` element](./endpoints/sitemaps/page.md#get-a-single-page-content) can also return an array

**2016-11-20**
* Updated [Color Palettes](./endpoints/palettes.md) `colors` array format - each item is now an object with `background` (background color), `text` (text color) and `level` (assigned sitemap page level) attributes
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