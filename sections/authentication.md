# Authenticating with Slickplan

We offer OAuth2 as the standard way to authenticate with our API as this offers a simple flow for users to allow app access without you having to store their passwords.

## Getting started

1. Register your app at [slickplan.com/api/v1/register](https://slickplan.com/api/v1/register).
  You'll be assigned a `client_id` and `client_secret`. You'll need to provide a `redirect_uri`: a URL where we can send a verification code. Just enter a dummy URL like `http://example.com/oauth` if you're not ready for this yet.
2. [Grab an OAuth2 library](http://oauth.net/code/).
3. Configure your OAuth2 library with your `client_id`, `client_secret`, and `redirect_uri`.

  You'll need to configure these URLs as well:
  * `https://slickplan.com/api/v1/authorize` to request authorization
    
    **Parameters**
    
    Key | Type | Description
    --- | --- | ---
    client_id | string | **Required.** The client ID you received from Slickplan when you registered.
    redirect_uri | string | **Required.** The URL in your app where users will be sent after authorization.
    scope | string | A space separated list of [scopes](./scopes.md). If not provided, scope defaults to `basic`.
    
    If the user accepts your request, Slickplan redirects back to your site with a temporary code in a `code` parameter.

  * `https://slickplan.com/api/v1/token` to retrieve tokens
    
    **Parameters**
    
    Key | Type | Description
    --- | --- | ---
    client_id | string | **Required.** The client ID you received from Slickplan when you registered.
    client_secret | string | **Required.** The client secret you received from Slickplan when you registered.
    redirect_uri | string | **Required.** The URL in your app where users will be sent after authorization.
    code | string | **Required.** The code you received as a response after authorization.
    
    **Response**
    
    ```json
    {
        "access_token": "742075952535e1ae2f616z189c1828fac2a2a555",
        "expires_in": 604800,
        "token_type": "Bearer",
        "scope": "basic",
        "refresh_token": "f31ee59fc5ez8443015cff37f572f8ec39dca7da"
    }
    ```

    Use the access token to access the Slickplan API. The access token allows you to make requests to the API on a behalf of a user, i.e.:

    `GET https://slickplan.com/api/v1/me?access_token=...`
    
    Access token expires after 7 days and need to be refreshed. When authenticating, a refresh token and expiration timestamp is provided. Use the refresh token to retrieve a new access token. Most OAuth2 client libraries will handle this automatically.