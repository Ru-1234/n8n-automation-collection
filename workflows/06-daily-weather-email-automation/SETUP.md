# n8n Weather Notification Bot

A simple automation workflow built in n8n that sends daily weather updates via Gmail.

---

## Features
- Daily scheduled weather updates (6 AM)
- Multiple city support
- Weather condition decoding
- Email notifications via Gmail
- Powered by Open-Meteo API

---

## ⚙️ Setup Guide

### 1. Import Workflow
- Open n8n
- Click **Import Workflow**
- Paste JSON file from this repo

---

### 2. Add Gmail Credentials
- Go to **Credentials → Gmail OAuth2**
- Connect your Google account
- Select it inside the "Send Email" node

---

### 3. Set Your Email
Replace:
YOUR_EMAIL_HERE with your actual email.

---

### 4. Set Your Cities
Replace:


YOUR_LATITUDE, 
YOUR_LONGITUDE


You can get coordinates from Google Maps.

---

## How It Works
1. Workflow triggers at 6 AM
2. Fetches weather from Open-Meteo API
3. Formats message using JavaScript
4. Sends email via Gmail node

---

## 📦 Tech Stack
- n8n
- Open-Meteo API
- Gmail API

---

## ⭐ Future Ideas
- Telegram/Whatsapp alerts
- Weather alerts (rain/snow warnings)
- Multi-user support

---

## 📄 License
This project is licensed under the MIT License.
