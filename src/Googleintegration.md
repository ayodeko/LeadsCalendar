# Google Calendar API Integration

## Introduction

Integrate Google Calendar API to allow LeadsCalendar to manage user events. This guide details the essential steps for integration.

## Step 1: Enable API and Create Credentials

- **API Console**: Access your Google Cloud Console and select the project for LeadsCalendar.
- **Enable API**: In the "Library" section, find and enable the "Google Calendar API."
- **Credentials**: Navigate to "Credentials" in the API & Services section.
  - Click on "Create Credentials" and select "OAuth client ID".
  - Configure your OAuth consent screen and take note of the resulting Client ID and Client Secret.

## Step 2: Authenticate and Obtain Tokens

- **OAuth Consent**: Direct users to Google's OAuth 2.0 consent page.
- **Exchange Code for Token**: Use the authorization code returned to exchange for an access token.

POST /token HTTP/1.1
Host: oauth2.googleapis.com
Content-Type: application/x-www-form-urlencoded

code=AUTHORIZATION_CODE&client_id=YOUR_CLIENT_ID&client_secret=YOUR_CLIENT_SECRET&redirect_uri=YOUR_REDIRECT_URI&grant_type=authorization_code


**Note**: Replace `AUTHORIZATION_CODE`, `YOUR_CLIENT_ID`, `YOUR_CLIENT_SECRET`, and `YOUR_REDIRECT_URI` with actual values.

## Step 3: Create Events

- **Create Event Request**: Send a POST request to Google Calendar's `events` endpoint with event details.

POST /calendars/primary/events HTTP/1.1
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json
Host: www.googleapis.com

{
"summary": "Event Summary",
"location": "Event Location",
"description": "Event Description",
"start": {
"dateTime": "2024-01-01T10:00:00-07:00"
},
"end": {
"dateTime": "2024-01-01T11:00:00-07:00"
}
}


**Note**: Include a valid `YOUR_ACCESS_TOKEN` and adjust event details as needed.

## Step 4: Handle API Responses

- **Success and Errors**: Handle API responses, success indicates a `200 OK` status with event details. Error responses should be caught and handled according to HTTP status codes and error messages.

**Note**: Implement error handling for HTTP status codes like `401 Unauthorized` and `400 Bad Request`.

## Conclusion

Following these steps ensures a successful integration of Google Calendar with LeadsCalendar, allowing event management upon payment confirmation.