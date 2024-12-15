# # README: NPRI Data Analysis

## Project Overview
The **National Pollutant Release Inventory (NPRI)** is Canada’s primary database for tracking pollutants released to air, water, and land, as well as waste disposed of or transferred for recycling. Managed by **Environment and Climate Change Canada (ECCC)**, it helps monitor industrial activities and supports public transparency, regulatory compliance, and environmental decision-making.

This project analyzes NPRI data spanning over two decades (2000–2022) to extract meaningful insights, identify patterns, and address issues affecting environmental health and sustainability in Canada.

---

## Purpose of NPRI Data
### Key Uses:
1. **Environmental Protection**: Tracks pollution to inform policy-making.
2. **Public Right-to-Know**: Provides transparency on pollutant emissions.
3. **Regulatory Insight**: Ensures compliance with environmental standards.
4. **Research and Decision-Making**: Supports academics, NGOs, and policymakers.
5. **Progress Tracking**: Monitors trends and evaluates the effectiveness of environmental programs.

---

## Dataset Description
The NPRI dataset consists of three main components:

### 1. **Releases**
- **Industries Covered**: Conventional oil and gas extraction, fossil fuel power generation, chemical pulp mills, and petroleum refineries.
- **Common Substances**:
  - Particulate Matter (≤ 2.5 μm, ≤ 10 μm)
  - Nitrogen Oxides (NOx)
  - Carbon Monoxide (CO)
  - Volatile Organic Compounds (VOCs)
- **Size**: 737,516 rows; 28 columns
- **Units**: Includes tonnes, kilograms, grams, etc.
- **Spatial Information**: Facility locations (province, city, latitude, longitude).

### 2. **Disposals and Transfers**
- **Industries Covered**: Sewage treatment facilities, waste disposal, petroleum refineries, and chemical pulp mills.
- **Common Substances**:
  - Lead, Zinc, Copper, Xylene, Manganese
- **Size**: 191,645 rows; 41 columns
- **Units**: Varying units (e.g., tonnes, kg, grams).
- **Geography**: Province and city-level data.

### 3. **Comments**
- **Key Information**: Annotations about particulate matter, NOx, CO, and other pollutants.
- **Size**: 363,310 rows; 14 columns

---

## Insights from Data
### Key Findings:
1. **Industry-Specific Impact**:
   - Identified top pollutant-emitting industries.
   - Tracked trends over time for emission reductions.

2. **Geographic Hotspots**:
   - Mapped pollution-intense regions across Canada.

3. **Compliance Monitoring**:
   - Evaluated industry adherence to regulations.

4. **Sustainability Progress**:
   - Assessed progress toward reducing pollution over the 20-year period.

---

## Issues Detected
### 1. **Missing Data**:
- Some columns, such as *"Release to Air - Fugitive"* and *"Releases to Land - Leaks"*, have over 95% missing values.

### 2. **Inconsistent Units**:
- Substances are reported in varying units, making aggregation challenging.

### 3. **Invalid CAS Numbers**:
- Some CAS numbers are improperly formatted, impacting chemical identification.

### 4. **Incomplete Aggregates**:
- The *"Sum of release to all media (<1 tonne)"* column has substantial blanks.

### 5. **Geographic Data Accuracy**:
- Latitude and longitude values may lack verification.

### 6. **Estimation Method Ambiguity**:
- Estimation methods (e.g., *"M"* for monitoring, *"E"* for emission factor) need clearer definitions.

### 7. **Formatting Issues**:
- Inconsistent naming of substances (e.g., *"Methanol"* vs. *"Methanol (and its salts)"").

---

## Data Exploration Process
### Steps Taken:
1. **Dataset Loading**:
   ```python
   df_releases = pd.read_csv('NPRI_Releases.csv', encoding='latin-1')
   pd.set_option('display.max_columns', None)
   ```
2. **Shape and Structure**:
   - Shape: *(737,516 rows, 28 columns)*
   - Column Names:
     ```python
     df_releases.columns
     ```
3. **Data Types and Info**:
   ```python
   df_releases.info()
   ```
4. **Duplicate Check**:
   ```python
   df_releases.duplicated().sum()
   ```
   *Result*: No duplicate rows.
5. **Missing Values**:
   ```python
   df_releases.isnull().sum()
   ```
6. **Summary Statistics**:
   ```python
   df_releases.describe()
   ```

---

## Tools and Libraries Used
### Python Libraries:
- **Pandas**: Data manipulation and analysis
- **NumPy**: Numerical computing
- **Matplotlib** & **Seaborn**: Data visualization
- **Plotly**: Interactive visualizations
- **Scikit-learn**: Data preprocessing
- **Statsmodels**: Statistical analysis

---

## Future Work
### Planned Improvements:
1. **Standardize Units**:
   - Convert all values to a single unit for easier comparison.
2. **Enhance Data Imputation**:
   - Address missing values with advanced imputation methods.
3. **Improve Geographic Accuracy**:
   - Verify and clean latitude/longitude data.
4. **Clarify Estimation Methods**:
   - Provide clearer definitions for estimation codes.
5. **Develop Dashboards**:
   - Create interactive dashboards to visualize trends.

---



