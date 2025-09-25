# Project Description

## Data Scraper: Real Estate (Tranio / HomesOverseas / Prian)

Scripts for bulk collection of listings from websites, data cleaning, and Excel export.  
Supports: pagination, deduplication, error handling (429/non-200), extraction of area/rooms, price normalization, and *price per m²* calculation.  
Includes a final consolidated report: a single Excel file with a separate sheet for each country.

---

## What’s Inside (Key Features)

* **HTML Parsing**: `requests` + `BeautifulSoup` / `LxmlSoup`, resilient to empty pages and duplicates  
* **Cleaning & Calculations**:  
  - price parsing and currency conversion → €  
  - extraction of area and number of rooms  
  - price per m² calculation  
  - unified column set and numbering  
* **Excel Export (openpyxl)**:  
  - “smart tables” with totals and banded rows  
  - mini-pivots (averages) on each sheet  
  - automatic number formatting  
  - multi-sheet file: one tab per country  
* **Aggregation**: read files from each site → combine into one consolidated report  
* **Anti-blocking measures**: delays between requests, retries on 429  

---

## Useful Code Snippets (Reusable)

* Auto-create missing directories before saving  
* Template for Excel “smart table” (Table, style, totals)  
* Adding multiple sheets/tables into one file  
* Mini-summary with `SUBTOTAL` formulas  
* Universal functions for writing DataFrames to Excel with auto-formatting  

---

## Input & Output

* **Input**: website pages, list of countries, and base save paths:  
  - !before running the code, add a folder with the corresponding name on your desktop  

  <img width="237" height="98" alt="image" src="https://github.com/user-attachments/assets/f3de9a21-6531-4f88-97c7-a043ab5d9a7c" />

* **Output**:  
  - Excel files by site (`/data/<Site>/<Country>.xlsx`)  

  <img width="370" height="265" alt="image" src="https://github.com/user-attachments/assets/c7f23719-63d4-46f9-8d20-f58bb28184f2" /> <img width="1044" height="621" alt="image" src="https://github.com/user-attachments/assets/b626968a-d528-4049-94aa-f335bb2b8db5" />

  - consolidated report `/output/RealEstate.xlsx` with country-level tabs  
    
<img width="953" height="726" alt="image" src="https://github.com/user-attachments/assets/936b0d7b-b937-4f4e-99ec-a290017c2f05" />

---

## Limitations & Ethics

* Website markup may change — selectors need updating accordingly  
* Respect robots.txt and rate-limit (don’t shorten delays, don’t raise `max_pages`)  
