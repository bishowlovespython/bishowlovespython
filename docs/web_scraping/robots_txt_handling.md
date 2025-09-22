# 🤖 Handling `robots.txt` in Web Scraping with Python

When scraping websites, one of the first and most important things you should do is check the site's `robots.txt` file. This file tells web crawlers what parts of the site are allowed or disallowed for automated access.

Beautiful Soup and `requests` **do not automatically respect `robots.txt`**, so you must handle it manually.

---

## 📄 What is `robots.txt`?

`robots.txt` is a simple text file hosted at the root of a domain (e.g., `https://example.com/robots.txt`) that defines rules for web crawlers about what URLs can or cannot be accessed.

**Example:**

```txt
User-agent: *
Disallow: /admin/
Allow: /
```

---

## ✅ How to Check `robots.txt` in Python

Use Python’s built-in `urllib.robotparser` to parse and check access permissions.

**🔧 Example: Basic Usage**

```py
import urllib.robotparser
from urllib.parse import urlparse

def is_allowed(url, user_agent='*'):
    parsed = urlparse(url)
    base_url = f"{parsed.scheme}://{parsed.netloc}/robots.txt"

    rp = urllib.robotparser.RobotFileParser()
    rp.set_url(base_url)
    rp.read()

    return rp.can_fetch(user_agent, url)

# Usage
url = "http://quotes.toscrape.com/page/1/"
if is_allowed(url):
    print("✅ Allowed to scrape.")
else:
    print("🚫 Not allowed to scrape.")
```

---

## 🧪 What if `robots.txt` is Missing?

Some websites don’t have a `robots.txt` at all, or it may return a `404 Not Found`. In that case, there are **no explicit rules**—but it does **not mean free access**.

## 🧠 Proceed Cautiously

You can detect this case and make a judgment call:

```py
import requests

def check_robots_txt(url):
    parsed = urlparse(url)
    robots_url = f"{parsed.scheme}://{parsed.netloc}/robots.txt"

    try:
        response = requests.get(robots_url, timeout=5)
        if response.status_code == 200:
            print("✅ robots.txt found.")
            return response.text
        elif response.status_code == 404:
            print("⚠️ robots.txt not found — proceed cautiously.")
            return None
        else:
            print(f"⚠️ Unexpected status {response.status_code}.")
            return None
    except Exception as e:
        print(f"❌ Error fetching robots.txt: {e}")
        return None
```

---

## 🧱 Ethical Scraping Practices

Even when allowed by `robots.txt`, you should follow best practices to avoid overwhelming servers or violating terms of service.

| Practice                   | How to Implement                      |
| -------------------------- | ------------------------------------- |
| Respect `robots.txt`       | Always check before scraping          |
| Add request delays         | `time.sleep(1-5)` between requests    |
| Identify yourself          | Use a custom `User-Agent` string      |
| Avoid login-protected data | Only scrape publicly accessible info  |
| Limit data collected       | Don't scrape entire sites blindly     |
| Cache scraped data         | Prevent repeated hits on the same URL |

**🧾 Example with Headers & Delay**

```py
import time
import requests

headers = {
    "User-Agent": "MyScraperBot/1.0 (contact@example.com)"
}

response = requests.get("http://quotes.toscrape.com", headers=headers)
time.sleep(2)  # wait 2 seconds before the next request
```

---

## ❓ Can I Ignore `robots.txt`?

Technically, yes — Python will not stop you — but:

- **Ethically, you shouldn't**.
- **Legally**, scraping protected or copyrighted content may expose you to legal consequences.
- Many websites track and block bad bots.

⚠️ Always respect the site's terms of use.

---

## 🔗 Resources

- [Wikipedia: Robots Exclusion Standard](https://en.wikipedia.org/wiki/Robots_exclusion_standard)
- [Google’s Guide to robots.txt](https://developers.google.com/search/docs/crawling-indexing/robots/intro)
- [urllib.robotparser Docs](https://docs.python.org/3/library/urllib.robotparser.html)

---

## ✅ Summary

| Situation                     | Action                              |
| ----------------------------- | ----------------------------------- |
| `robots.txt` disallows access | ❌ Don’t scrape                     |
| `robots.txt` allows access    | ✅ You can scrape                   |
| `robots.txt` is missing       | ⚠️ Proceed cautiously and ethically |

Before you scrape, check first. Scraping responsibly helps keep the web healthy and open for everyone.
