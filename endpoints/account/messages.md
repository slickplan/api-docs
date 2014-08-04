# Email Messages

## Get all messages

* `GET /v1/account/messages`
* Required scope: `email_messages_read` or `email_messages_write`

### Response
``` json
{
    "forgotten_password": "**Hi %first_name%,**\r\n\r\nTo reset your password click the link below:\r\n<a href='%url%'>Reset my password<\/a>\r\n\r\nIf the link does not work please copy the entire URL in your browser's address bar.\r\n<a href='%url%'>%url%<\/a>\r\n\r\nPlease disregard this message if you did not request your password.\r\n\r\nThanks, Slickplan",
    "forgotten_username": "**Hi %first_name%,**\r\n\r\nYour Username: **%username%**\r\n\r\nPlease disregard this message if you did not request your username.\r\n\r\nThanks, Slickplan",
    "new_comment": "A new comment has been added to sitemap %sitemap% by %first_name% %last_name%:\r\n\r\n__%comment%__\r\n\u2014 **%first_name% %last_name%**\r\n\r\n<a href='%url%'>View this sitemap<\/a>",
    "register_confirmation": "Welcome to Slickplan %first_name%\r\n\r\nYour new account has been created!\r\n\r\nYou can now login to your personal domain with the following details.\r\n\r\n**Domain:** <a href='%url%'>%domain%<\/a>\r\n**Username:** %username%\r\n\r\nForgot your password? You can <a href='%url%#password'>reset it here<\/a>.",
    "user_invitation": "Hi %first_name%,\r\n\r\nYou have been invited to the %company_name%'s Slickplan account. Please <a href='%url%'>login here<\/a>.\r\n\r\nYour Username: %username%\r\nYour Password: %password%\r\n\r\nAfter logging in for the first time you can change your login details.\r\n\r\nThanks, %owner_name%",
    "user_invitation_sitemap": "Hi %first_name%,\r\n\r\nYou have been invited to the %company_name%'s Slickplan account to %role% the sitemap %sitemap%. Please <a href='%url%'>login here<\/a>.\r\n\r\nYour Username: %username%\r\nYour Password: %password%\r\n\r\nAfter logging in for the first time you can change your login details.\r\n\r\nThanks, %owner_name%",
    "user_invitation_sitemap_exists": "Hi %first_name%,\r\n\r\nYou have been invited to %role% the sitemap %sitemap%. Please <a href='%url%'>login here<\/a>.\r\n\r\nThanks, %owner_name%"
}
```
Key | Type | Description
--- | --- | ---
forgotten_password | string | Forgotten Password.
forgotten_username | string | Forgotten Username.
new_comment | string | New Comment Notification.
register_confirmation | string | Register Confirmation.
user_invitation | string | New User Confirmation.
user_invitation_sitemap | string | New User Confirmation (with sitemap link).
user_invitation_sitemap_exists | string | User Invitation to Sitemap.

## Get single message

* `GET /v1/account/messages/<key>` (ex. `GET /v1/account/messages/forgotten_password`)
* Required scope: `email_messages_read` or `email_messages_write`

### Response
``` json
{
    "forgotten_password": "(...)"
}
```

## Update message

* `PUT /v1/account/messages/<key>` (ex. `PUT /v1/account/messages/forgotten_password`)
* Required scope: `email_messages_write`

Will update the message from the content passed and return the JSON representation of the message. If the user does not have access to update message you'll see `403 Forbidden`. You can use simple markdown syntax to format message, allowed tags:
* `**text**` - bold text
* `__text__` - italic text
* `[text](http://example.com)` or `<a href='http://example.com'>text</a>` - link