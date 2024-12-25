# quotes_scrape

Overview

This Python script scrapes inspirational quotes, authors, and tags from the website Quotes to Scrape. The data is saved to a CSV file for further use. The script is robust, handles errors gracefully, and allows configurable parameters for scalability and flexibility.

Features

Retry Mechanism: Automatically retries failed network requests.

User-Agent Header: Mimics a browser to avoid server blocks.

Logging: Logs progress, errors, and summary to scraper.log.

Command-Line Arguments: Flexible input for dynamic configuration.

Graceful Pagination Handling: Stops scraping when no more pages are available or upon reaching a maximum page limit.

Incremental CSV Writing: Ensures data is saved after each page.

Error Handling: Captures errors without halting execution.

Requirements

Ensure the following Python libraries are installed:

pip install requests beautifulsoup4

Usage

Command-Line Arguments

Argument

Required

Description

Default Value

--start_url

Yes

Starting URL for scraping.

None

--output_file

No

Name of the output CSV file.

quote_list.csv

--max_pages

No

Maximum number of pages to scrape.

Unlimited (None)

Run the Script

Save the script as advanced_scraper.py.

Run the script from the terminal with desired arguments. For example:

python advanced_scraper.py --start_url "http://quotes.toscrape.com/tag/inspirational/" --output_file "quotes.csv" --max_pages 5

Output

CSV File

The output CSV file will contain the following columns:

Column

Description

quote

The inspirational quote text.

author

The author of the quote.

tags

Comma-separated tags associated with quote

Log File

A scraper.log file is generated to log the scraping process, including:

URLs scraped

Number of quotes extracted

Errors encountered

Example Output

Console Output

Starting the scraping process...
Scraping completed! Total pages scraped: 5, Total quotes saved: 50

CSV Output (quotes.csv)

Quote

Author

Tags

"The greatest glory in living lies not in..."

Nelson Mandela

inspirational, life

"It is never too late to be what you might..."

George Eliot

inspirational

Log Output (scraper.log)

2024-12-25 12:00:00 - INFO - Scraping URL: http://quotes.toscrape.com/tag/inspirational/
2024-12-25 12:00:05 - INFO - Extracted 10 quotes from http://quotes.toscrape.com/tag/inspirational/
2024-12-25 12:00:10 - INFO - Scraping URL: http://quotes.toscrape.com/tag/inspirational/page/2/
2024-12-25 12:00:15 - INFO - Scraping completed! Total pages scraped: 5, Total quotes saved: 50

Implementation Details

Functions

fetch_page_content(url, retries=3, delay=2):

Fetches and returns the parsed HTML content of a URL.

Retries failed requests up to retries times.

extract_quotes(bs):

Extracts quote text, author, and tags from the HTML content.

get_next_page(bs, base_url):

Finds the next page link and constructs its full URL.

write_to_csv(file_name, data, fieldnames):

Appends the extracted data to a CSV file.

scrape_quotes(start_url, output_file, max_pages):

Orchestrates the scraping process and saves results incrementally.

Extensibility

Scraping Other Tags:

Modify the start_url argument to target a different tag.

Multithreading/Async:

For large-scale scraping, incorporate concurrent.futures or aiohttp.

Custom Fields:

Extend the script to capture additional fields from the website.

Troubleshooting

No Data in CSV:

Ensure the start_url is correct.

Check the website’s structure for changes.

Blocked by Website:

Increase the delay in fetch_page_content.

Use proxies or rotate user-agent strings.

Incomplete Data:

Check the scraper.log  for errors or skipped pages.
