# 🌍 Global Development Insights
### World Bank Indicators Analysis | Python · Power BI · DAX · REST API

![Recording 2026-02-23 235038 (1)](https://github.com/user-attachments/assets/ee73dc22-2f8c-4eef-860f-32e5b56ad3a9)


---

## 📌 Overview

An end-to-end data analytics project that fetches real-world development data from the **World Bank public API**, processes it using Python, and presents insights through an **interactive Power BI dashboard**.

The dashboard analyses **26 key development indicators** across **200+ countries** from **2016 to 2024**, covering health, economic activity, trade, poverty, environment, labour market, and technology dimensions.

---



## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Python** | Data collection via REST API |
| **Pandas** | Data cleaning, transformation, merging |
| **Requests** | API calls with pagination handling |
| **Seaborn** | Correlation heatmap and regression scatter |
| **Matplotlib** | Custom chart styling |
| **Power BI** | Interactive dashboard and data model |
| **DAX** | Custom measures (Poverty Reduction %) |

---
## 🔍 Key Findings

- 💧 **Water access** predicts life expectancy more strongly than health spending (r ≈ 0.8)
- 🌐 **Internet penetration** correlates positively with higher immunisation rates globally
- 🏥 **Sub-Saharan Africa** allocates the highest share of GDP to health (18.44%) yet continues to face the highest disease burden
- 📈 **Health expenditure positively correlates with life expectancy**, Though with significant variation, higher spending alone does not
  guarantee better outcomes
- 📱 **Mobile subscriptions** have grown steadily since 2016, with rates
  exceeding 100% in several countries due to multi-SIM usage

---

## 🗂️ Project Structure

```
WorldBank-Development-Dashboard/
│
├── API_Data.ipynb          # Complete data collection and cleaning pipeline
│
├── data/
│   ├── economic.csv        # GDP growth and GDP per capita
│   ├── health.csv          # 13 health indicators
│   ├── trade.csv           # Exports and imports
│   ├── labour_market.csv   # Unemployment and labour force
│   ├── poverty.csv         # Poverty headcount and Gini index
│   ├── environment.csv     # Renewable energy and forest area
│   └── technology.csv      # Internet usage and mobile subscriptions
│
├── screenshots/
│   ├── Screenshot Page 2  # Full dashboard view
│   └── Screenshot Page 1        
│     
│
├── requirements.txt        # Python dependencies
└── README.md               # Project documentation
```

---

## ⚙️ How to Run

### 1. Clone the repository
```bash
git clone https://github.com/Sonusrj/WorldBank-Development-Dashboard.git
cd WorldBank-Development-Dashboard
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the notebook
```bash
jupyter notebook API_Data.ipynb
```
Run all cells — this will fetch data from the World Bank API and generate all 7 CSV files.

> ⏱️ **Note:** Full data fetch takes approximately 10–15 minutes due to API pagination across 500+ pages.

### 4. Open the dashboard
Open `WorldBank_Dashboard.pbip` in **Power BI Desktop** and refresh the data source to point to your local CSV files.

---

## 📐 Data Architecture

### Pipeline Stages

```
World Bank API
      │
      ▼
Python (requests + pandas)
      │
      ├── countries DataFrame    (296 countries)
      ├── indicators catalog     (26,223 indicators → saved as final_df.csv)
      └── 7 category DataFrames  (~57,000+ rows total)
              │
              ▼
         7 clean CSV files
              │
              ▼
         Power BI (Star Schema)
              │
              ├── countries (Dimension table — 1 side)
              └── 7 fact tables (Many side)
                  connected via country_id
```

### Star Schema Model

```
              countries (DIM)
                    │
        ┌───────────┼───────────┐
        │           │           │
     health      economic    trade
     (FACT)      (FACT)      (FACT)   ...and 4 more
```

---

## 📡 Data Source

- **Source:** [World Bank Open Data API](https://api.worldbank.org/v2/)
- **Coverage:** 200+ countries and territories
- **Period:** 2016 – 2024
- **Indicators:** 26 handpicked from 26,223 available indicators
- **API Format:** JSON with pagination (`per_page=500`)

---

## 🔮 Future Improvements

- [ ] Add time-series forecasting for key indicators
- [ ] Cluster countries by development profile using K-Means
- [ ] Add country-level drill-through pages

---

## 📬 Contact

**Sonu Saroj**
[LinkedIn](https://www.linkedin.com/in/sonu-saroj-0459b9243/)
