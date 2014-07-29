# Authenticating with Slickplan

We offer OAuth2 as the standard way to authenticate with our API as this offers a simple flow for users to allow app access without you having to store their passwords.

## Getting started

1. Register your app at [slickplan.com/api/v1/register](https://slickplan.com/api/v1/register). You'll be assigned a `client_id` and `client_secret`. You'll need to provide a `redirect_uri`: a URL where we can send a verification code. Just enter a dummy URL like `http://example.com/oauth` if you're not ready for this yet.
2. [Grab an OAuth 2 library](http://oauth.net/code/).
3. Configure your OAuth 2 library with your `client_id`, `client_secret`, and `redirect_uri`. You'll need to configure these URLs as well:
* `https://slickplan.com/api/v1/authorize` to request authorization,
* `https://slickplan.com/api/v1/token.json` to retrieve tokens.
4. Try making an authorized request to `https://slickplan.com/api/v1/me.json` to dig in and test it out!