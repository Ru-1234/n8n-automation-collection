# Setup Guide — Weather API to Google Sheets

This workflow automatically fetches weather data every hour using the OpenWeatherMap API and stores it in Google Sheets using :contentReference[oaicite:0]{index=0}.

---

## Workflow Overview

Schedule Trigger  
--> HTTP Request (Weather API)  
--> Set Node (Extract Fields)  
--> Google Sheets (Append Row)

---

## Requirements

- :contentReference[oaicite:1]{index=1} installed
- Google account
- OpenWeatherMap API key

---

## Step 1 — Create Google Sheet

Create a new Google Sheet with these headers:

| city | temp | weather | timestamp |
|------|------|------|------|

Copy the Spreadsheet ID from the URL.

Example:

```txt
https://docs.google.com/spreadsheets/d/SPREADSHEET_ID/edit
```

---

## Step 2 — Create OpenWeatherMap API Key

Go to:

[OpenWeatherMap](https://openweathermap.org/api?utm_source=chatgpt.com)

1. Create account
2. Open API Keys
3. Copy your API key

---

## Step 3 — Configure Google Sheets OAuth

1. Open Google Cloud Console
2. Enable Google Sheets API
3. Create OAuth2 credentials
4. Add redirect URI:

```txt
http://localhost:5678/rest/oauth2-credential/callback
```

5. Connect credentials inside :contentReference[oaicite:3]{index=3}

---

## Step 4 — Import Workflow

1. Open :contentReference[oaicite:4]{index=4}
2. Import `workflow.json`
3. Replace:

```txt
YOUR_API_KEY
```

with your actual API key.

4. Replace:

```txt
YOUR_GOOGLE_SHEET_ID
```

with your spreadsheet ID.

5. Select your Google Sheets credential.

---

## Step 5 — Activate

Click:

- Save
- Activate Workflow

The workflow will now fetch weather data every hour and append it to Google Sheets automatically.

---

## Notes

- Default city is Islamabad
- Temperature is returned in Kelvin by default
- You can change the city in the HTTP Request node

---
