# Adult Income Exploratory Data Analysis

## 1. Project Overview

This project analyzes the UCI Adult Income dataset to understand which demographic, education, and work characteristics are associated with an annual income above USD 50K.

The project covers:

- Data collection
- Data cleaning
- Feature engineering
- Exploratory Data Analysis (EDA)
- Data visualization
- Summary of findings
- Limitations

## 2. Business Question

Which demographic, education, and work characteristics are associated with an annual income above USD 50K in this census dataset?

## 3. Dataset

The dataset used is the UCI Adult Income dataset.

### Dataset Details

- Source: UCI Machine Learning Repository
- Records: 48,842
- Original features: 14
- Target variable: Income
- Income groups: `<=50K` and `>50K`

The dataset contains numerical and categorical variables such as:

- Age
- Workclass
- Education
- Occupation
- Marital Status
- Relationship
- Race
- Sex
- Capital Gain
- Capital Loss
- Hours per Week
- Native Country

## 4. Data Collection

The dataset was collected from two official UCI files:

- `adult.data`
- `adult.test`

The two partitions were combined into a single dataset.

A `source_split` column was preserved to identify whether each record came from the training or test partition.

## 5. Data Cleaning

The following cleaning steps were performed:

1. Removed leading and trailing whitespace from categorical values.
2. Converted `?` and empty values to missing values.
3. Replaced missing `workclass`, `occupation`, and `native_country` values with `Unknown`.
4. Converted numeric columns using numeric coercion.
5. Converted numeric columns using numeric coercion and checked for invalid or impossible values. No invalid core numeric rows were found.
6. Identified 29 exact duplicate rows.
7. Retained duplicate rows because the dataset does not contain a unique person identifier.
8. Removed the trailing period from income labels in the test data.
9. Created the `high_income` binary target variable.

## 6. Feature Engineering

The following features were created:

### high_income

- `1` = income greater than USD 50K
- `0` = income less than or equal to USD 50K

### age_group

Age was divided into defined age bands:

- 18-25
- 26-35
- 36-45
- 46-55
- 56-65
- 66+

### hours_group

Weekly working hours were divided into:

- 0-20
- 21-40
- 41-60
- 61+

### net_capital

Calculated as:

`capital_gain - capital_loss`

## 7. Exploratory Data Analysis

The following questions were analyzed:

1. What proportion of records have income greater than USD 50K?
2. How does the income >50K rate vary by education?
3. How does the income >50K rate vary by occupation?
4. How does the income >50K rate vary by age group?
5. How does the income >50K rate vary by workclass?
6. How does the income >50K rate vary by sex?
7. How do weekly working hours differ between income groups?
8. What numeric relationships exist between important variables?

## 8. Key Findings

- Higher education levels generally show higher >50K income rates in this dataset.
- Income >50K rates vary across occupation categories.
- Income >50K rates vary across age groups.
- Income >50K rates vary across workclass categories.
- Income >50K rates differ between male and female groups in this dataset.
- The >50K group has a higher average number of weekly working hours.
- Numeric variables show different levels of association with high income.

These findings describe associations in the dataset and do not establish causation.

## 9. Project Structure

```text
adult_income_eda_project/
│
├── data/
│   ├── adult_raw.csv
│   └── adult_income_cleaned.csv
│
├── reports/
│   ├── charts/
│   │   ├── 01_overall_income_distribution.png
│   │   ├── 02_income_by_education.png
│   │   ├── 03_income_by_occupation.png
│   │   ├── 04_income_by_age_group.png
│   │   ├── 05_income_by_workclass.png
│   │   ├── 06_income_by_sex.png
│   │   ├── 07_working_hours_by_income.png
│   │   └── 08_numeric_correlation_heatmap.png
│   │
│   ├── screenshots/
│   ├── tables/
│   └── Adult_Income_EDA_Report.pdf
│
├── source/
│   ├── data_cleaning.ipynb
│   ├── data_analysis.ipynb
│   └── build_pdf_report.py
│
├── README.md
└── requirements.txt
```

## 10. Reports and Outputs

The project generates:

- Cleaned dataset
- EDA charts
- EDA summary table
- Cleaning log
- PDF analysis report

The main PDF report is:


- `reports/tables/cleaning_log.csv`
- `reports/tables/eda_summary.csv`

## 11. Limitations

- The dataset is historical and may not represent current income patterns.
- The analysis identifies associations and does not establish causation.
- Demographic variables should be interpreted carefully.
- The visualizations are unweighted summaries and do not account for survey/sample weights.
- This project focuses on descriptive analysis and does not build a predictive model.

## 12. Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Jupyter Notebook
- ReportLab

## 13. How to Run the Project

### Step 1: Install dependencies

```bash
pip install -r requirements.txt
```

### Step 2: Run data cleaning

Open:

`source/data_cleaning.ipynb`

Run the notebook to create the cleaned dataset.

### Step 3: Run data analysis

Open:

`source/data_analysis.ipynb`

Run the notebook to perform EDA and generate charts and summary tables.

### Step 4: Generate the PDF report

From the project root folder, run:

```bash
python source/build_pdf_report.py
```

The PDF report will be created inside the `reports` folder.

## 14. Conclusion

The exploratory analysis shows that income >50K is associated with differences across education, occupation, age group, workclass, sex, and weekly working hours in this dataset.

These findings are descriptive associations rather than causal relationships. The cleaned dataset and analysis provide a foundation for further statistical analysis or predictive modeling.
