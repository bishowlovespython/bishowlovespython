# 🤖 Automating Scrapy: Running Scrapy Programmatically in Your Projects

Scrapy is a powerful framework primarily designed to be run from the command line. But what if you want to integrate Scrapy spiders into your Python projects and run them without manually triggering the command? This guide will show you how to automate Scrapy runs programmatically.

!!! question "**how to integrate and run Scrapy projects programmatically without manual triggering**, so you can automate or embed scraping within larger Python projects."

---

## Why Automate Scrapy?

- Run spiders on-demand from a web app or script
- Schedule scraping tasks with custom logic
- Integrate scraping with data pipelines or workflows
- Avoid manual CLI calls and automate data collection

---

## Running Scrapy Spiders Programmatically

Scrapy provides a `CrawlerProcess` API that lets you run spiders from within Python scripts.

### Basic Example

```python
from scrapy.crawler import CrawlerProcess
from scrapy.utils.project import get_project_settings
from myproject.spiders.example_spider import ExampleSpider

def run_spider():
    # Get Scrapy project settings
    settings = get_project_settings()

    # Create a crawler process with settings
    process = CrawlerProcess(settings)

    # Schedule your spider
    process.crawl(ExampleSpider)

    # Start crawling (blocks until finished)
    process.start()

if __name__ == "__main__":
    run_spider()
```

Replace `myproject.spiders.example_spider` and `ExampleSpider` with your actual project and spider names.

---

## Running Multiple Spiders

You can schedule multiple spiders before calling `start()`:

```py
process.crawl(SpiderOne)
process.crawl(SpiderTwo)
process.start()
```

Scrapy will run them sequentially by default.

---

## Non-Blocking Runs (Using Twisted Reactor)

If you want your script to continue running while Scrapy works in the background, use `CrawlerRunner` with Twisted reactor:

```py
import scrapy
from scrapy.crawler import CrawlerRunner
from twisted.internet import reactor, defer
from myproject.spiders.example_spider import ExampleSpider

runner = CrawlerRunner()

@defer.inlineCallbacks
def crawl():
    yield runner.crawl(ExampleSpider)
    reactor.stop()

crawl()
reactor.run()
```

This allows integration into asynchronous workflows or long-running applications.

---

## Running Scrapy from Other Python Code (Example Use Cases)

- Trigger spiders from Flask/Django web apps based on user actions
- Run spiders as part of data ETL pipelines
- Schedule spiders with `cron` or task queues like Celery by running Python scripts
- Embed scraping functionality into desktop applications

---

## Handling Scrapy Output

- Store scraped items via Scrapy pipelines to databases or files
- Use callbacks in spiders to process data
- Access logs and stats programmatically via signals

---

## Additional Tips

- Use `settings.py` to configure things like download delays, user agents, and auto-throttling to avoid bans when running programmatically.
- Catch and handle errors in your Python wrapper to avoid crashing your whole app.
- For long-running or heavy scraping, consider using Scrapy’s `Job Directory` feature to pause/resume crawls.

---

## Resources

- [Scrapy CrawlerProcess Documentation](https://docs.scrapy.org/en/latest/topics/practices.html#running-scrapy-from-a-script)
- [Twisted Reactor Integration](https://docs.scrapy.org/en/latest/topics/practices.html#running-scrapy-from-a-twisted-application)
- [Scrapy Signals](https://docs.scrapy.org/en/latest/topics/signals.html)

---

Automate your scraping with confidence — no more manual command line triggers needed! 🚀
