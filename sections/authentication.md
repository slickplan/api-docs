# Authenticating with Slickplan

We offer OAuth2 as the standard way to authenticate with our API as this offers a simple flow for users to allow app access without you having to store their passwords.

## Getting started

1. Register your app at [slickplan.com/api/register](https://slickplan.com/api/register).
  You’ll be assigned a `client_id` and `client_secret`. You’ll need to provide a `redirect_uri`: a URL where we can send a verification code. Just enter a dummy URL like `https://example.com/oauth` if you’re not ready for this yet.
2. [Grab an OAuth2 library](https://oauth.net/code/).
3. Configure your OAuth2 library with your `client_id`, `client_secret`, and `redirect_uri`.

  You’ll need to configure these URLs as well:
  * `https://slickplan.com/api/v1/authorize` to request authorization
    
    **Parameters**
    
    Key | Type | Description
    --- | --- | ---
    response_type | string | **Required.** Value MUST be set to `code`
    client_id | string | **Required.** The client ID you received from Slickplan when you registered
    redirect_uri | string | **Required.** The URL in your app where users will be sent after authorization
    state | string | **Recommended.** This is an unguessable random string, equivalent of a `CSRF` token, and provides session validation for your authorize request. See the [OAuth2.0 Spec](https://tools.ietf.org/html/rfc6749#section-4.1.1) for more information
    scope | string | Optional. A space separated list of [scopes](./scopes.md). If not provided, scope defaults to `all_read`
    
    If the user accepts your request, Slickplan redirects back to your site with a temporary code in a `code` parameter as well as the state you provided in the previous step in a `state` parameter. If the states don’t match, the request has been created by a third party and the process should be aborted.

  * `https://slickplan.com/api/v1/token` to retrieve tokens
    
    **Parameters**
    
    Key | Type | Description
    --- | --- | ---
    client_id | string | **Required.** The client ID you received from Slickplan when you registered
    client_secret | string | **Required.** The client secret you received from Slickplan when you registered
    redirect_uri | string | **Required.** The URL in your app where users will be sent after authorization
    code | string | **Required.** The code you received as a response after authorization
    
    **Response**
    
    ``` json
    {
        "access_token": "742075952535e1ae2f616z189c1828fac2a2a555",
        "expires_in": 604800,
        "token_type": "Bearer",
        "refresh_token": "f31ee59fc5ez8443015cff37f572f8ec39dca7da"
    }
    ```

    Use the access token to access the Slickplan API. The access token allows you to make requests to the API on a behalf of a user, i.e.:

    `GET https://slickplan.com/api/v1/me?access_token=...`
    
    Access token expires after 60 days and need to be refreshed. Refresh token expires after 180 days. When authenticating, a refresh token and expiration timestamp is provided. Use the refresh token to retrieve a new access token. Most OAuth2 client libraries will handle this automatically.
