---
name: web-scraper
description: Scrape web content with anti-detection features. Extract data from static and dynamic websites, handle JavaScript-rendered pages, and respect robots.txt. Use when scraping websites, extracting web data, or working with HTML content.
allowed-tools: Bash, Read, Grep, Glob
---

# Web Scraper

Scrape web content from static and dynamic websites with built-in anti-detection features.

## What this Skill does

- Extract data from static HTML pages
- Handle JavaScript-rendered content (SPA websites)
- Respect robots.txt and implement rate limiting
- Support for CSS selectors and XPath queries
- Proxy support for anonymous scraping
- Handle authentication and sessions
- Export data to JSON, CSV, or XML formats
- Batch scraping with pagination support

## Requirements

Install required packages:
```bash
pip install requests beautifulsoup4 lxml selenium
```

For advanced features (JavaScript rendering):
```bash
pip install playwright
playwright install chromium
```

## How to use

### Basic HTML scraping
```python
import requests
from bs4 import BeautifulSoup

url = "https://example.com"
response = requests.get(url)
soup = BeautifulSoup(response.content, 'html.parser')

# Extract specific elements
title = soup.find('title').text
links = [a['href'] for a in soup.find_all('a', href=True)]
```

### Handle JavaScript content
```python
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.chromium.launch()
    page = browser.new_page()
    page.goto('https://example.com')
    content = page.content()
    browser.close()
```

### Extract data with CSS selectors
```python
from bs4 import BeautifulSoup
import requests

response = requests.get('https://example.com')
soup = BeautifulSoup(response.content, 'html.parser')

# Extract product cards
products = soup.select('.product-item')
for product in products:
    name = product.select_one('.product-title').text
    price = product.select_one('.product-price').text
    print(f"{name}: {price}")
```

### Batch scraping with pagination
```python
import requests
from bs4 import BeautifulSoup

for page in range(1, 11):  # Pages 1-10
    url = f"https://example.com/products?page={page}"
    response = requests.get(url)
    soup = BeautifulSoup(response.content, 'html.parser')
    # Process page content
```

## Examples

When to use this Skill:
- "Scrape product listings from this e-commerce site"
- "Extract news articles from this blog"
- "Get data from a website with pagination"
- "Scrape a JavaScript-heavy SPA website"
- "Extract structured data from HTML tables"
- "Scrape and export data to CSV"

## Best Practices

- Always check robots.txt first: `https://site.com/robots.txt`
- Use rate limiting to avoid overwhelming servers
- Rotate user agents and proxies for large-scale scraping
- Store data incrementally to avoid losing progress
- Handle errors gracefully (timeouts, 404s, etc.)

## Tips

- For dynamic content, use Selenium or Playwright
- For large datasets, implement checkpointing
- Cache responses to avoid repeated requests
- Respect copyright and terms of service
