# Scrapy Web Scraper with MongoDB

A Python web scraper built with **Scrapy** that extracts book data and persists it into **MongoDB**. This project demonstrates a standard Scrapy workflow from extraction to database storage.

## 🚀 Overview

The scraper focuses on:

* **Spider Logic:** Automated crawling and parsing of web pages.
* **Item Schema:** Structured data definitions for consistency.
* **Item Pipelines:** Cleanly handling data persistence to MongoDB.
* **Centralized Config:** Managed settings for database URIs and collection names.

---

## Project Structure

```text
Web_Scraping/
├── scrapy.cfg            # Scrapy project entry point
├── tests/                # Unit tests
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

1. Create and activate a virtual environment.
2. Install the necessary dependencies:

```bash
pip install scrapy pymongo

```

---

## Configuration

Ensure your **MongoDB** instance is active:

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
# General Syntax
scrapy crawl <spider_name>

# Example (Check spiders/ directory for exact name)
scrapy crawl books

```

---

## Viewing Scraped Data

Once the crawl is complete, verify the stored data using the Mongo shell:

```bash
mongo
use books
db.items.find().pretty()

```

> **Note:** Replace `items` with your specific collection name if customized in your pipeline.