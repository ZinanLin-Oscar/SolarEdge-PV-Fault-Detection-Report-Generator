# SolarEdge-PV-Fault-Detection-Report-Generator
This project generates a weekly report for photovoltaic (PV) panel fault detection. It analyzes energy generation data, identifies low-energy panels, and compiles the findings into a structured HTML report, which can be converted into a PDF format. The report includes various tables and heatmaps to visualize the data effectively.


## Project Structure
```
SolarEdge-PV-Fault-Detection-Report-Generator/
│
├── report_template.html      # HTML template for the report
├── generate_report.ipynb     # Main Python script for report generation
├── data/                     # Folder containing CSV data files
├── images/                   # Folder for saving generated images
└── README.md                 # Project documentation
```


## Installation
Ensure you have the following libraries installed:
```bash
pip install pandas jinja2 pdfkit matplotlib seaborn
```
Also, make sure to install `wkhtmltopdf` for PDF conversion.


## Workflow
1. **Data Collection**: Gather energy generation data from CSV files.
2. **Data Processing**: Analyze the data to identify faulty panels and low-energy panels.
3. **Report Generation**: Use an HTML template to create a report that summarizes the findings.
4. **PDF Conversion**: Convert the HTML report into a PDF format for distribution.


## Code Explanation
### 1. HTML Template (`report_template.html`)
This file defines the structure and style of the report. It uses Jinja2 templating syntax to dynamically insert data into the HTML.
**Key Sections**:
- **Header**: Defines the title and styles for tables and text.
- **Tables**: Displays summaries of low-energy panels and faulty panels.
- **Heatmaps**: Visual representations of energy generation data.

### 2. Main Python Script (`generate_report.ipynb`)
```python
import pandas as pd
import os
from datetime import datetime, timedelta
from jinja2 import Environment, FileSystemLoader
import pdfkit
import matplotlib.pyplot as plt
import seaborn as sns
import base64
```
This section imports necessary libraries for data handling, HTML rendering, PDF generation, and plotting.

#### Function Definitions

**a. `generate_faulty_panel_summary()`**

This function scans the data folders for CSV files, calculates energy generation, and identifies faulty panels based on a specified threshold.

```python
def generate_faulty_panel_summary(crawl_data_folder, start_date, end_date, threshold):
    # Implementation details...
```

**b. `generate_status_table()`**

This function creates a status table for low-energy modules, tracking their performance over weeks.

```python
def generate_status_table(low_energy_modules, start_date, end_date):
    # Implementation details...
```

**c. `calculate_daily_energy()`**

Calculates daily energy generation for each module from a given CSV file.

```python
def calculate_daily_energy(file_path):
    # Implementation details...
```

**d. `sum_daily_energy()`**

Aggregates daily energy data for a specific station over a date range.

```python
def sum_daily_energy(target_station, start_date, end_date):
    # Implementation details...
```

**e. `find_low_energy_pv()`**

Identifies low-energy PV panels by comparing their generation against the average.

```python
def find_low_energy_pv(target_station, start_date, end_date, threshold):
    # Implementation details...
```

**f. `generate_heatmap()`**

Generates heatmaps to visualize the performance of low-energy modules.

```python
def generate_heatmap(low_energy_data, start_date, end_date):
    # Implementation details...
```

**g. `generate_report()`**

This function orchestrates the report generation process, compiling all data and rendering the HTML report.

```python
def generate_report(low_energy_data, start_date, end_date, total_panels_dict, threshold):
    # Implementation details...
```

#### Main Execution Block

```python
if __name__ == "__main__":
    main()
```

The `main()` function drives the overall workflow, calling all necessary functions to complete the report generation.

## Usage Instructions

1. Place your CSV data files in the `data/` folder.
2. Update the paths in the script as necessary.
3. Run the script:

```bash
python generate_report.ipynb
```

4. The report will be generated as `weekly_report.html` and converted to `weekly_report.pdf`.

## Conclusion

This project provides a comprehensive solution for monitoring PV panel performance and generating insightful reports. Feel free to contribute or modify the code as needed!





