# 🚀 Setup Steps to Execute This Workflow

## 1. Import workflow into n8n

* Open n8n
* Click **Import workflow**
* Paste JSON or upload file
* Save workflow

---

## 2. Configure SMTP credentials ⭐ (MOST IMPORTANT)

Go to:

👉 **Credentials → New → SMTP**

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

## 3. Attach credential to node ⭐

Open your workflow → Email node:

👉 Replace:

```json
"REPLACE_WITH_YOUR_SMTP_CREDENTIAL_ID"
```

BUT in UI (important ✨):

* Select your SMTP credential
* Don’t manually edit JSON unless required

---

## 4. Update email addresses ✨

Inside **Send Email node**, change:

```json
"fromEmail": "your-email@gmail.com",
"toEmail": "receiver-email@gmail.com"
```

Replace with:

* your sender email
* receiver email

---

## 5. Set trigger time ⭐ (optional)

Current setup:

```json
triggerAtHour: 14
triggerAtMinute: 5
```

👉 Runs daily at **2:05 PM**

You can change it:

* Morning: 9:00
* Evening: 18:30

---

## 6. Activate workflow 🚀

Top right:

👉 Toggle **Activate Workflow = ON**

Without this:

* workflow will not run automatically

---

## Final checklist ✨

* SMTP credentials created
* Gmail app password used
* Emails updated
* Workflow activated
* Time set

---

# ⚡ What happens when it runs

At scheduled time:

1. Schedule Trigger fires ⭐
2. Email node runs
3. SMTP sends email
4. Receiver gets message:
   → “u can do it 💪✨”

---

## Note ⭐

This workflow requires SMTP setup inside n8n. Credentials are not included for security reasons.

---
