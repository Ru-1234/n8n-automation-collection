# Workflow #05 — Inactive Users Reminder System

## Overview

This workflow runs automatically every night at 2 AM. It finds users who haven’t logged in for 90+ days, sends them a reminder email, and updates their status so they don’t get contacted again.

---

## Workflow Logic

```text id="w5flow"
Schedule Trigger
   ↓
MySQL (Find inactive users)
   ↓
IF (users found?)
   ↓
Send Email
   ↓
MySQL (Update status to notified)
```

---

## Step 1 — Schedule Trigger

* Add **Schedule Trigger**
* Set: Every Day → 2:00 AM

---

## Step 2 — MySQL (Find Inactive Users)

Add **MySQL → Execute Query**

```sql id="w5sql1"
SELECT id, email, name
FROM users
WHERE last_login < DATE_SUB(NOW(), INTERVAL 90 DAY)
AND status = 'active';
```

---

## Step 3 — IF Node

Condition:

* Value 1: `{{ $input.all().length }}`
* Operator: Greater than
* Value 2: `0`

👉 Only continue if inactive users exist.

---

## Step 4 — Send Email Node

Configure Email:

* To: `{{ $json.email }}`
* Subject: We miss you!
* Body:

```text id="w5mail"
Hi {{ $json.name }},

We noticed you haven't logged in for a while.
Come back and check what's new!
```

⚠️ Enable:

* Process each item individually

---

## Step 5 — MySQL Update Node

```sql id="w5sql2"
UPDATE users
SET status = 'notified'
WHERE id = {{ $json.id }};
```

---

## Notes

* Prevents duplicate emails using `status = notified`
* Runs fully automatically every day
* Works best when email node processes items one by one
* Always test SQL query before activating workflow

---
