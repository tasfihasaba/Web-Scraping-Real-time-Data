# Real-time COVID-19 Data Web Scraping

This project demonstrates how to scrape real-time COVID-19 data from the Worldometer website using Python. The data is extracted, cleaned, and stored in a Pandas DataFrame for further analysis.

## Overview

The script scrapes COVID-19 statistics from the Worldometer website. It collects information about the number of cases, deaths, recoveries, and other related metrics for different countries. The data is then processed and cleaned for use in analysis.

## Usage

1. **Import Libraries**: Import the necessary libraries for web scraping and data handling.

    ```python
    from bs4 import BeautifulSoup
    import requests
    import pandas as pd
    import urllib.request
    ```

2. **Fetch and Parse Data**: Fetch the HTML content from the URL and parse it using BeautifulSoup.

    ```python
    url = 'https://www.worldometers.info/coronavirus/'
    data = requests.get(url)
    soup = BeautifulSoup(data.content, "html.parser")
    ```

3. **Extract Table Data**: Locate the table containing the COVID-19 data and extract the relevant information.

    ```python
    table = soup.find_all('table', class_='main_table_countries')[0]
    thead = table.find('thead')
    tbody = table.find('tbody')

    head = thead.find_all('tr')
    body = tbody.find_all('tr')
    ```

4. **Store Data in DataFrame**: Store the extracted data in a Pandas DataFrame.

    ```python
    head_column = [i.text for i in head[0].find_all('th')]
    rowvalues = [[i.text for i in tr.find_all('td')] for tr in body]

    covidglobal = pd.DataFrame(rowvalues, columns=head_column)
    ```

5. **Clean Data**: Clean the DataFrame to remove unnecessary columns and rows.

    ```python
    covid = covidglobal.copy()
    covid.drop(['#', '1 Caseevery X ppl', '1 Deathevery X ppl', '1 Testevery X ppl'], axis=1, inplace=True)
    covid = covid[7:].reset_index(drop=True)
    covid.rename(columns={'Country,Other': 'Country'}, inplace=True)
    ```

## Data Cleaning

The data cleaning process involves:

- **Removing Irrelevant Columns**: Columns that are not necessary for the analysis are dropped from the DataFrame.
  
- **Skipping Unnecessary Rows**: Rows that do not contain relevant data are excluded from the dataset.
  
- **Renaming Columns**: Columns are renamed to provide clarity and ensure consistency.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
