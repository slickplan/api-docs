# Scopes

Scopes let you specify exactly what type of access you need. Scopes limit access for OAuth tokens. They do not grant any additional permission beyond that which the user already has. Scopes ending with `_write` include the same scope with `_read` ending, so there is no need to include both, but it will not throw any error if you do.

Name | Description
--- | ---
account_preferences_read | Grants read-only access to account preferences
account_preferences_write | Grants read/write access to account preferences
contributors_read | Grants read-only access to contributors
contributors_write | Grants read/write access to contributors
company_settings_read | Grants read-only access to company settings
company_settings_write | Grants read/write access to company settings
email_messages_read | Grants read-only access to email messages
email_messages_write | Grants read/write access to email messages
invoice_history_read | Grants read-only access to invoice history
sitemaps_color_palettes_read | Grants read-only access to color palettes
sitemaps_color_palettes_write | Grants read/write access to color palettes
sitemaps_comments_read | Grants read-only access to sitemaps comments (you will need `sitemaps_read` or `sitemaps_write` to get sitemaps list first)
sitemaps_comments_write | Grants read/write access to sitemaps comments (you will need `sitemaps_read` or `sitemaps_write` to get sitemaps list first)
sitemaps_content_read | Grants read-only access to sitemap contents
sitemaps_content_write | Grants read/write access to sitemap contents
sitemaps_diagrams_read | Grants read-only access to sitemap diagrams
sitemaps_diagrams_write | Grants read/write access to sitemap diagrams
sitemaps_files_read | Grants read-only access to sitemap files
sitemaps_files_write | Grants read/write access to sitemap files
sitemaps_page_types_read | Grants read-only access to page types (sitemap archetypes)
sitemaps_page_types_write | Grants read/write access to page types (sitemap archetypes)
sitemaps_read | Grants read-only access to sitemaps structures (**includes** `sitemaps_page_types_read` and `sitemaps_color_palettes_read`). You can also read pages datas such as: note, url, background color and text color
sitemaps_write | Grants read/write access to sitemaps structures (**does not** include `sitemaps_comments_write`, `sitemaps_page_types_write` nor `sitemaps_color_palettes_write`). You can also write pages datas such as: note, url, background color and text color
user_read | Grants read-only access to authorized user information
user_write | Grants read/write access to authorized user information

## Extra (group) scopes

There scopes are just groups, so for example:
1. if you would like your app to access all user’s information you can use just `all_write` scope in your request instead of sending all of the scopes above;
2. if you would like to have read-only access to everything and write access to comments you can use `all_read` scope along with `sitemaps_comments_write`.

**Note:** if, for example, any new `*_write` (or `*_read`) scope will be added in the future and your app requested `all_write` (or `all_read`) you will automatically be granted to access the new scope. Same thing about `sitemap_all_write` (or `sitemaps_all_read`) scope - it will grant access to all new `sitemaps_*_write` (or `sitemaps_*_read`) scopes.

Name | Description
--- | ---
sitemaps_all_read | Groups `sitemaps_read` and `sitemaps_*_read`
sitemaps_all_write | Groups `sitemaps_write` and `sitemaps_*_write`
all_read | Groups all the `*_read` scopes listed on this page
all_write | Groups all the `*_read` and `*_write` scopes listed on this page