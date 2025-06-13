# Authorization

This document outlines the authorization process for integrating with Scalev API. We use OAuth 2.0 to allow third-party applications to access user data securely and with user consent. By following this guide, you will learn how to authenticate users, obtain access tokens, and make authorized API requests.

## Overview

Scalev API uses the OAuth 2.0 Authorization Code flow, which provides a secure way for your application to obtain permission to access resources on behalf of a user. The flow consists of these key steps:

1. Registering your application with Scalev
2. Redirecting users to Scalev's authorization page
3. Receiving an authorization code
4. Exchanging the code for access and refresh tokens
5. Using the access token to make API requests
6. Refreshing the access token when it expires

## Step 1: Register Your Application

Before you can begin the OAuth flow, you need to register your application:

1. Log into your Scalev account
2. Navigate to [**Settings > Developers > Apps**](https://app.scalev.id/setting/developers/apps)
3. Click on "Create New App"
4. Fill out the required information:
   - Application name
   - Description
   - Redirect URI (where users will be sent after authorization)
   - Requested scopes (permissions your app requires)
5. Submit the form to create your application
6. You will receive a **Client ID** and **Client Secret** - store these securely

> ⚠️ **Security Note**: Keep your Client Secret confidential. Never expose it in client-side code or public repositories.

## Step 2: Authorization Request

When a user wants to connect your application to their Scalev account, redirect them to Scalev's authorization endpoint with the following parameters:

```
https://app.scalev.id/oauth/authorize?
  client_id=YOUR_CLIENT_ID&
  redirect_uri=YOUR_REDIRECT_URI&
  response_type=code&
  state=RANDOM_STATE_STRING
```

| Parameter       | Required | Description                                                                                                        |
| --------------- | -------- | ------------------------------------------------------------------------------------------------------------------ |
| `client_id`     | Yes      | The Client ID you received when registering your application                                                       |
| `redirect_uri`  | Yes      | The URI where users will be sent after authorization (must match one registered with your app)                     |
| `response_type` | Yes      | Must be set to `code` for the Authorization Code flow                                                              |
| `state`         | Yes      | A random string you generate to protect against CSRF attacks. You should validate this when receiving the callback |

## Step 3: User Authorization

At the authorization page, users will:

1. Log in to their Scalev account (if not already logged in)
2. See information about your application and the permissions you're requesting
3. Choose to approve or deny the authorization request

## Step 4: Receiving the Authorization Code

If the user approves your request, Scalev will redirect them back to your `redirect_uri` with the following parameters:

```
https://your-redirect-uri.com/callback?code=AUTHORIZATION_CODE&state=RANDOM_STATE_STRING
```

| Parameter | Description                                                                                |
| --------- | ------------------------------------------------------------------------------------------ |
| `code`    | The authorization code that you'll exchange for an access token; only valid for 10 minutes |
| `state`   | The same state parameter you provided in the authorization request                         |

Important security steps:

1. Verify that the `state` parameter matches the one you sent in the original request
2. Exchange the code for tokens promptly as authorization codes expire quickly

## Step 5: Exchanging the Code for Tokens

Make a POST request to Scalev's token endpoint to exchange your authorization code for tokens:

```
POST https://api.scalev.id/v2/oauth/token
Content-Type: application/json

{
  "grant_type": "authorization_code",
  "code": "AUTHORIZATION_CODE",
  "client_id": "YOUR_CLIENT_ID",
  "client_secret": "client_secret"
}
```

If successful, you'll receive a JSON response containing:

```json
{
  "access_token": "ACCESS_TOKEN",
  "refresh_token": "REFRESH_TOKEN",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

| Field           | Description                                                               |
| --------------- | ------------------------------------------------------------------------- |
| `access_token`  | Token to use for authenticating API requests                              |
| `refresh_token` | Token to use for obtaining new access tokens                              |
| `token_type`    | Always "Bearer"                                                           |
| `expires_in`    | Time until the access token expires, in seconds (typically 3600 = 1 hour) |

## Step 6: Using the Access Token

Use the access token to authenticate requests to Scalev API by including it in the Authorization header:

```
GET https://api.scalev.id/v2/some-endpoint
Authorization: Bearer ACCESS_TOKEN
```

## Step 7: Refreshing Access Tokens

Access tokens expire after 1 hour. When an access token expires, use the refresh token to obtain a new one without requiring user interaction:

```
POST https://api.scalev.id/v2/oauth/token
Content-Type: application/json

{
  "grant_type": "refresh_token",
  "refresh_token": "REFRESH_TOKEN",
  "client_id": "YOUR_CLIENT_ID",
  "client_secret": "client_secret"
}
```

The response will contain a new access token and refresh token:

```json
{
  "access_token": "NEW_ACCESS_TOKEN",
  "refresh_token": "NEW_REFRESH_TOKEN",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

> ⚠️ **Important**: Always update both your access token AND refresh token after a refresh operation. The old refresh token will be invalidated.

## Token Lifecycle and Security

- **Access Tokens**: Short-lived (1 hour) to limit potential damage if compromised
- **Refresh Tokens**: Longer-lived (30 days) but can be revoked
- **Token Storage**: Store tokens securely and never expose them to client-side code
- **Token Expiration**: Implement proper token refresh mechanisms to ensure uninterrupted service

## Revoking Access

If your app needs to revoke its access to a user's account, you can do so by making a request to the revocation endpoint:

```
POST https://api.scalev.id/v2/oauth/revoke
Content-Type: application/json

{
  "token": "TOKEN_TO_REVOKE",
  "token_type": "refresh_token",
  "client_id": "YOUR_CLIENT_ID",
  "client_secret": "YOUR_CLIENT_SECRET"
}
```

## Best Practices

1. **Implement PKCE (Proof Key for Code Exchange)** for added security, especially for mobile apps
2. **Validate all redirect URI parameters** to prevent open redirect vulnerabilities
3. **Use the state parameter** to protect against CSRF attacks
4. **Store tokens securely**, never in local storage or cookies accessible by JavaScript
5. **Implement proper error handling** for all OAuth-related operations
6. **Be prepared for token refresh failures** and redirect users to re-authenticate when necessary

## Error Handling

The OAuth endpoints may return various error responses. Common error codes include:

| Error                 | Description                                                           |
| --------------------- | --------------------------------------------------------------------- |
| `invalid_request`     | The request is missing a required parameter or is otherwise malformed |
| `invalid_client`      | Client authentication failed                                          |
| `invalid_grant`       | The authorization code or refresh token is invalid or expired         |
| `unauthorized_client` | The client is not authorized to use the requested grant type          |
| `server_error`        | The server encountered an unexpected error                            |
