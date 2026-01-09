# Noon Web Scraper

A Python-based web scraper for noon.com that extracts product listings with multi-seller support and exports data to Excel format.

## Features

- Keyword Search: Search for any product keyword on noon.com
- Multi-Seller Support: Automatically detects and captures all sellers for each product
- Comprehensive Data: Extracts 9 fields per product-seller combination
- Excel Export: Formatted Excel output with auto-adjusted columns
- Smart Scraping: Includes delays and human-like behavior to avoid bot detection
- Progress Tracking: Real-time progress updates during scraping

## Requirements

- Python 3.7+
- Chrome browser installed
- Internet connection

## Installation

1. **Clone or download this repository**

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

   This will install:
   - `selenium` - Web automation
   - `webdriver-manager` - Automatic ChromeDriver management
   - `pandas` - Data manipulation
   - `openpyxl` - Excel file creation

## Usage

### Basic Usage

Run the scraper:

```bash
python main.py
```

Follow the interactive prompts:
1. Enter search keywords (one per line)
2. Optionally set a limit for products per keyword
3. Confirm and start scraping

### Example Session

```
Keyword 1: iphone
Keyword 2: samsung galaxy
Keyword 3: done

Limit products per keyword? (Enter number or press Enter for all): 10

Proceed with scraping? (yes/no): yes
```

## Output

### Excel File

The scraper creates an Excel file in the `output/` directory with the following format:

| Search Keyword | Category | Title | Description | Price | Rating | Reviews | Seller | Product URL |
|----------------|----------|-------|-------------|-------|--------|---------|--------|-------------|
| iphone | Electronics > Mobiles | iPhone 16... | 128GB, White... | AED 3,999 | 4.6 | 12.8K | noon | https://... |

**Note**: Products with multiple sellers will have one row per seller.

### File Naming

Files are named with timestamps:
- Single keyword: `noon_scraper_iphone_2026-01-09_13-30-45.xlsx`
- Multiple keywords: `noon_scraper_2026-01-09_13-30-45.xlsx`

## Data Fields

1. Search Keyword: The keyword used to find the product
2. Category: Product category from breadcrumbs (e.g., "Electronics > Mobiles & Tablets")
3. Title: Full product title
4. Description: Product highlights/description
5. Price: Product price (varies by seller)
6. Rating: Product rating (1-5 stars)
7. Reviews: Number of reviews
8. Seller: Seller name (e.g., "noon", "TechStore")
9. Product URL: Direct link to product page

## Configuration

Edit `config.py` to customize:

- Timeouts: Adjust wait times for page loading
- Delays: Modify delays between requests
- Selectors: Update CSS selectors if website structure changes
- Output: Change output directory or filename format

## Troubleshooting

### Common Issues

1. ChromeDriver not found
- The script automatically downloads ChromeDriver
- Ensure Chrome browser is installed

2. No data scraped
- Check internet connection
- Verify noon.com is accessible
- Review `scraper.log` for detailed error messages

3. CAPTCHA appears
- The scraper includes delays to avoid detection
- If CAPTCHA appears, you may need to solve it manually
- Consider increasing delays in `config.py`

4. Selectors not working
- noon.com may have updated their website structure
- Update CSS selectors in `config.py`
- Check `scraper.log` for specific errors

### Logs

Check `scraper.log` for detailed execution logs and error messages.

## Project Structure

```
revent-automation-assignment/
├── main.py                 # Main entry point
├── noon_scraper.py         # Core scraper logic
├── excel_exporter.py       # Excel export functionality
├── config.py               # Configuration settings
├── requirements.txt        # Python dependencies
├── README.md              # This file
├── output/                # Excel output directory (created automatically)
└── scraper.log           # Log file (created automatically)
```

## Technical Details

### Web Scraping Approach

- **Selenium WebDriver**: Handles JavaScript-rendered content
- **Dynamic Waits**: Waits for elements to load before extraction
- **Multi-Seller Detection**: Clicks "Other Sellers" button to access modal
- **Error Handling**: Continues scraping even if individual products fail

### Anti-Bot Measures

- Random delays between requests (2-4 seconds)
- Human-like scrolling behavior
- Realistic user agent
- Disabled automation flags

## Limitations

- Scraping speed is intentionally slow to avoid detection
- Large scrapes (100+ products) may take significant time
- noon.com may implement additional anti-scraping measures
- Some product fields may be "N/A" if not available

## Legal Notice

This scraper is for educational purposes. Always respect website terms of service and robots.txt. Use responsibly and ethically.

## Support

For issues or questions:
1. Check `scraper.log` for error details
2. Review this README's troubleshooting section
3. Verify all dependencies are installed correctly

## Version

v1.0 - Initial release (2026-01-09)
