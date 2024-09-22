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
- **Header**: 
  - Contains the title of the report and styles for tables and text. 
  - It sets the overall look of the report, including font sizes, colors, and spacing, ensuring that the report is visually appealing and easy to read.

- **Tables**: 
  - Displays summaries of low-energy panels and faulty panels.
  - Each table is structured to provide clear and concise information, such as the number of low-energy panels, their percentage compared to the total, and details about faulty panels, including their ID, detected date, and kWh loss. 
  - This structured approach allows readers to quickly grasp the important metrics and findings.

- **Heatmaps**: 
  - Visual representations of energy generation data.
  - Heatmaps provide a graphical view of performance over time, allowing for easy identification of trends and anomalies in energy generation across different modules and dates. 
  - By using colors to represent different levels of performance, heatmaps make it easier to spot low-performing panels at a glance.


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
- **pandas**: Used for data manipulation and analysis, especially for handling CSV files.
- **os**: Provides a way to interact with the operating system, such as file and directory management.
- **datetime**: Used for manipulating dates and times.
- **jinja2**: A templating engine for rendering HTML templates.
- **pdfkit**: A library for converting HTML to PDF using `wkhtmltopdf`.
- **matplotlib** and **seaborn**: Libraries for data visualization, particularly for creating plots and heatmaps.
- **base64**: Used for encoding binary data into ASCII strings.
This section imports necessary libraries for data handling, HTML rendering, PDF generation, and plotting.



#### Function Definitions

**a. `generate_faulty_panel_summary()`**
This function scans the data folders for CSV files, calculates energy generation, and identifies faulty panels based on a specified threshold.

```python
def generate_faulty_panel_summary(crawl_data_folder, start_date, end_date, threshold):
    # Implementation details...
```
- **Parameters**:
  - `crawl_data_folder`: The directory where the CSV files are stored.
  - `start_date`: The date to start the analysis.
  - `end_date`: The date to end the analysis.
  - `threshold`: The number of standard deviations below the average to classify a panel as faulty.
- **Returns**: A dictionary containing details about faulty panels, including their first detection date, resolution status, and energy loss.


**b. `generate_status_table()`**
This function creates a status table for low-energy modules, tracking their performance over weeks.

```python
def generate_status_table(low_energy_modules, start_date, end_date):
    # Implementation details...
```
- **Parameters**:
  - `low_energy_modules`: A list of modules identified as low energy.
  - `start_date`: The date to start the analysis.
  - `end_date`: The date to end the analysis.
- **Returns**: A dictionary containing the status of each module over the weeks.
  

**c. `calculate_daily_energy()`**
Calculates daily energy generation for each module from a given CSV file.

```python
def calculate_daily_energy(file_path):
    # Implementation details...
```
- **Parameters**:
  - `file_path`: The path to the CSV file containing the energy data.
- **Returns**: A DataFrame containing the module names and their corresponding energy generation in kWh.


**d. `sum_daily_energy()`**
Aggregates daily energy data for a specific station over a date range.

```python
def sum_daily_energy(target_station, start_date, end_date):
    # Implementation details...
```
- **Parameters**:
  - `target_station`: The name of the station for which to sum daily energy.
  - `start_date`: The start date for the aggregation.
  - `end_date`: The end date for the aggregation.
- **Returns**: A DataFrame containing the total daily energy generation for each module.


**e. `find_low_energy_pv()`**
Identifies low-energy PV panels by comparing their generation against the average.

```python
def find_low_energy_pv(target_station, start_date, end_date, threshold):
    # Implementation details...
```
- **Parameters**:
  - `target_station`: The name of the station to analyze.
  - `start_date`: The start date for the analysis.
  - `end_date`: The end date for the analysis.
  - `threshold`: The number of standard deviations below the average to classify a panel as low energy.
- **Returns**: A list of tuples containing the module names and their percentage below the average generation.


**f. `generate_heatmap()`**
Generates heatmaps to visualize the performance of low-energy modules.

```python
def generate_heatmap(low_energy_data, start_date, end_date):
    # Implementation details...
```
- **Parameters**:
  - `low_energy_data`: A dictionary containing details about low-energy modules.
  - `start_date`: The start date for the analysis.
  - `end_date`: The end date for the analysis.
- **Returns**: The Base64 encoding of the heatmap image.


**g. `generate_report()`**

This function orchestrates the report generation process, compiling all data and rendering the HTML report.

```python
def generate_report(low_energy_data, start_date, end_date, total_panels_dict, threshold):
    # Implementation details...
```
- **Parameters**:
  - `low_energy_data`: A dictionary containing details about low-energy modules.
  - `start_date`: The start date for the report.
  - `end_date`: The end date for the report.
  - `total_panels_dict`: A dictionary containing total panel counts for each station.
  - `threshold`: The threshold for identifying low-energy panels.
- **Returns**: None (saves the report as an HTML file and converts it to PDF).


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





