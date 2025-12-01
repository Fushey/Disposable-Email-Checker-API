# 🛡️ Disposable Email Checker API  
Detect temporary / disposable emails (Mailinator, 10MinuteMail, GuerrillaMail, Temp-Mail, etc.) in real time using a simple REST API.

> One request → one boolean → block fake signups.

---

## 🚀 Overview

Disposable emails are frequently used for:
- Fake signups
- Promo / referral abuse
- Trial farming
- Spam account creation
- Destroying deliverability (bounces → spam folder)

This API instantly detects whether an email belongs to a disposable provider — so you can block them **before** the account is created.

---

## 🔗 API Endpoints

| Region      | Base URL |
|-------------|----------|
| 🇪🇺 Europe   | `https://tempmailchecker.com` |
| 🇺🇸 US       | `https://us.tempmailchecker.com` |
| 🇸🇬 Asia     | `https://asia.tempmailchecker.com` |

All endpoints share the same database & API key.  
Pick the closest region for lowest latency.

---

## 🔑 Authentication

Send your API key in the request header:

```
X-API-Key: YOUR_API_KEY
```

👉 **Get your free API key:** https://tempmailchecker.com

---

## ✔ Check if an Email is Disposable  
### `GET /check`

**Query parameters**
| Name | Required | Description |
|-------|----------|-------------|
| `email` | optional | Full email address |
| `domain` | optional | Email domain only |

> Use either `email` OR `domain`. The API extracts the domain automatically.

**Example request**
```bash
curl "https://tempmailchecker.com/check?email=user@mailinator.com" \
  -H "X-API-Key: YOUR_API_KEY"
```

**Response**
```json
{ "temp": true }
```

---

## 📊 Check API Usage  
### `GET /usage?key=YOUR_API_KEY`

```bash
curl "https://tempmailchecker.com/usage?key=YOUR_API_KEY"
```

Response:
```json
{
  "usage_today": 37,
  "limit": 100,
  "reset": "midnight UTC"
}
```

---

## 🧩 Code Examples

### JavaScript / Node / Next.js
```js
const res = await fetch(
  "https://tempmailchecker.com/check?email=user@mailinator.com",
  { headers: { "X-API-Key": YOUR_API_KEY } }
);
console.log(await res.json());
```

### Python
```python
import requests
r = requests.get(
    "https://tempmailchecker.com/check",
    params={"email": "user@mailinator.com"},
    headers={"X-API-Key": YOUR_API_KEY}
)
print(r.json())
```

### PHP
```php
$ch = curl_init("https://tempmailchecker.com/check?email=user@mailinator.com");
curl_setopt($ch, CURLOPT_HTTPHEADER, ["X-API-Key: YOUR_API_KEY"]);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
echo curl_exec($ch);
```

---

## 📌 Why Block Disposable Emails?

Allowing temporary inboxes leads to:

| Problem | Result |
|--------|--------|
| Fake signups | inflated MAU / wasted server resources |
| Referral & promo abuse | coupon / trial farming |
| Bounce spikes | email domain reputation destruction |
| “Lost password” support tickets | inbox expires → cannot receive reset emails |
| Zero revenue | throwaway emails almost never convert to paying users |

---

## ⏳ Rate Limits

| Plan | Requests / Day |
|------|----------------|
| Free | 100 |

Exceeding returns **HTTP 429**
```json
{
  "error": "Rate limit exceeded",
  "limit": 100,
  "used": 100
}
```

---

## 🧠 Ideal Integration Points

Block disposable emails at:

| Place | Purpose |
|-------|---------|
| User signup | stop fake accounts |
| Email change | prevent switching to throwaway |
| Newsletter opt-ins | protect deliverability |
| Waitlists | improve launch quality |
| Coupon + referral forms | prevent abuse |

---

## 🌐 Website & Documentation

📌 Landing page → https://tempmailchecker.com  
📌 API docs → https://tempmailchecker.com/docs  
📌 Code examples → https://tempmailchecker.com/code-examples  

---

## ⭐ Support the Project

If this API helps your project, consider starring the repository — it helps visibility and ranking on GitHub.

```
⭐ Star → helps more devs discover it
```

You can also open issues or feature requests through GitHub.

---

## 📄 License

MIT License — free for personal and commercial use.

```
Copyright (c) 2025
```

---

### 🔥 TL;DR

> **Stop fake signups in 60 seconds.**  
> `true` = disposable email → block  
> `false` = real email → allow  
> Start free → https://tempmailchecker.com

```
One API request. One boolean. Zero fake users.
```
