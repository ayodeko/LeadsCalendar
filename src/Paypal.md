# PayPal REST API Integration

## Introduction

Integrate PayPal REST APIs to process payments in the LeadsCalendar app. Utilize client IDs and secrets for authentication and use OAuth 2.0 to obtain access tokens for API calls.

## Step 1: Get Client ID and Client Secret

- **Client ID**: Unique identifier for your app required for payment buttons and credit card processing.
- **Client Secret**: Authenticates the Client ID and is exchanged for an access token.

### Obtaining Credentials:

1. Log in to the [PayPal Developer Dashboard](https://developer.paypal.com/).
2. Navigate to **Apps & Credentials**.
3. Use the existing Default Application or create a new one.
4. Copy the provided Client ID and Client Secret.

## Step 2: Get Access Token

Exchange your client ID and client secret for an access token using the following cURL command:

curl -v -X POST "https://api-m.sandbox.paypal.com/v1/oauth2/token"
-u "CLIENT_ID:CLIENT_SECRET"
-H "Content-Type: application/x-www-form-urlencoded"
-d "grant_type=client_credentials"


**Note**: Replace `CLIENT_ID` and `CLIENT_SECRET` with your actual values. Important: Encode `CLIENT_ID:CLIENT_SECRET` in Base64 before sending it.

### Sample Response

A successful response will return an access token, its type, and the expiration time:

{
"scope": "...",
"access_token": "Access-Token",
"token_type": "Bearer",
"app_id": "APP-ID",
"expires_in": 31668,
"nonce": "Nonce-Value"
}


## Step 3: Make API Calls

With the access token, you can make API calls. Include the access token in the authorization header of your HTTP requests:

-H "Authorization: Bearer ACCESS-TOKEN"



**Note**: Replace `ACCESS-TOKEN` with your actual access token. When the access token expires, call the `/v1/oauth2/token` endpoint again to get a new one.

## Step 4: Sandbox Testing

Test your integrations in the PayPal sandbox environment. 

### Getting Sandbox Account Credentials:

1. Log into the [Developer Dashboard](https://developer.paypal.com/).
2. Select **Sandbox** > **Accounts** and choose the account you want to use.
3. Use the account credentials to simulate transactions and validate your API calls.

Ensure to test thoroughly before going live with your integrations.

## Conclusion

Following these steps ensures that your LeadsCalendar app can securely process payments through PayPal, providing a complete experience from event creation to payment processing.