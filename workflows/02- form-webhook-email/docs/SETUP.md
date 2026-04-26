# 🚀 Setup Steps to Execute This Workflow

## 1. Import workflow into n8n

* Open n8n  
* Click **Import workflow**  
* Paste JSON or upload file  
* Save workflow  

---

## 2. Configure SMTP credentials ⭐ (IMPORTANT)

Go to:

👉 **Credentials -> New -> SMTP**

### Gmail setup (recommended)

* **Host:** `smtp.gmail.com`  
* **Port:** `465`  
* **Secure (SSL):** true  
* **User:** your Gmail address  
* **Password:** Gmail **App Password** (NOT normal password)  

---

## 🔐 How to get Gmail App Password ✨

1. Go to Google Account settings  
2. Enable **2-Step Verification**  
3. Search: **App Passwords**  
4. Create one for “Mail”  
5. Copy 16-character password  

---

## 3. Attach SMTP credential ⭐

Open your workflow -> **Send Email node**

👉 Select your SMTP credential in UI  

---

## 4. Setup Webhook ✨

Open **Webhook node** in n8n:

* Method: `POST`  
* Path: `YOUR_WEBHOOK_PATH_HERE`  

👉 Copy **Production URL**

---

## 5. Connect external form (if used) ⭐

If using Google Form / Apps Script:

Replace:

```plaintext
YOUR_WEBHOOK_URL
````

With:

```plaintext
https://your-n8n-webhook-url
```

---

## 6. Email behavior ✨

This workflow will:

* Receive data via webhook
* Extract email from request
* Send automatic response email

---

## ⚡ Final checklist

* SMTP credentials created
* Gmail app password used
* Webhook configured
* Email node updated via UI
* Workflow activated

---

## 🚀 What happens when it runs

1. Webhook receives data ⭐
2. n8n processes request
3. Email is extracted dynamically
4. Confirmation email is sent
5. User receives response ✨

---

## Note

This workflow requires a valid webhook trigger source (Google Form, API, or frontend request). SMTP must be configured inside n8n.

---

## 🌐 Google Form Integration (Optional ⭐✨)

### 📋 Step 1: Create Google Form

Add fields:

* Name
* Email
* Contact
* Department

Link it to Google Sheets:
👉 Responses -> **Link to Sheets**

---

### ⚙️ Step 2: Open Apps Script

In Google Sheets:

👉 Extensions -> Apps Script

Paste this code:

```javascript
function onFormSubmit(e) {
  const row = e.values;

  const payload = JSON.stringify({
    name: row[1],
    email: row[2],
    contact: row[3],
    department: row[4]
  });

  UrlFetchApp.fetch("YOUR_N8N_WEBHOOK_URL_HERE", {
    method: "POST",
    contentType: "application/json",
    payload: payload
  });
}
```

---

### 🚀 Step 3: Add Trigger

* Click **Triggers (clock icon)**
* Add Trigger:

  * Function: `onFormSubmit`
  * Event Source: From spreadsheet
  * Event Type: On form submit

Save and authorize ⭐

---

### 🔗 Step 4: Add Webhook URL

Replace:

```
YOUR_N8N_WEBHOOK_URL_HERE
```

With:

```
https://your-n8n-webhook-url
```

---

### ⚡ Step 5: Test Flow

1. Submit Google Form ⭐
2. Apps Script sends data
3. n8n receives webhook
4. Email is sent automatically ✨

---
