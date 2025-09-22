# 🕷️ Scrapy Tutorial

**Scrapy** is a fast, open-source web crawling and scraping framework written in Python. It allows you to extract structured data from websites and is ideal for building large-scale web scrapers.

---

## 🚀 Why Use Scrapy?

- Asynchronous and high-performance
- Handles crawling, scraping, and data pipelines
- Supports retries, throttling, and logging out of the box
- Can export data to JSON, CSV, XML, or databases

---

## 🛠️ Installation

Install Scrapy using pip:

```bash
pip install scrapy
```

To verify:

```bash
scrapy --version
```

---

## 📁 Creating a Scrapy Project

```bash
scrapy startproject quotes_scraper
cd quotes_scraper
```

This creates the following structure:

```
quotes_scraper/
├── scrapy.cfg
└── quotes_scraper/
    ├── __init__.py
    ├── items.py
    ├── middlewares.py
    ├── pipelines.py
    ├── settings.py
    └── spiders/
```

---

## 🧠 Writing Your First Spider

Create a file in `spiders/` called `quotes_spider.py`:

```py
import scrapy

class QuotesSpider(scrapy.Spider):
    name = "quotes"
    start_urls = ['http://quotes.toscrape.com/']

    def parse(self, response):
        for quote in response.css("div.quote"):
            yield {
                'text': quote.css("span.text::text").get(),
                'author': quote.css("small.author::text").get(),
                'tags': quote.css("div.tags a.tag::text").getall(),
            }

        next_page = response.css("li.next a::attr(href)").get()
        if next_page:
            yield response.follow(next_page, self.parse)
```

---

## ▶️ Running the Spider

From the root directory of your project:

```bash
scrapy crawl quotes
```

---

## 📤 Exporting Data

You can save the scraped data to a file like this:

```bash
scrapy crawl quotes -O quotes.json
scrapy crawl quotes -O quotes.csv
```

---

## 🧱 Scrapy Project Structure Overview

- `items.py` – Define data models
- `pipelines.py` – Clean/process data
- `middlewares.py` – Modify requests/responses
- `settings.py` – Configuration (user agents, delays, throttling, pipelines)

---

## 🧩 Useful Features

- **Request throttling**: Respect site load using `DOWNLOAD_DELAY` and `AUTOTHROTTLE`.
- **User-Agent spoofing**: Pretend to be a real browser.
- **Login support**: Handle login forms using `FormRequest`.
- **Middleware**: Customize request/response behavior globally.

---

## ⚠️ Tips & Ethics

- Respect `robots.txt`
- Don't hammer servers — use delays and rate limits
- Never scrape private or copyrighted content without permission

---

## 📚 Learn More

- Official Docs: [https://docs.scrapy.org](https://docs.scrapy.org)
- Scrapy FAQ: [https://docs.scrapy.org/en/latest/faq.html](https://docs.scrapy.org/en/latest/faq.html)

---

Ready to level up your scraping game? Try building spiders that:

- Login and maintain sessions
- Follow multiple link levels
- Scrape multiple websites in one project

Happy crawling! 🕸️
