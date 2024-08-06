# Real-time COVID-19 Data Web Scraping

This project demonstrates how to scrape real-time COVID-19 data from the Worldometer website using Python. The data is extracted, cleaned, and stored in a Pandas DataFrame for further analysis.

## Table of Contents

- [Overview](#overview)
- [Requirements](#requirements)
- [Usage](#usage)
- [Data Cleaning](#data-cleaning)
- [License](#license)

## Overview

The script scrapes COVID-19 statistics from the Worldometer website. It collects information about the number of cases, deaths, recoveries, and other related metrics for different countries. The data is then processed and cleaned for use in analysis.

## Requirements

Ensure you have the following Python libraries installed:
- `beautifulsoup4`
- `requests`
- `pandas`

You can install these using pip:
```bash
pip install beautifulsoup4 requests pandas
Data Cleaning

## The data cleaning process involves:

Removing irrelevant columns.
Skipping rows that do not contain relevant data.
Renaming columns for clarity.
