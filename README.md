# Clutch 2025 Hiring Test

## Overview

This repository contains the source code for a Vue.js application as part of the Clutch 2025 Hiring Test. The application should display a form for users to input their details, submits the form data to an external API, and then shows a thank you message for 5 seconds before resetting for the next submission.

## Project Setup

Install dependencies:

```bash
npm install
```

Launch the development server with hot-reloading:

```bash
npm run serve
```

For a complete list of available commands, refer to the [package.json](./package.json) file.

## API Integration

The application integrates with an external API to handle form submissions. The API endpoint requires an API key, which should be provided in the endpoint URL. Replace the placeholder `<YOUR_API_KEY_HERE>` with your actual API key, as provided via email.

### API Endpoint

```text
https://dev-api-api.hiring-test.experientialpreview.com/api/lead/<YOUR_API_KEY_HERE>
```

### Example Request

Below is an example of how to submit the form data using cURL:

```bash
curl --location 'https://dev-api-api.hiring-test.experientialpreview.com/api/lead/<YOUR_API_KEY_HERE>' \
--data-raw '{
    "first": "Test",
    "last": "Test",
    "company": "Test",
    "phone": "3135555555",
    "email": "test@test.test"
}'
```

### Request Parameters

| Field   | Type   | Description          | Example          |
| ------- | ------ | -------------------- | ---------------- |
| first   | string | User's first name    | "Test"           |
| last    | string | User's last name     | "Test"           |
| company | string | User's company name  | "Test"           |
| phone   | string | User's phone number  | "3135555555"     |
| email   | string | User's email address | "test@test.test" |

Replace the sample data with actual user input when making a submission. [You can use this tool to view data that has been submitted.](https://dev-fe.hiring-test.experientialpreview.com/)

## Application Flow

1. **Display the Form:** The app shows a form for the user to fill out.
2. **Submit Data:** On submission, the form data is sent to the API endpoint using the provided API key.
3. **Thank You Message:** A thank you message is displayed for 5 seconds after submission.
4. **Repeat Process:** The form resets for the next user submission.
