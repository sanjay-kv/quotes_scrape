# Quote Scraper

This Python script scrapes inspirational quotes from the website [Quotes to Scrape](http://quotes.toscrape.com) and saves them into a CSV file. It collects the following details for each quote:

- **Quote text**
- **Author**
- **Tags associated with the quote**

The script handles pagination to scrape all quotes under the "inspirational" tag. The collected data is saved in a CSV file named `quote_list.csv`.

## Requirements

- Python 3.x
- `beautifulsoup4` library
- `requests` library

You can install the required libraries using pip:

```bash
pip install beautifulsoup4 requests
