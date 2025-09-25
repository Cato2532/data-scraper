# AvitoScraper

A script for scraping listings from Avito.  
It collects product data: **title**, **price**, and **additional information**.  
Results are exported to CSV for further analysis.

---

## How It Works
* Uses `requests` to load HTML pages and `BeautifulSoup` to parse them.  
* Saves three fields for each listing:  
  - `name`  — listing title  
  - `price` — price (as text, without normalization)  
  - `info`  — description or product details  
* Includes duplicate protection: identical listings are not repeated in the final table.  

---

## Important Note
Avito **regularly changes HTML classes**.  
In the code, this looks like:  
```python
soup.find_all("div", class_="iva-item-body-oMJBI")
snippet.find("div", class_="iva-item-title-KE8A9")
snippet.find("div", class_="price-priceContent-I4I3p")
snippet.find("div", class_="iva-item-bottomBlock-VewGa")
```
---

## What to Do If the Scraper Stops Finding Data?

1. Open the desired **Avito** page in your browser.  
2. Right-click → choose *Inspect*.  
3. Find the HTML block with **title**, **price**, or **description**.  
4. Copy the current `class` value and replace it in the scraper code.   

<img width="1433" height="651" alt="image" src="https://github.com/user-attachments/assets/09d22961-a989-41ea-84d1-d9def03aaea6" />

---

## Примечание об ограничениях и авторских правах

Этот скрипт **не нарушает авторские права Avito**, так как:

* Парсер принимает на вход только **одну конкретную страницу URL**, а не обходит сайт целиком.  
* Код предназначен исключительно для **учебных и исследовательских целей** — показать пример работы с HTML и `BeautifulSoup`.  
* Нет обхода защиты (CAPTCHA, авторизация, API Avito). Скрипт работает только с **открытыми публичными страницами**.  
* Для больших объёмов данных требуется вручную прописывать новые URL и запускать парсер снова.  
* Добавлена защита от дублей и остановка при повторяющихся данных, что ограничивает нагрузку на сайт.  

⚠️ Если нужен полноценный сбор больших массивов данных, используйте официальные API и соблюдайте правила Avito.
