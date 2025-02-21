# Introduction to Web Scraping

## What is Web Scraping?
Web scraping is the process of extracting data from websites using automated scripts or tools. It allows you to gather information from the web and save it in a structured format like CSV, JSON, or a database.

## Prerequisites
Before getting started, ensure you have the following installed:
- **Python** (Download: [python.org](https://www.python.org/))
- **pip** (Python package manager)
- **Libraries:** `requests`, `BeautifulSoup`, and `pandas`

You can install them using:
```bash
pip install requests beautifulsoup4 pandas
```

## Basic Web Scraping Example
Here is a simple example of scraping titles from a website:

```python
import requests
from bs4 import BeautifulSoup

# URL of the website to scrape
url = "https://example.com"
response = requests.get(url)

# Parse the HTML content
soup = BeautifulSoup(response.text, 'html.parser')

# Extract titles
titles = soup.find_all('h2')

for title in titles:
    print(title.text)
```

## Handling Dynamic Content
For websites that load content dynamically, you can use **Selenium**:
```bash
pip install selenium
```
Example:
```python
from selenium import webdriver
from selenium.webdriver.common.by import By

# Set up WebDriver (Ensure you have the correct driver installed)
driver = webdriver.Chrome()
driver.get("https://example.com")

# Extract elements
elements = driver.find_elements(By.TAG_NAME, 'h2')
for element in elements:
    print(element.text)

driver.quit()
```

## Storing Scraped Data
Save data to CSV using `pandas`:
```python
import pandas as pd

# Sample data
data = {"Titles": [title.text for title in titles]}

# Convert to DataFrame
df = pd.DataFrame(data)

# Save as CSV
df.to_csv("scraped_data.csv", index=False)
```

## Ethical Considerations
- Always check the website’s **robots.txt** file before scraping.
- Do not overload the server with frequent requests.
- Use **headers** to mimic a real browser request.

Example:
```python
headers = {"User-Agent": "Mozilla/5.0"}
requests.get(url, headers=headers)
```

## Next Steps
- Explore APIs for structured data retrieval.
- Learn about advanced scraping with Scrapy.
- Handle JavaScript-heavy sites with Selenium.

Happy Scraping! 🚀
