# Authentication (Bearer Token)

The Reg-Sense AI API uses token-based authentication (Bearer Token) over HTTPS to ensure all communication and data transfer remains secure and compliant.

## 1. Acquiring an API Key

API keys are generated via the Reg-Sense AI Customer Portal.

1.  Log into your account.
2.  Navigate to **Settings > API Key Management**.
3.  Click **Generate New Key**.
4.  Specify the required permissions (e.g., `trialdata:ingest`).
5.  The generated key (Token) must be stored securely and treated as a password.

## 2. Using the Bearer Token

The API Key must be passed in the HTTP request header using the `Authorization` scheme.

* **Scheme:** `Bearer`
* **Header Name:** `Authorization`

### Example Header Implementation

```http
Authorization: Bearer [YOUR_GENERATED_API_KEY]