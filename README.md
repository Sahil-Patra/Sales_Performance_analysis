# Sales_Performance_analysis

Sales Performance Analysis is the process of evaluating and interpreting sales data to understand how well a business is achieving its sales objectives. This analysis provides insights into revenue generation, sales trends, and regional performance.

## Table of Contents
- [Overview](#Overview)
- [Objective](#Objective)
- [Key feature](#Key-Features)
- [DataSet](#dataset)
- [Data Cleaning and Preparation](#Data-Cleaning-and-Preparation)
- [Key Insights](#Key-Insights)
- [Future Enhancements](#Future-Enhancements)
- [Contact](#contact)

## Overview
This analysis involves examining key sales metrics to evaluate performance, uncover trends, and identify areas for improvement. It helps businesses make informed decisions to drive growth and efficiency.
 
## Project Objective
The primary objective of this project is to:
-  Identify successful strategies and replicate them.
-  Address underperformance in products, categories, or regions.
-  Optimize pricing, inventory, and marketing efforts.
-  Align business goals with actionable insights.

## Key Features
This project uses Python to collect, analyze, and visualize sales data. Key features include:
-  Trend Analysis: To track sales growth and also forecasting over time.
-  Correlation Analysis: Identify relationships between numerical variables such as sales, profit, discount, quantity, and profit_margin.
-  Performance Metrics: Easily accessible KPIs for decision-making.

## Dataset
The project is built using only one dataset, which is Superstore sales dataset, which includes detailed information about sales from 2019 to 2022. The dataset features:
- **order_id'** : It' a column with unique identifier for each order.
- **order_date** : It's a column that show the dates when the order was placed.
- **ship_date** : It's a column that show the dates when the order was shipped.
- **customer** : It's a column that shows the name or identifier of the customer who placed the order.
- **manufactory** : It's a column that shows the names of the manufacturer.
- **product_name** : It's a column that shows the name of the product
- **segment** : It's a column that shows the  market segments to which the customer belongs.
- **category** : It's a column that shows the category of the product.
- **subcategory** : It's a column that shows the subcategory of the product.
- **region'** It's a column that shows the region of the order was placed.
- **zip** : It's a column that shows the zip or postal code of the delivery address.
- **city** : It's a column that shows the names of city where the order was delivered.
- **state** : It's a column that shows the names of state where the order was delivered.
- **country** : It's a column that shows the names of country where the order was delivered.
- **discount** : It's a column that shows the discounts applied to the order.
- **profit** : It's a column that shows the profits generated by the order.
- **quantity** : It's a column that shows the number of products purchased in the order.
- **sales'** : It's a column that shows the total revenue generated from the order.
- **profit_margin** : It's a column that shows the ration of profit to sales genereated from the order.

##Project
  ## **Project** : - [Sales Performance Analysis](assets/Jupyter_note/S_P_A.ipynb)
  
## Project Code

```python
total_sales = df['sales'].sum()
total_profit = df['profit'].sum()

print(f"Total Sales: ${total_sales:.2f}")
print(f"Total Profit: ${total_profit:.2f}")
```

Total Sales: $2297200.86
Total Profit: $286397.02

```python
top_products = df.groupby('product_name')['sales'].sum().sort_values(ascending=False).head(10)
print("Top Products:\n", top_products)
```

| product_name | Sales |
| ----------------------------------------------------------------------------- | --------- |
| Canon imageCLASS 2200 Advanced Copier                                         | 61599.824 |
| Fellowes PB500 Electric Punch Plastic Comb Binding Machine with Manual Bind   | 27453.384 |
| Cisco TelePresence System EX90 Videoconferencing Unit                         | 22638.480 |
| HON 5400 Series Task Chairs for Big and Tall                                  | 21870.576 |
| GBC DocuBind TL300 Electric Binding System                                    | 19823.479 |
| GBC Ibimaster 500 Manual ProClick Binding System                              | 19024.500 |
| Hewlett Packard LaserJet 3310 Copier                                          | 18839.686 |
| HP Designjet T520 Inkjet Large Format Printer - 24" Color                     | 18374.895 |
| GBC DocuBind P400 Electric Binding System                                     | 17965.068 |
| High Speed Automatic Electric Letter Opener                                   | 17030.312 |

```python
top_regions = df.groupby('region')['sales'].sum().sort_values(ascending=False)
print("Top Regions:\n", top_regions)
```

| region | Sales |
|----------|------------|
| West     |  725457.8245
| East     |  678781.2400
| Central  |  501239.8908
| South    |  391721.9050

```python
products = df.groupby('product_name')['profit'].sum().sort_values(ascending=False).head(10)
print("Top Products:\n", products)
```

| product_name | Profit |
| ---------------------------------------------------------------------------- | ---------- |
| Canon imageCLASS 2200 Advanced Copier                                        | 25199.9280 |
| Fellowes PB500 Electric Punch Plastic Comb Binding Machine with Manual Bind  |  7753.0390 |
| Hewlett Packard LaserJet 3310 Copier                                         |  6983.8836 |
| Canon PC1060 Personal Laser Copier                                           |  4570.9347 |
| HP Designjet T520 Inkjet Large Format Printer - 24" Color                    |  4094.9766 |
| Ativa V4110MDD Micro-Cut Shredder                                            |  3772.9461 |
| 3D Systems Cube Printer, 2nd Generation, Magenta                             |  3717.9714 |
| Plantronics Savi W720 Multi-Device Wireless Headset System                   |  3696.2820 |
| Ibico EPK-21 Electric Binding System                                         |  3345.2823 |
| Zebra ZM400 Thermal Label Printer                                            |  3343.5360 |


```python
regions = df.groupby('region')['profit'].sum().sort_values(ascending=False)
print("Top Regions:\n", regions)
```

| region | Pofit |
| -------- | ----------- |
| West      | 108418.4489 |
| East      |  91522.7800 |
| South     |  46749.4303 |
| Central   |  39706.3625 |

```python
sns.barplot(x='discount', y='sales', data=df)
plt.title('Discount vs Sales')
plt.show()
```

![Profit Margin By Category](assets/Jupyter_note/S_S/Bar.png)

```python
category_margin = df.groupby('category')['profit_margin'].mean()
print("Average Profit Margin by Category:\n", category_margin)

sns.barplot(x=category_margin.index, y=category_margin.values)
plt.title('Profit Margin by Category')
plt.show()
```


| category | Average Profit |
| ----------------- | -------- |
| Furniture         | 0.038784 |
| Office Supplies   | 0.138030 |
| Technology        | 0.156138 |

![Profit Margin By Category](assets/Jupyter_note/S_S/proft_margin.png)

```python
numerical_cols = ['sales', 'profit', 'discount', 'quantity', 'profit_margin']
correlation_matrix = df[numerical_cols].corr()
plt.figure(figsize=(8, 6))
sns.heatmap(correlation_matrix, annot=True, cmap='Greens', fmt='.2f')
plt.title('Correlation Matrix')
plt.show()
```

![Profit Margin By Category](assets/Jupyter_note/S_S/Correlation_Matrix.png)

```python
monthly_sales = ddf.groupby(pd.Grouper(key='order_date', freq='M'))['sales'].sum()

### Decompose the time series
'''Python
result = seasonal_decompose(monthly_sales, model='additive', period=12)
result.plot()
plt.show()
```

![Profit Margin By Category](assets/Jupyter_note/S_S/Seasonal_Trend.png)

### Forecasting with Holt-Winters
```python
model = ExponentialSmoothing(monthly_sales, trend='add', seasonal='add', seasonal_periods=12).fit()
forecast = model.forecast(12)
```

### Plot forecast
```python
plt.figure(figsize=(12,6))
plt.plot(monthly_sales, label='Actual Sales')
plt.plot(forecast, label='Forecasted Sales', linestyle='--')
plt.legend()
plt.title('Sales Forecast')
plt.show()
```

![Profit Margin By Category](assets/Jupyter_note/S_S/Forcasting.png)

```python
ddf['year_month'] = ddf['order_date'].dt.to_period('M')
monthly_sales = ddf.groupby('year_month')['sales'].sum().reset_index()
monthly_sales['sales_growth'] = monthly_sales['sales'].pct_change() * 100
```

```python
from statsmodels.tsa.stattools import adfuller

print('Results of Dickey-Fuller Test:')
dftest = adfuller(df['sales'], autolag = 'AIC')

dfoutput = pd.Series(dftest[0:4], index = ['Test Statistic' , 'p-value', '#lags Used', ' Number of Observations Used'])
for key, value in dftest[4].items():
    dfoutput['Critical Value (%s)' %key] = value
```

|Results of Dickey-Fuller Test |  |
| ------------------------------ | ----------- |
| Test Statistic                 |  -98.890821 |
| p-value                        |    0.000000 |
| #lags Used                     |    0.000000 |
| Number of Observations Used    | 9993.000000 |
| Critical Value (1%)            |   -3.431005 |
| Critical Value (5%)            |   -2.861829 |
| Critical Value (10%)           |   -2.566924 |


## Key Insights
1. Certain proucts with categories and geographic regions show higher profit rates.
2. Revenue Trends: Identification of sales trends over time (e.g., monthly, quarterly, yearly).
3. Top-Performing Products: Products with the highest revenue contribution.
4. Average order value (AOV) and frequency of purchases.
5. High-performing regions contributing most to sales.
6. Insights into profit margins across products and regions.
8. Potential areas for expansion or increased investment.

## Future Enhancements
- **Refression Modeling**: Integrate machine learning models to predict sales growth
- **Incorporate Real-Time Data**: Enhance the dashboards with real-time data feeds for dynamic sales analysis.

## Contact
- [Sahil Patra]
- [+91 7735367833]
- [sahilpatra1004@gmail.com]
- [[LinkedIn Profile](https://www.linkedin.com/in/sahil-patra10)]

## Acknowledgements
- Thanks to the youtube community for valuable tutorials and resources.
- Special mention to open data sources for providing the superstore sales dataset.

---

