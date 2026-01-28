Here is a clean, professionally formatted version of your README. I’ve added a clearer structure, code blocks, and a touch of visual hierarchy to make it more readable for other developers.

---

# Scrapy Web Scraper with MongoDB

This project is a high-performance Python web scraper built with **Scrapy**. It is designed to extract book data from structured websites and persist that data directly into **MongoDB** for long-term storage and analysis.

## Overview

The scraper demonstrates a complete Scrapy workflow, covering:

* **Spider Logic:** Automated crawling and parsing of web pages.
* **Item Schema:** Structured data definitions for consistency.
* **Pipeline Storage:** Custom middleware to handle asynchronous MongoDB inserts.
* **Centralized Config:** Managed settings for easy environment switching.

---

## Project Structure

```text
Web_Scraping/
├── scrapy.cfg            # Scrapy project entry point
├── tests/                # Unit tests for spiders/parsers
└── books/
    └── books/
        ├── spiders/      # Crawler logic and extraction rules
        ├── items.py      # Data models (schemas)
        ├── pipelines.py  # MongoDB persistence logic
        ├── settings.py   # Project-level configuration
        ├── middlewares.py# Request/Response hooks
        └── __init__.py

```

---

## Requirements & Installation

### Prerequisites

* **Python 3.x**
* **MongoDB** (Ensure the service is running locally)

### Setup

1. Clone the repository.
2. Install the necessary dependencies:

```bash
pip install scrapy pymongo

```

---

##  Configuration

Before running the spider, ensure your **MongoDB** instance is active. You can start it using:

```bash
mongod

```

Verify the connection details in `books/books/settings.py`:

```python
# MongoDB Settings
MONGO_URI = "mongodb://localhost:27017"
MONGO_DATABASE = "books"

```

---

## Running the Spider

Navigate to the project root directory and execute the crawl command:

```bash
# Syntax
scrapy crawl <spider_name>

# Example
scrapy crawl books

```

---

## 📊 Viewing Scraped Data

Once the crawl is complete, you can verify the stored data using the Mongo shell:

```bash
mongo
use books
db.items.find().pretty()

```

> **Note:** Replace `items` with your specific collection name if you have customized it in `pipelines.py`.