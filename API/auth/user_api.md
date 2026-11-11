# User Authentication API Guide

The User Authentication API handles user registration, login, and profile security. All requests require the `x-avci-workspace` header.

## Base URL
`POST /v1/auth`

---

## Endpoints

### Check Email
`POST /v1/auth/check-email`

Checks if an email is already registered in the workspace.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `email` | `string` | Yes | User's email address |

---

### Signup (Register)
`POST /v1/auth/register`

Registers a new user and returns authentication tokens.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `email` | `string` | Yes | Unique email address |
| `password` | `string` | Yes | Min 8 chars, 1 letter, 1 number |
| `name.first` | `string` | Yes | First name |
| `name.last` | `string` | Yes | Last name |
| `contact.mobileNumber` | `array` | Yes | List of phone objects (areaCode, countryCode, phoneNumber) |
| `birthDate` | `date` | No | YYYY-MM-DD |
| `gender` | `string` | No | User gender |

**Response Data:**
```json
{
  "user": {
    "_id": "string",
    "name": { "first": "string", "last": "string" },
    "email": "string",
    "role": "string",
    "workspace": "string"
  },
  "tokens": {
    "access": { "token": "string", "expires": "ISO Date" },
    "refresh": { "token": "string", "expires": "ISO Date" }
  }
}
```

---

### Login
`POST /v1/auth/login`

Authenticates a user and returns tokens.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `email` | `string` | Yes | Registered email |
| `password` | `string` | Yes | User password |

**Response Data:**
Same structure as Signup.

---

### Forgot Password
`POST /v1/auth/forgot-password`

Initiates the password reset process by sending a token or OTP.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `email` | `string` | Yes | Registered email |
| `method` | `string` | No | `email` (default) or `sms` |

---

### Verify OTP
`POST /v1/auth/verify-otp`

Verifies the 6-digit One Time Password (OTP) for password reset or validation.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `email` | `string` | Yes | User's email |
| `otp` | `string` | Yes | 6-digit code |

---

### Resend OTP
`POST /v1/auth/resend-otp`

Resends the verification or reset OTP.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `email` | `string` | Yes | User's email |
| `method` | `string` | No | `email` (default) or `sms` |

---

### Reset Password
`POST /v1/auth/reset-password`

Resets the password using a token.

**Query Parameters:**
- `token`: Reset token (usually from URL)

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `email` | `string` | No | User's email |
| `password` | `string` | Yes | New password |

---

### Verify Email
`GET /v1/auth/verify-email`

Verifies the user's email address using a token.

**Query Parameters:**
- `token`: Verification token

---

### Logout
`POST /v1/auth/logout`

Invalidates the refresh token.

**Request Body:**
| Field | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `refreshToken` | `string` | Yes | Current refresh token |
