# Email Messages

## Get all messages

* `GET /v1/account/messages`
* Required scope: `email_messages_read` or `email_messages_write`

### Response
``` json
{
    "new_comment": "A new comment has been added to sitemap %sitemap% by %first_name% %last_name%:\r\n\r\n__%comment%__\r\n\u2014 **%first_name% %last_name%**\r\n\r\n[View this sitemap](%url%)",
    "user_invitation": "Hi %first_name%,\r\n\r\nYou have been invited to the %company_name%’s Slickplan account. Please [login here](%url%).\r\n\r\nYour Username: %username%\r\nYour Password: %password%\r\n\r\nAfter logging in for the first time you can change your login details.\r\n\r\nThanks, %owner_name%",
    "user_invitation_role": "Hi %first_name%,\r\n\r\nYou have been invited to %role% the sitemap %sitemap%. Please [login here](%url%).\r\n\r\nThanks, %owner_name%",
    "user_invitation_permission": "Hi %first_name%,\r\n\r\nYou have been given %permission% permissions to the sitemap %sitemap%. Please [login here](%url%).\r\n\r\nThanks, %owner_name%",
    "user_invitation_role_permission": "Hi %first_name%,\r\n\r\nYou have been invited to %role% the sitemap %sitemap%. You have also been given %permission% permissions. Please [login here](%url%).\r\n\r\nThanks, %owner_name%",
    "approved_sitemap": "Hi %first_name%,\r\n\r\nThe sitemap %sitemap% has been approved by %user%.\r\n\r\nPlease [login here](%url%).",
    "request_unlock": "Hi %first_name%,\r\n\r\nA(n) %role% on your team, %user%, is requesting that the sitemap %sitemap% be unlocked.\r\n\r\nThis may affect the sitemap’s approval status.\r\n\r\nPlease [login here](%url%).",
    "sitemap_unlocked": "Hi %first_name%,\r\n\r\nThe sitemap %sitemap% you approved has be unlocked by %user%.\r\n\r\nThis has affected %sitemap% sitemap’s approval status.\r\n\r\nPlease consult your team as the sitemap will need to be a approved again.\r\n\r\nPlease [login here](%url%)."
}
```

Possible other [responses](./../../sections/responses.md): `403`.

Key | Type | Description
--- | --- | ---
new_comment | string | New comment notification
user_invitation | string | New user invitation with username and password
user_invitation_role | string | User invitation, with sitemap link and sitemap role
user_invitation_permission | string | User invitation, with sitemap link and extra permissions info
user_invitation_role_permission | string | User invitation, with sitemap link, sitemap role and extra permissions info
approved_sitemap | string | Sitemap approval notification
request_unlock | string | Request to unlock a sitemap
sitemap_unlocked | string | Sitemap unlocked notification

## Get single message

* `GET /v1/account/messages/<key>` (ex. `GET /v1/account/messages/new_comment`)
* Required scope: `email_messages_read` or `email_messages_write`

### Response
``` json
{
    "new_comment": "(...)"
}
```

Possible other [responses](./../../sections/responses.md): `403` and `404`.

## Update message

* `PUT /v1/account/messages/<key>` (ex. `PUT /v1/account/messages/new_comment`)
* Required scope: `email_messages_write`

You can use simple markdown syntax to format message, allowed tags:
* `**text**` - bold text
* `__text__` - italic text
* `[text](http://example.com)` or `<a href="http://example.com">text</a>` - link

Will update the message from the content passed and return the JSON representation of the message. You can pass an empty string to reset the message to default value. Possible other [responses](./../../sections/responses.md): `400`, `403` and `404`.