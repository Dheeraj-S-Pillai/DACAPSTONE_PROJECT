# CSR Projects by Companies in India (2014 to 2020)

An exploratory data analysis (EDA) of Corporate Social Responsibility (CSR) projects reported by Indian companies between 2014 and 2020. The project cleans the raw data and studies how CSR money is spread across development sectors, states and companies, and how it changed over time.

## Project Overview

- **Problem statement:** Analyse CSR projects reported by Indian companies (2014 to 2020) to understand how spending is distributed across sectors, states and companies, and how it changed over the years.
- **Domain:** Corporate Social Responsibility (CSR), money companies spend on social causes such as education and health.
- **Objectives:**
  - Clean the data and handle missing, inconsistent and invalid values
  - Find which sectors, states and companies get or give the most CSR money
  - Study the change in spending over the years
  - Compare government companies with other companies

## Dataset


- **File used:** `csr-projects-by-companies.xlsx` (loaded directly from the project's GitHub repository)
- **Size:** 36,664 projects and 17 columns (36,660 rows and 18 columns after cleaning)
- **Coverage:** 693 companies, years 2014 to 2020
- **Units:** Amounts are in lakhs (1 crore = 100 lakhs)

Main columns: `year`, `state_name`, `district_name`, `csr_project_name`, `development_sector`, `company_name`, `company_type`, `listing_status`, `project_outlay_amount_in_lakhs`, `amount_spent_in_lakhs`.

## Tools and Libraries

- Python
- pandas, numpy (data handling)
- matplotlib, seaborn (static charts)
- plotly (interactive charts)

## Workflow

1. **Import libraries and load data**
2. **First look at the data** (shape, data types, summary statistics)
3. **Data cleaning**
   - Filled 3 empty project names with `Not Mentioned`
   - Checked "hidden" missing values (district 66%, sector 1,572 rows, state 667 rows are `Not Mentioned`) and kept those rows
   - Dropped the unused `id` column and checked for duplicates (none found)
   - Converted `year` from a date to a year number
   - Removed extra spaces and fixed inconsistent labels (for example `PLC` to `Public`)
   - Removed 4 rows with negative amounts
   - Flagged 194 planned outlays above 10,00,000 lakhs as likely entry errors. The rows are kept, but the outlay column is not used for totals or averages
   - Renamed long column names and created two new columns: `spent_crore` and `project_size`
4. **Exploratory Data Analysis**
   - Univariate: projects by sector, company type, distribution of spending
   - Bivariate: spending by year, sector, state and company; government vs other companies; outlay vs amount spent
   - Multivariate: sector x year heatmap, year x company type, correlation heatmap
   - Interactive Plotly charts
5. **Summary, recommendations, limitations and conclusion**

## Key Findings

1. **Spending grew until 2019.** It rose from about 5,556 crore in 2014 to 11,904 crore in 2019, then fell about 23% to 9,108 crore in 2020.
2. **Education and Health Care get the most money.** Together they take about 44% of all spending.
3. **More than half the money (52%) is reported as "All India"**, so it cannot be assigned to a state. Among real states, Maharashtra leads with about 6,609 crore, followed by Andhra Pradesh and Karnataka.
4. **A few big companies give a large share.** The top 10 of 693 companies give about 42% of all CSR money. Reliance Industries, ONGC and TCS are the top three.
5. **Government companies run fewer but larger projects.** They run about 11% of the projects but give about 26% of the spending.
6. **Most projects are small.** The mean spend is 155.6 lakhs but the median is only 10 lakhs, so a few very large projects pull the average up. Totals and medians describe the data better than averages.
7. **2020 looks different.** Health Care rose to its highest level (2,463 crore) while Education fell to 1,790 crore, making Health Care the top sector for the first time. The data cannot tell us the reason.

## Recommendations

- Companies should report the state and district of every project.
- The planned outlay values should be checked at the source.
- Sectors and regions that receive very little money deserve a closer look.
- The 2020 drop and the shift towards Health Care should be read carefully, since this data does not explain the cause.

## Limitations

- 66% of rows have no district, so no district-level analysis was done.
- `All India` is not a state and is shown as its own category.
- The planned outlay column is unreliable, so only the amount spent is used for totals.
- The data shows what companies reported, not the real impact of the projects.

## How to Run

1. Clone the repository and open `CSR_Project_Final.ipynb` in Jupyter Notebook, JupyterLab or Google Colab.
2. Install the required libraries if needed:
   ```bash
   pip install pandas numpy matplotlib seaborn plotly openpyxl
   ```
3. Run all cells. The notebook reads the Excel file from the GitHub link, so an internet connection is needed.

## Files

| File | Description |

| `CSR_Project_Final.ipynb` | Full analysis notebook (cleaning, EDA, findings) |
| `csr-projects-by-companies.xlsx` | Raw dataset from India Data Portal |
| `README.md` | Project description |

## Future Work

- Add state population data to compare spending per person.
- Add newer years of data to see whether the fall in 2020 continued.
