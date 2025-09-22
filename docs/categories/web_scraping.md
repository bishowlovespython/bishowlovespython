# Web Scraping & Crawling with Python

Python is widely used for extracting data from websites, automating data collection, and building web crawlers. This category explores tools and techniques for web scraping, with a focus on the popular framework **Scrapy**.

---

## What is Web Scraping?

Web scraping is the process of programmatically retrieving information from websites. It helps gather data from online sources that may not provide APIs or structured data feeds.

Common use cases:

- Price monitoring for e-commerce
- Market research and competitive analysis
- Content aggregation and news monitoring
- Data collection for research and analytics

---

## Introduction to Scrapy

[Scrapy](https://scrapy.org/) is a powerful and flexible Python framework designed specifically for web scraping and crawling. It provides all the tools needed to extract structured data from websites quickly and efficiently.

### Key Features of Scrapy

- Built-in support for crawling multiple pages automatically
- Easy-to-use selectors to extract data (XPath, CSS)
- Middleware and pipelines for data processing and storage
- Support for handling cookies, sessions, and login
- Extensible and customizable architecture

---

## Basic Scrapy Workflow

1. **Define a Spider:** A class that specifies how to crawl a website and extract data.
2. **Send Requests:** Scrapy automatically sends HTTP requests to the target URLs.
3. **Parse Responses:** Extract information using selectors in the spider’s `parse` method.
4. **Store Data:** Save scraped data in formats like JSON, CSV, or databases via pipelines.

---

## Example Spider

```python
import scrapy

class QuotesSpider(scrapy.Spider):
    name = "quotes"
    start_urls = [
        'http://quotes.toscrape.com/page/1/',
    ]

    def parse(self, response):
        for quote in response.css('div.quote'):
            yield {
                'text': quote.css('span.text::text').get(),
                'author': quote.css('small.author::text').get(),
                'tags': quote.css('div.tags a.tag::text').getall(),
            }

        next_page = response.css('li.next a::attr(href)').get()
        if next_page is not None:
            yield response.follow(next_page, self.parse)
```

---

## Other Popular Web Scraping Tools in Python

- **Beautiful Soup**: Easy-to-use library for parsing HTML and XML.
- **Requests**: Simplifies HTTP requests.
- **Selenium**: Automates browsers for scraping JavaScript-heavy sites.

---

## Ethics and Legal Considerations

- Always check a website’s `robots.txt` and terms of service.
- Avoid overloading servers with rapid requests.
- Use scraping responsibly and respect copyright laws.
