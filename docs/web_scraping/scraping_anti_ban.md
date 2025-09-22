# 🛡️ Avoiding Bans While Scraping

Web scraping can trigger anti-bot protections if you're not careful. To avoid getting blocked or banned, follow these best practices:

---

## 🧠 Why You Might Get Blocked

Websites often use techniques to detect and block bots:

- Too many requests in a short time
- Using default headers (like Python's `requests`)
- Not following `robots.txt`
- Ignoring JavaScript rendering
- Accessing login-restricted or sensitive areas

---

## ✅ Key Anti-Ban Techniques

### 1. 🔁 Rotate User-Agent Headers

User-Agent strings identify the browser/device making the request. Using the same one repeatedly (especially Python's default) is a red flag.

```python
import random

user_agents = [
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 Chrome/116.0.0.0 Safari/537.36",
    "Mozilla/5.0 (Macintosh; Intel Mac OS X 13_3) AppleWebKit/605.1.15 Version/16.1 Safari/605.1.15",
    "Mozilla/5.0 (X11; Linux x86_64) Firefox/117.0",
    # Add more real user-agents
]

headers = {
    "User-Agent": random.choice(user_agents)
}
```

---

### 2. ⏳ Use Random Delays Between Requests

Fixed delays are predictable. Random delays simulate human browsing behavior.

```py
import time
import random

delay = random.uniform(2, 5)
print(f"Sleeping for {delay:.2f} seconds")
time.sleep(delay)
```

Use after every request or interaction.

---

### 🧪 Combined Example with `requests` + `BeautifulSoup`

```py
import time
import random
import requests
from bs4 import BeautifulSoup

urls = ["https://example.com/page1", "https://example.com/page2"]

user_agents = [
    "Mozilla/5.0 ...",
    "Mozilla/5.0 ...",
]

for url in urls:
    headers = {
        "User-Agent": random.choice(user_agents)
    }

    response = requests.get(url, headers=headers)
    soup = BeautifulSoup(response.text, 'html.parser')

    # Parse content here...

    delay = random.uniform(2, 4)
    time.sleep(delay)
```

---

## 🧪 Example with Selenium

You can also rotate user agents in Selenium:

```py
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
import random

user_agents = [
    "Mozilla/5.0 ...",
    "Mozilla/5.0 ..."
]

options = Options()
options.add_argument(f"user-agent={random.choice(user_agents)}")
options.headless = True

driver = webdriver.Chrome(options=options)
driver.get("https://example.com")
```

Add delays with `time.sleep()` between actions as needed.

---

## 🧾 Other Useful Techniques

| Technique               | Description                                   |
| ----------------------- | --------------------------------------------- |
| ✅ Respect `robots.txt` | Always check if scraping is allowed           |
| 🌐 Use rotating proxies | Helps bypass IP-based rate limits and bans    |
| 🔁 Retry logic          | Use `try/except` blocks to handle failures    |
| 🛑 Rate limiting        | Never hammer a site — use exponential backoff |
| 🧑‍💻 Custom headers       | Mimic browser behavior more closely           |

---

## ⚠️ Things to Avoid

- ❌ Scraping login-required pages without permission
- ❌ Running multiple threads with no throttling
- ❌ Using scraping tools without setting headers
- ❌ Ignoring `robots.txt` or site TOS

---

## 📦 Libraries That Help

| Tool                      | Use Case                        |
| ------------------------- | ------------------------------- |
| `fake-useragent`          | Random browser-like User-Agents |
| `requests`                | Simple static HTML scraping     |
| `Selenium`                | Dynamic content scraping        |
| `cfscrape`                | Bypass Cloudflare protection    |
| `scrapy-rotating-proxies` | Proxy rotation in Scrapy        |

---

## 🔐 Always Scrape Responsibly

Even if you can scrape a site, always ask:

- **Should you?**
- **What data are you collecting?**
- **Are you putting unnecessary load on the server?**

Always identify yourself in your user agent or headers if you're doing heavy scraping for research or business.

---

## 🐍 Scrapy: Avoiding Bans & Being Polite

Scrapy includes built-in tools and middlewares to help you scrape responsibly and avoid getting banned.

**1. Download Delay & Randomization**

In your `settings.py`:

```py
DOWNLOAD_DELAY = 2
RANDOMIZE_DOWNLOAD_DELAY = True
```

---

**2. Rotate User Agents**

Use the `scrapy-user-agents` middleware:

Install:

```bash
pip install scrapy-user-agents
```

Enable in `settings.py`:

```py
DOWNLOADER_MIDDLEWARES = {
    'scrapy_user_agents.middlewares.RandomUserAgentMiddleware': 400,
}
```

Alternatively, write a custom middleware to rotate user agents.

---

**3. Enable AutoThrottle**

AutoThrottle adjusts crawling speed based on server load.

```py
AUTOTHROTTLE_ENABLED = True
AUTOTHROTTLE_START_DELAY = 1
AUTOTHROTTLE_MAX_DELAY = 10
AUTOTHROTTLE_TARGET_CONCURRENCY = 1.0
```

**4. Respect `robots.txt`**

Make sure this is enabled:

```py
ROBOTSTXT_OBEY = True
```

**5. Retry & Proxy Middleware**

Enable retrying failed requests:

```py
RETRY_ENABLED = True
RETRY_TIMES = 5
```

Use rotating proxies if needed.

---

**Example `settings.py` snippet**

```py
BOT_NAME = 'myproject'

SPIDER_MODULES = ['myproject.spiders']
NEWSPIDER_MODULE = 'myproject.spiders'

ROBOTSTXT_OBEY = True

DOWNLOAD_DELAY = 2
RANDOMIZE_DOWNLOAD_DELAY = True

AUTOTHROTTLE_ENABLED = True
AUTOTHROTTLE_START_DELAY = 1
AUTOTHROTTLE_MAX_DELAY = 10
AUTOTHROTTLE_TARGET_CONCURRENCY = 1.0

RETRY_ENABLED = True
RETRY_TIMES = 5

DOWNLOADER_MIDDLEWARES = {
    'scrapy_user_agents.middlewares.RandomUserAgentMiddleware': 400,
    'scrapy.downloadermiddlewares.retry.RetryMiddleware': 550,
}
```

---

## Resources

- [User-Agent List](https://developers.whatismybrowser.com/useragents/explore/)
- [Python fake-useragent](https://pypi.org/project/fake-useragent/)
- [Selenium Docs](https://www.selenium.dev/documentation/)
- [Scrapy Settings](https://docs.scrapy.org/en/latest/topics/settings.html)

---

Scrape smart. Scrape safe. Scrape ethically. 🕵️‍♂️
