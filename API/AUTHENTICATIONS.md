# Authentication Guide

AVCI-CMS uses JWT (JSON Web Tokens) for authenticating users. While most catalog endpoints only require a Workspace ID, user-specific actions (like managing a basket, placing an order, or viewing a profile) require a valid User Token.

## Authentication Headers

| Header | Description |
| :--- | :--- |
| `Authorization` | `Bearer <ACCESS_TOKEN>` |
| `x-avci-workspace` | Your Workspace UUID (Mandatory for all requests) |

## Login Flow

1. **Login**: Send email and password to the login endpoint.
2. **Access Token**: If successful, you receive an `accessToken`.
3. **Storage**: Store the token securely in your client.
4. **Authorized Requests**: Include the `Authorization: Bearer <token>` header in subsequent requests to protected endpoints.

### Refreshing Tokens

Access tokens have a limited lifespan. Use the `refreshToken` received during login to obtain a new access token when the old one expires.

## Authentication Endpoints

### Login
`POST /v1/auth/login`

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "yourpassword"
}
```

**Response:**
```json
{
  "user": {
    "name": { "first": "John", "last": "Doe" },
    "email": "user@example.com"
  },
  "tokens": {
    "access": {
      "token": "...",
      "expires": "2024-..."
    },
    "refresh": {
      "token": "...",
      "expires": "2024-..."
    }
  }
}
```

### Sign Up
`POST /v1/auth/signup`

**Request Body:**
```json
{
  "name": { "first": "John", "last": "Doe" },
  "email": "user@example.com",
  "password": "yourpassword"
}
```

### Refresh Token
`POST /v1/auth/refresh-tokens`

**Request Body:**
```json
{
  "refreshToken": "..."
}
```

## Security Best Practices
- **Always use HTTPS**: Never send credentials or tokens over plain HTTP.
- **Secure Token Storage**: On mobile, use EncryptedSharedPreferences (Android) or Keychain (iOS). On the web, use `HttpOnly` cookies if possible (the API sets these automatically) or secure session storage.
- **Handle 401 Unauthorized**: Implement a global interceptor to handle token expiration and trigger the refresh flow.
