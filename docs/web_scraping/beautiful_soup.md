# 🍲 Web Scraping with Beautiful Soup

**Beautiful Soup** is a Python library for parsing HTML and XML documents. It’s ideal for beginners and small-to-medium web scraping tasks where you want quick and readable code.

---

## 🌟 Why Use Beautiful Soup?

- Simple and beginner-friendly
- Great for static pages with predictable structure
- Integrates easily with `requests`
- Supports multiple parsers (html.parser, lxml)

---

## 🛠️ Installation

Install Beautiful Soup along with the `requests` library:

```bash
pip install beautifulsoup4 requests
```

---

## 🔍 Basic Example

Let’s scrape quotes from [http://quotes.toscrape.com](#)

```py
import requests
from bs4 import BeautifulSoup

URL = "http://quotes.toscrape.com/"
response = requests.get(URL)

soup = BeautifulSoup(response.text, 'html.parser')

for quote in soup.find_all('div', class_='quote'):
    text = quote.find('span', class_='text').get_text()
    author = quote.find('small', class_='author').get_text()
    tags = [tag.get_text() for tag in quote.find_all('a', class_='tag')]

    print(f"{text} — {author} | Tags: {tags}")
```

---

## 🔧 How It Works

- `requests.get()` fetches the webpage content.
- `BeautifulSoup()` parses the HTML.
- `find()` and `find_all()` are used to locate elements by tag and class.
- `.get_text()` extracts the inner text from an element.

---

## 🧠 Key Features

| Feature                 | Description                                |
| ----------------------- | ------------------------------------------ |
| Tag navigation          | Traverse HTML tags as objects (`soup.div`) |
| Searching by attributes | `find()`, `find_all()`, `select()`         |
| CSS selectors           | Use `.select('div.quote span.text')`       |
| Parser flexibility      | Use `html.parser`, `lxml`, or `html5lib`   |

---

## ✨ Example: Extract All Authors

```py
authors = soup.find_all('small', class_='author')
for author in set(a.get_text() for a in authors):
    print(author)
```

---

## 📦 Exporting Data

You can save data to a CSV file like this:

```py
import csv

with open('quotes.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerow(['Quote', 'Author', 'Tags'])

    for quote in soup.find_all('div', class_='quote'):
        text = quote.find('span', class_='text').get_text()
        author = quote.find('small', class_='author').get_text()
        tags = [tag.get_text() for tag in quote.find_all('a', class_='tag')]
        writer.writerow([text, author, ', '.join(tags)])
```

---

## ✅ When to Use Beautiful Soup

| Scenario                           | Use Beautiful Soup? |
| ---------------------------------- | ------------------- |
| Parsing static HTML pages          | ✅ Yes              |
| Quick one-off scraping scripts     | ✅ Yes              |
| Pages with simple structure        | ✅ Yes              |
| Crawling multiple pages or domains | ❌ Use Scrapy       |
| JavaScript-rendered content        | ❌ Use Selenium     |

---

## ⚠️ Ethics and Best Practices

- Respect the website’s `robots.txt`
- Add delays to avoid overwhelming servers
- Avoid scraping personal/private data
- Review the site's terms of service

---

## 🔗 Resources

- [Official Docs](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
- [Real Python Tutorial](https://realpython.com/beautiful-soup-web-scraper-python/)

---

Beautiful Soup is perfect for getting started with web scraping. It's powerful enough for most everyday scraping tasks and easy to pick up.

Happy scraping! 🥄

---

## Respect `robots.txt` with Beautiful Soup

Let’s fix that by clearly explaining how to respect `robots.txt` **when using Beautiful Soup**, since Beautiful Soup itself doesn't handle this — ==you have to do it manually==.

> ✅ How to Respect `robots.txt` with Beautiful Soup

Unlike **Scrapy**, which has built-in support for handling `robots.txt`, Beautiful Soup is just an HTML parser. So you must manually check whether the site allows scraping before you proceed.

Here’s how you can do that in Python:

---

**📦 Step 1: Install `robotparser` (standard in Python)**

Python has a built-in module for this:

```bash
import urllib.robotparser
from urllib.parse import urlparse
```

---

**🧠 Step 2: Check if Scraping Is Allowed**

Here’s an example that checks whether you’re allowed to scrape a page:

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

# Example usage
url = "http://quotes.toscrape.com/page/1/"
if is_allowed(url):
    print("✅ Allowed to scrape")
else:
    print("🚫 Not allowed to scrape")

```

???+ note "💡 Notes"

    -   `robots.txt` is a voluntary standard, but it's widely respected by ethical scrapers.
    -   Some sites don’t have a `robots.txt` at all — in that case, you may choose to proceed cautiously.
    -   Always identify yourself in your headers if doing heavy scraping.

---

## Proceed Cautiously

Great follow-up! If a site **doesn’t have a** `robots.txt`, it means there are no explicit rules for scraping — which ==isn’t the same as permission==, but also not an outright denial.

So when `robots.txt` is **missing**, the ethical and practical response is to:

1.  Proceed **cautiously and respectfully**
2.  Follow **general good scraping practices** (throttling, not scraping sensitive data, etc.)
3.  Ideally contact the site owner if scraping heavily

---

> 🧪 How to Detect If `robots.txt` Is Missing

You can check if the file exists by making a request and seeing the HTTP status:

```py title="Updated Example"
import requests
from urllib.parse import urlparse
import urllib.robotparser

def is_allowed(url, user_agent='*'):
    parsed = urlparse(url)
    robots_url = f"{parsed.scheme}://{parsed.netloc}/robots.txt"

    try:
        response = requests.get(robots_url, timeout=5)
        if response.status_code == 200:
            rp = urllib.robotparser.RobotFileParser()
            rp.parse(response.text.splitlines())
            return rp.can_fetch(user_agent, url)
        elif response.status_code == 404:
            print("⚠️ robots.txt not found — proceed cautiously.")
            return True  # You decide whether to allow this or not
        else:
            print(f"⚠️ Unexpected response ({response.status_code}) for robots.txt — proceed with caution.")
            return False
    except Exception as e:
        print(f"❌ Error checking robots.txt: {e}")
        return False
```

---

> How to Proceed Cautiously

If `robots.txt` is not found (`404`), and you decide to scrape anyway, follow these best practices:

| Guideline                           | How to Implement in Python              |
| ----------------------------------- | --------------------------------------- |
| Throttle requests                   | Use `time.sleep()` or `asyncio.sleep()` |
| Set custom user-agent               | Use headers with `requests`             |
| Avoid scraping sensitive data       | Only target public, visible info        |
| Don't scrape too many pages at once | Limit page depth and pagination         |
| Cache data when possible            | Store locally to reduce repeat scraping |
| Monitor for changes in access rules | Check `robots.txt` before each session  |

```py title="Example"
import time
headers = {
    "User-Agent": "Mozilla/5.0 (compatible; MyScraper/1.0)"
}

response = requests.get("https://example.com", headers=headers)
time.sleep(2)  # wait 2 seconds between requests
```

---

> 📝 Optional: Log That You Proceeded Cautiously

This is useful for auditability in your scraper:

```py
if response.status_code == 404:
    print("robots.txt missing. Proceeding cautiously with delays and limited scraping.")
```

---

> ⚠️ Final Note

Just because `robots.txt` is missing doesn't mean you're free to scrape anything — especially:

- Login-required or private pages
- Sites with terms of service prohibiting bots
- Pages with copyright-protected content

When in doubt, **limit what you collect** and **contact the site owner** if it's a long-term or heavy-use project.
