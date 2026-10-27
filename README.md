# Day 1 – API Data Analysis Using Python Structures

A Jupyter notebook that pulls customer data from a public REST API, explores its nested JSON structure, flattens it into analysis-ready records, aggregates it with plain Python (loops, sets, dict comprehensions), then validates and visualises the results with pandas and matplotlib.

**Data source:** [JSONPlaceholder `/users`](https://jsonplaceholder.typicode.com/users) – a free fake API returning 10 sample user records.

---

## What the notebook does

| # | Step | Description |
|---|------|-------------|
| 1 | **Retrieve data** | `get_customers(url)` fetches the data with `requests`, using a 10-second timeout and graceful handling of network and JSON errors. |
| 2 | **Explore structure** | `explore(record)` recursively walks a nested record and prints every key with its Python type. |
| 3 | **Extract attributes** | `extract_attributes(customers)` flattens each customer into one dict (ID, name, username, email, email domain, phone, city, zipcode, coordinates, company, website). |
| 4 | **Unique cities** | `unique_cities(customers)` uses a set comprehension to find distinct cities and compares that count to total customers. |
| 5 | **Aggregation in pure Python** | `city_counts()` counts customers per city using a loop; `email_domain_counts()` counts email domains using a dict comprehension. No `Counter`, no pandas. |
| 6 | **DataFrame** | Converts the flat records to a pandas DataFrame and checks that pandas' `value_counts()` matches the hand-written counts. |
| 7 | **CSV export** | Saves `customers.csv` and `city_counts.csv` to `output/`. |
| 8 | **Visualisation** | Saves a bar chart of customers by email domain to `output/customer_distribution.png`. |

## Key findings

- Every customer lives in a different city, so the city distribution is flat (each city has a count of 1). This suggests customers are highly dispersed geographically.
- Because of that, the chart shows **email domain distribution**, which is more informative for a marketing audience.

## Project structure

```
day1-api-analysis/
├── day1_api_analysis.ipynb      # Main notebook (rename to match your file)
├── requirements.txt             # Python dependencies
├── README.md
└── output/
    ├── customers.csv            # Flattened customer table
    ├── city_counts.csv          # Customers per city (sorted by count, then city)
    └── customer_distribution.png  # Email domain bar chart
```

## Requirements

- Python 3.9+
- Libraries: `requests`, `pandas`, `matplotlib`, `ipython`, `jupyter` (or the VS Code Jupyter extension)

Example `requirements.txt`:

```
requests
pandas
matplotlib
ipython
ipykernel
```

## Getting started

1. **Clone the repository**
   ```bash
   git clone https://github.com/AgathaMuli/day1-api-analysis.git
   cd day1-api-analysis
   ```

2. **Create and activate a virtual environment**
   ```bash
   python -m venv .venv

   # Windows
   .venv\Scripts\activate

   # macOS / Linux
   source .venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the notebook**
   Open `day1_api_analysis.ipynb` in VS Code or Jupyter and choose **Run All**. The `output/` folder is created automatically if it doesn't exist.

> An internet connection is required, since the notebook calls the live API.

## Output files

- **`customers.csv`** – one row per customer with the flattened attributes.
- **`city_counts.csv`** – customer count per city, sorted by count (descending) then city name (A–Z).
- **`customer_distribution.png`** – bar chart of customers by email domain.

## Concepts practised

- Making HTTP requests and handling errors (`requests`, `raise_for_status`, `try/except`)
- Navigating nested dictionaries and lists, including recursion
- Safe access with `dict.get()` and default values
- Sets, loops and dict comprehensions for aggregation
- Cross-checking manual results against pandas
- Exporting data to CSV and saving charts with matplotlib

## Author

**Agatha Nduku Muli** – [GitHub](https://github.com/AgathaMuli)
