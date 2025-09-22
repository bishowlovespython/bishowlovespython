---
draft: false
tags: [Beautiful Soup]
date: 2025-09-22
---

# 🤖 How to Respect `robots.txt` with Beautiful Soup

Unlike Scrapy, Beautiful Soup doesn't handle robots.txt rules automatically. To respect them, use Python’s built-in `robotparser` module:

<!-- more -->

```python
import urllib.robotparser
from urllib.parse import urlparse

def is_allowed(url, user_agent='*'):
    parsed = urlparse(url)
    base_url = f"{parsed.scheme}://{parsed.netloc}/robots.txt"

    rp = urllib.robotparser.RobotFileParser()
    rp.set_url(base_url)
    rp.read()

    return rp.can_fetch(user_agent, url)

# Example usage
url = "http://quotes.toscrape.com/page/1/"
if is_allowed(url):
    print("✅ Allowed to scrape")
else:
    print("🚫 Not allowed to scrape")
```

> ✅ Always check `robots.txt` before scraping a website to stay ethical and avoid legal issues.
