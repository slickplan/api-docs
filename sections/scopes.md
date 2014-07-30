# Scopes

Scopes let you specify exactly what type of access you need. Scopes limit access for OAuth tokens. They do not grant any additional permission beyond that which the user already has.

Name | Description
--- | ---
user_read | Grants read-only access to authorized user information.
user_write | Grants read/write access to authorized user information.
contributors_read | Grants read-only access to contributors.
contributors_write | Grants read/write access to contributors.
company_settings_read | Grants read-only access to company settings.
company_settings_write | Grants read/write access to company settings.
email_messages_read | Grants read-only access to email messages.
email_messages_write | Grants read/write access to email messages.
invoice_history_read | Grants read-only access to invoice history.
sitemaps_read | Grants read-only access to sitemaps (**includes** `sitemaps_page_types_read` and `sitemaps_color_palettes_read`).
sitemaps_write | Grants read/write access to sitemaps (**does not** include `sitemaps_comments_write`, `sitemaps_page_types_write` nor `sitemaps_color_palettes_write`).
sitemaps_comments_read | Grants read-only access to sitemaps comments (you will need `sitemaps_read` or `sitemaps_write` to get sitemaps list first).
sitemaps_comments_write | Grants read/write access to sitemaps comments (you will need `sitemaps_read` or `sitemaps_write` to get sitemaps list first).
sitemaps_page_types_read | Grants read-only access to page types (sitemap archetypes).
sitemaps_page_types_write | Grants read/write access to page types (sitemap archetypes).
sitemaps_color_palettes_read | Grants read-only access to color palettes.
sitemaps_color_palettes_write | Grants read/write access to color palettes.