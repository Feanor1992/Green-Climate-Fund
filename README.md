# Green-Climate-Fund

## Code Overview ##

1. **Importing Libraries and Loading Data**
    - ***Libraries:*** The code uses the `pandas` library for data manipulation, `plotly.express` for creating visualizations, and `dash` for building an interactive web-based dashboard.
    - ***Data Loading:*** The dataset is loaded from a CSV file (`green_climate_fund.csv`) into a Pandas DataFrame (`df`).
2. **Data Cleaning and Transformation**
    - ***Numeric Conversion:*** The columns `RP Financing $`, `FA Financing $`, and `Total Financing $` are converted to numeric using `pd.to_numeric` to ensure proper handling of financial data.
    - ***Creating Derived Columns:*** A new column, `Total Financing $`, is created by summing `RP Financing $` and `FA Financing $` for each country.
3. **Exploratory Data Analysis (EDA)**
    - ***Regional Analysis:***
        - The data is grouped by `Region` to calculate:
            - Total financing per region (`total_financing`).
            - Average financing per region (`avg_financing`).
            - The number of countries in each region (`num_countries`).
        - The resulting `region_summary` DataFrame is used for regional visualizations.
    - ***SIDS and LDCs Analysis:***
        - The data is grouped by `SIDS` and `LDCs` to analyze financing for these vulnerable groups.
        - The resulting `sids_ldcs_summary` DataFrame includes total and average financing and the count of countries in these categories.
    - ***Top Countries by Financing:***
        - The top 10 countries with the highest `Total Financing $` are identified using `nlargest`.
        - The resulting `top_countries` DataFrame includes `Country Name` and `Total Financing $`.
    - ***Financing Distribution Statistics:***
        - Summary statistics (`describe`) for `RP Financing $` and `FA Financing $` are calculated and formatted with two decimal places for clarity.
4. **Data Visualization**
    - ***Choropleth Map:*** A world map visualizes `Total Financing $` distribution, where countries are shaded based on the intensity of financing received. The map uses lighter color tones (`color_continuous_scale="Mint"`) for better visibility on a dark background.
    - ***Financing Distribution Bar Chart:*** A grouped bar chart compares `RP Financing $` and `FA Financing $` for each country.
    - ***Regional Analysis Bar Chart:*** A bar chart displays total financing by region, with bars colored by average financing and annotated with the number of countries per region.
    - ***SIDS and LDCs Analysis Bar Chart:*** A bar chart highlights financing distribution based on the `SIDS` and `LDCs` categories.
    - ***RP vs FA Scatter Plot:*** A scatter plot compares `RP Financing $` (`x-axis`) and `FA Financing $` (`y-axis`), with bubble size proportional to `Total Financing $` and colors representing regions.
5. **Dashboard Creation with Dash**
    - ***Tabs Layout:*** The dashboard is structured into four interactive tabs, each designed for a specific aspect of the data:
        - *Tab 1:* Global financing distribution (map and bar chart).
        - *Tab 2:* SIDS and LDCs financing.
        - *Tab 3:* Regional analysis.
        - *Tab 4:* Comparison of RP and FA financing.
    - ***Styling:*** 
        - A dark theme is applied throughout the dashboard for a modern aesthetic.
        - Text descriptions are added to provide context for each tab.
    - ***Interactivity:***
        - The dashboard is fully interactive, allowing users to explore the data dynamically.
