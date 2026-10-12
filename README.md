# Web Scraping Lab: Programming Languages & Salaries

A hands-on Jupyter notebook that scrapes a table of programming languages and their average annual salaries from a static web page, then saves the result to a CSV file.

Based on the IBM Skills Network lab *"Hands-on Lab: Web Scraping"* (IBM-DA0321EN).

---

## Objectives

- Download and parse a web page with `requests` and `BeautifulSoup`
- Extract specific fields from an HTML table
- Load the scraped data into a `pandas` DataFrame
- Export the data to a CSV file

## Data Source

| Item | Detail |
|---|---|
| Page | `Programming_Languages.html` (hosted on IBM Skills Network cloud storage) |
| Fields scraped | Programming language name, average annual salary |
| Format | Single HTML `<table>` |

The URL is defined in the first code cell of the notebook.

## Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.7+ | Runtime (notebook kernel was 3.7.12) |
| `requests` | Download the page HTML |
| `beautifulsoup4` | Parse the HTML and locate table rows |
| `pandas` | Build the DataFrame and write the CSV |
| Jupyter | Run the notebook |

## How It Works

1. **Fetch**: `requests.get(url).text` downloads the page HTML.
2. **Parse**: `BeautifulSoup(data, "html.parser")` builds a searchable soup object.
3. **Locate**: `soup.find('table')` grabs the first table on the page.
4. **Extract**: loop through every `<tr>`, collect its `<td>` cells, and keep:
   - Column index `1` → language name
   - Column index `3` → annual average salary
   - Rows with fewer than 5 cells are skipped (this filters out the header row).
5. **Export**: the two lists become a DataFrame and are saved with `df.to_csv('popular_languages.csv', index=False)`.

## Output

**`popular_languages.csv`** with two columns:

| Language Name | Annual Average Salary |
|---|---|
| *(language)* | *(salary as scraped, text)* |

## Getting Started

### 1. Install dependencies

```bash
pip install requests beautifulsoup4 pandas jupyter
```

### 2. Run the notebook

```bash
jupyter notebook Web-Scraping-Lab.ipynb
```

Run all cells from top to bottom. The CSV is written to the same folder as the notebook.

## Project Structure

```
.
├── Web-Scraping-Lab.ipynb    # The lab notebook
├── popular_languages.csv     # Generated output
└── README.md
```


## Scraping Etiquette

This lab uses a page built for practice. For real sites, check the `robots.txt` and terms of service first, and rate-limit your requests.

## Credits

- **Author:** Ramesh Sannareddy
- **Contributor:** Rav Ahuja
- **Organization:** IBM Skills Network

## License

Original notebook © 2020 IBM Corporation, released under the [MIT License](https://cognitiveclass.ai/mit-license/).
