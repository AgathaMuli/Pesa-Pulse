# Day 1 Assignment: Python Data Analysis with API Data

This project fetches sample customer data from the JSONPlaceholder API, inspects the nested JSON structure, flattens it into a clean tabular format, and performs summary analysis using plain Python, pandas, and matplotlib.

The assignment is built around a small public dataset with 10 sample users and focuses on:

- extracting structured attributes from nested records
- counting values using Python loops and dictionaries
- validating results with pandas
- exporting CSV output files
- creating simple distribution charts

Data source: [JSONPlaceholder /users](https://jsonplaceholder.typicode.com/users)

---

## Project structure

```text
.
├── Analysis.ipynb
├── README.md
├── expected_output.md
├── pyproject.toml
├── requirements.txt
├── starter.py
├── output/
│   ├── city_counts.csv
│   ├── customers.csv
│   ├── city_distribution.png
│   └── email_domain_distribution.png
└── src/
    └── day1assignment/
        └── __init__.py
```

### File purpose

- `Analysis.ipynb`: main notebook containing the full data analysis workflow.
- `starter.py`: scaffold with the function definitions to complete for the assignment.
- `expected_output.md`: reference for the expected output format and summary structure.
- `output/`: generated CSV and chart files from the notebook.
- `src/day1assignment/`: Python package scaffold for the project.

---

## Assignment workflow

1. Retrieve customer records from the API.
2. Explore the nested JSON structure and inspect the keys and data types.
3. Flatten each user into a single dictionary with the fields needed for analysis.
4. Count unique cities and customers per city using pure Python.
5. Count email domains using string operations and dictionary logic.
6. Validate the manual counts against pandas `value_counts()`.
7. Save the processed customer data and counts as CSV files.
8. Generate charts showing the distribution of customers by city and email domain.

---

## Core fields extracted

Each customer record is flattened into a single row containing:

- `customer_id`
- `name`
- `username`
- `email`
- `email_domain`
- `phone`
- `city`
- `zipcode`
- `latitude`
- `longitude`
- `company`
- `website`

The nested API data is accessed through keys such as:

- `address.city`
- `address.geo.lat`
- `address.geo.lng`
- `email.split('@')[-1].split('.')[-1]`

---

## Expected outputs

### Customer data CSV

The cleaned customer data is saved to `output/customers.csv` with columns like:

```text
customer_id,name,username,email,email_domain,phone,city,zipcode,latitude,longitude,company,website
```

### City counts CSV

The aggregated counts are saved to `output/city_counts.csv`:

```text
city,customer_count
```

This file is sorted by `customer_count` descending and then `city` alphabetically.

### Charts

The notebook generates distribution charts such as:

- `output/city_distribution.png`
- `output/email_domain_distribution.png`

These are labeled bar charts that show the number of customers per category.

---

## Example findings

The analysis checks that:

- all customers are returned successfully from the API
- the number of unique cities matches the total customer count when every city is unique
- the manual city counts match the pandas counts
- email domains are summarized without using `Counter` or pandas for the aggregation step

The city-level chart and email-domain chart provide different perspectives:

- the city distribution shows geographic spread
- the email-domain chart is often more useful for marketing or business insights because it highlights cluster patterns in the dataset

---

## How to run

Install dependencies and then run the notebook or script:

```bash
pip install -r requirements.txt
```

Then open `Analysis.ipynb` in VS Code/Jupyter or execute the relevant logic from `starter.py`.

---

## Notes

This project is a structured data-analysis exercise designed to build confidence with:

- nested JSON parsing
- list and dictionary aggregation
- data cleaning and normalization
- pandas-based validation
- simple chart creation for reporting


