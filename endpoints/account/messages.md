# Email Messages

## Get all messages

* `GET /v1/account/messages`
* Required scope: `email_messages_read` or `email_messages_write`

### Response
``` json
{
    "user_invitation": "Hi %first_name%,\n\nYou have been invited to the %company_name%'s Slickplan account. Please [click here](%url%) to accept the invitation and set up your password.\n\nYour Username\/Email: %email%\n\nThanks, %sender_name%",
    "user_invitation_role": "Hi %first_name%,\n\nYou have been invited to edit the project %project_name%. Please [login here](%url%).\n\nThanks, %sender_name%",
    "user_invitation_role_permission": "Hi %first_name%,\n\nYou have been invited to edit the project %project_name%. You have also been given %permissions% permissions. Please [login here](%url%).\n\nThanks, %sender_name%",
    "new_comment": "Hi %first_name%,\n\nA new comment has been added to project %project_name% by %author_name%:\n\n__%comment%__\n\n[View this project](%url%)",
    "approved_sitemap": "Hi %first_name%,\n\nThe project %project_name% has been approved by %user%. Please [login here](%url%).\n\nThanks, %sender_name%",
    "sitemap_locked": "Hi %first_name%,\n\nThe project %project_name% has been locked by %user%. Please [login here](%url%).\n\nThanks, %sender_name%",
    "sitemap_unlocked": "Hi %first_name%,\n\nThe project %project_name% has been unlocked by %user%. Please [login here](%url%).\n\nThanks, %sender_name%"
}
```

Possible other [responses](./../../sections/responses.md): `403`.

Key | Type | Description
--- | --- | ---
user_invitation | string | New user invitation with username and password
user_invitation_role | string | User invitation, with sitemap link and sitemap role
user_invitation_role_permission | string | User invitation, with sitemap link, sitemap role and extra permissions info
new_comment | string | New comment notification
approved_sitemap | string | Sitemap approval notification
sitemap_locked | string | Sitemap unlocked notification
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
* `[text](https://example.com)` or `<a href="https://example.com">text</a>` - link

Will update the message from the content passed and return the JSON representation of the message. You can pass an empty string to reset the message to default value. Possible other [responses](./../../sections/responses.md): `400`, `403` and `404`.