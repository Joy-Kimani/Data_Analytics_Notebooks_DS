 SQL Query Exercises

A Python and SQLite notebook demonstrating foundational SQL querying (`SELECT`, `WHERE`, `LIMIT`, comparison operators, and logical operators) using an in-memory SQLite database populated from the Chinook CSV dataset[cite: 1].

## Overview
This project loads 11 relational CSV tables representing the a digital media store into an in-memory SQLite database via `pandas` and `sqlite3`, then executes seven analytical SQL queries covering customer records, employee profiles, and invoice transactions[cite: 1].

## Dataset Schema

The notebook ingests CSV files from the dataset into SQLite tables:

| Table Name | Row Count | Description |
| :--- | :---: | :--- |
| `albums` | 14 | Album titles and artist associations|
| `artists` | 10 | Music artists|
| `customers` | 30 | Store customer demographics and locations|
| `employees` | 5 | Staff roles, hire dates, reporting lines, and contact details|
| `genres` | 10 | Track music genres|
| `invoice_items` | 450 | Individual line items per invoice|
| `invoices` | 120 | Customer purchase invoices and billing details|
| `media_types` | 5 | Audio/media file formats|
| `playlist_track` | 130 | Many-to-many mapping between playlists and tracks|
| `playlists` | 6 | Curated music playlists|
| `tracks` | 80 | Individual tracks, durations, and pricing|


## Queries Covered

1. **Customer First Names (`LIMIT`)** — Retrieves the first names of the first 10 customers from `customers`.
2. **Employee Hire Dates (`SELECT` specific columns)** — Fetches `FirstName`, `LastName`, and `HireDate` for all staff in `employees`
3. **Full Employee Directory (`SELECT *`)** — Returns all columns and records from the `employees` table
4. **Customers in Germany (`WHERE =`)** — Filters `customers` for records where `Country = "Germany"`
5. **Customers Outside Germany (`WHERE !=` & `LIMIT`)** — Retrieves the first 10 customers whose `Country` is not `"Germany"`
6. **High-Value USA Invoices (`AND` operator)** — Queries `invoices` where `BillingCountry = "USA"` and `Total > 10`
7. **Filtered Sales Support Agents (Multi-condition `WHERE`)** — Returns all details for employees in `Calgary` with the title `Sales Support Agent` hired on or after `2003-05-03`.



## Prerequisites & Setup

### Requirements
* **Python** 3.13+
* **Libraries:** `pandas`, `sqlite3` (standard library)

### Running the Notebook
1. **Kaggle Environment:** Attach the `joykizenga/chinook-aigen` dataset so the CSV files are accessible at `/kaggle/input/datasets/joykizenga/chinook-aigen/*.csv`.
2. **Local Environment:** Download the Chinook CSV files into a local directory and update the `glob.glob(...)` path in the first code cell to point to your local folder.
3. Run all cells sequentially to initialize the `:memory:` SQLite connection and execute each `pd.read_sql_query()` exercise.
