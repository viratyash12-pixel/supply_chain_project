# supply_chain_project
Python data visualization of the DataCo supply chain dataset (180K orders): late delivery rates, shipping performance, sales trends and category profit.
# 📦 DataCo Supply Chain: Exploratory Data Analysis

Exploratory analysis of the DataCo Global supply chain dataset in Python. The notebook covers data loading, cleaning, feature engineering and a first look at how delivery delays relate to profit.

## 🗂️ Dataset

- **Source:** DataCo Global Supply Chain Dataset (CSV, not included in this repo because of its size)
- **Size:** 180,519 order line items, 53 columns
- **Covers:** orders, customers, products, shipping modes, delivery status, sales and profit across five markets (LATAM, Europe, Pacific Asia, USCA, Africa)

Download the CSV and set the path in the `pd.read_csv(...)` cell before running.

## 🔍 What the notebook does

1. 📥 **Load and inspect:** shape, dtypes, descriptive statistics, duplicates and missing values.
2. 🧹 **Clean:** drops 20 columns that are personal data (customer email, password, name, street), redundant, empty or single-valued, then converts the order and shipping dates to datetime.
3. 📊 **Profile categoricals:** value counts for low-cardinality columns such as payment type, shipping mode, delivery status, market and order status.
4. 🛠️ **Engineer features:** order processing time (shipping date minus order date), a delayed flag from `Late_delivery_risk`, order month, day and hour, and a profit / loss / breakeven flag from `Order Profit Per Order`.
5. 📈 **Analyze:** profit distribution, and profit compared between late and on-time deliveries.

## 💡 Findings so far

| Metric | Result |
|---|---|
| ✅ Profitable order lines | 145,558 (80.6%) |
| ❌ Loss-making order lines | 33,784 (18.7%) |
| ⚖️ Breakeven order lines | 1,177 (0.7%) |
| 🚚 Late deliveries | 98,977 lines (54.8%) |
| ⏰ Mean profit, late orders | $21.62 |
| ✅ Mean profit, on-time orders | $22.40 |

Late orders earn only slightly less per line ($0.78 on average), so delays alone don't explain the losses. That points to discounts, product category or shipping mode as the next things to check.

Other notes from the profiling step:
- 🚛 Standard Class is the most used shipping mode (107,752 lines), followed by Second Class, First Class and Same Day.
- 📅 Scheduled shipping time is 4 days for about 60% of orders.
- 🚫 `Product Status` has a single value across all rows, so it carries no information.

## 🧰 Tech stack

Python 🐍, pandas 🐼, NumPy, matplotlib, seaborn

## ⚙️ Setup

```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook supply_chain.ipynb
```

## 🚀 Next steps

- 🔎 Break profit down by shipping mode, category and market
- 📆 Add a time series of sales and profit (note that the data structure changes from Oct 2017, when orders move to one item per order)
- 🤖 Model late-delivery risk with a classifier

## 🔒 Data privacy

The raw file includes customer names and street addresses. Don't commit the CSV to a public repo.
