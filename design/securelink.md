🔒 Understanding Secure Links (Signed URLs)
===========================================

When building apps, you might've noticed that **Django** or similar frameworks don't actually serve user content (like PDFs, images, videos, audio, etc.) directly --- not because they can't, but because it's not efficient or scalable.

Instead, these tasks are delegated to **reverse proxies** or **storage services** --- like **NGINX**, **AWS S3**, **Cloudflare R2**, or **GCP Storage** --- which are optimized for high-performance file delivery.

* * * * *

### ⚠️ The Catch

Your application knows the user --- who's logged in, who owns what file, and who should have access (and for how long).\
So, how do you let these delivery systems serve content securely **without bypassing your app's control**?

That's where **signed URLs (secure links)** come in.\
They allow your app to generate a **temporary, verifiable link** that only authorized users can access --- often with **expiry time**, **IP restriction**, or other conditions.

* * * * *

💡 Common Use Cases
-------------------

-   Private file or media delivery via **NGINX** (secure link CDN setup)

-   Temporary document or report downloads in web apps

-   Secure access to cloud-stored files (**AWS S3**, **GCP**, **Azure**)

-   One-time access links for password reset or verification

-   Authenticated video streaming

* * * * *

🧩 SecureLink
-------------

**SecureLink** is a small side project I built to help others understand how signed URLs actually work under the hood (tested for **NGINX**).\
There are already many production-grade implementations out there, but this project is intentionally simple --- designed to be **educational** and **reusable**.

It's a lightweight reference for generating and verifying **expirable signed URLs** in Python.

* * * * *

### 🔧 How to Use

You can use SecureLink in two ways:

#### 📦 Library Mode

Import as a Python package to generate secure URLs directly from your app:
```
pip install securelink
```

🌍 API Mode

Run it as a FastAPI microservice, so all your services can use a common API for link generation:
```
pip install securelink[api]
```

🔗 [github](https://github.com/muscodev/secure-link-generator)
📦 [pypy](https://pypi.org/project/securelink)