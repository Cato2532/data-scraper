# Route Parser

This parser is designed to extract routes from the [Avtodispetcher](https://www.avtodispetcher.ru) website.  
It demonstrates how to work with HTML table structures and serves as an example that the approach is universal and can be applied not only to listing-based websites.

## Key Features
- Extracts **route point names**.  
- Extracts **route length (km)**.  
- Extracts **region** (using a selector with the `colspan` attribute).  
- Handles markup errors (mismatched list lengths, empty values).  
- Exports results into a **CSV file** for further analysis.  

## How This Parser Differs from Others
- **Different page model**: instead of listing cards in `<div>`, here we deal with **table rows and cells `<table>/<tr>/<td>`**.  
- **Attribute-based search**: example of a targeted selector with **`colspan="2"`**, not only class-based (`class="..."`).  
- **List synchronization**: data is distributed across different table columns, so we **iteratively align lists** by the shortest length (resilient to uneven markup).  
- **Strict positional binding**: name/length/region are read from different columns — it’s important to correctly “merge” fields from the same row.  

<img width="869" height="665" alt="image" src="https://github.com/user-attachments/assets/649f508a-47b2-4400-ba54-367240cbb621" />

## Why It Demonstrates a Universal Approach
- Shows how to work with **different HTML structures**: cards (`div` blocks) and tables (`td`, attributes).  
- Uses **different selector strategies**: by class (`class="..."`) and by arbitrary attributes (`colspan="2"`).  
- Implements **robust patterns**: protection from mismatched list lengths, fallbacks for missing elements, clean export into a tabular format.  
- Code is easily adaptable: **replace selectors — and it will work with another tabular source** (schedules, price lists, catalogs, etc.).  

## Example Output
CSV file with columns:  
- `name` — route point name  
- `length` — length in kilometers  
- `region` — region  

The file is saved as **`Routes.csv`**.   
