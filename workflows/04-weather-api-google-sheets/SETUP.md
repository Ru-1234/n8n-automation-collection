# Weather API to Google Sheets — n8n Workflow

This n8n workflow fetches weather data from the OpenWeatherMap API every hour and appends it to a Google Sheet automatically.

## Workflow Overview

```text
Schedule Trigger
   ↓
HTTP Request (Weather API)
   ↓
Set Node (Extract Fields)
   ↓
Google Sheets (Append Row)
```

---

# Requirements

* n8n installed
* Google account
* OpenWeatherMap API key

---

# Step 1 — Create a Google Sheet

Create a new Google Sheet with these columns:

| city | temp | weather | timestamp |
| ---- | ---- | ------- | --------- |

Copy the Spreadsheet ID from the URL:

```text
https://docs.google.com/spreadsheets/d/SPREADSHEET_ID/edit
```

---

# Step 2 — Get OpenWeatherMap API Key

Go to:

[OpenWeatherMap API](https://openweathermap.org/api?utm_source=chatgpt.com)

Then:

1. Create an account
2. Open the API Keys section
3. Copy your API key

---

# Step 3 — Configure Google Sheets OAuth in n8n

1. Open Google Cloud Console
2. Enable the Google Sheets API
3. Create OAuth2 credentials
4. Add this redirect URI:

```text
http://localhost:5678/rest/oauth2-credential/callback
```

5. Connect the credentials inside n8n

---

# Step 4 — Import the Workflow

1. Open n8n
2. Import `workflow.json`
3. Replace:

```text
YOUR_API_KEY
```

with your OpenWeatherMap API key.

4. Replace:

```text
YOUR_GOOGLE_SHEET_ID
```

with your Google Sheet ID.

5. Select your Google Sheets credentials.

---

# Step 5 — Activate the Workflow

Click:

* Save
* Activate Workflow

The workflow will now fetch weather data automatically every hour.

---

# Notes

* Default city: Islamabad
* Temperature unit: Kelvin (OpenWeatherMap default)
* You can change the city inside the HTTP Request node
