# QuickBasket Analytics — Sales & Profitability Analysis
1. Project Overview
QuickBasket is a simulated quick-commerce grocery business operating across six Indian cities. The business has substantial sales activity, but management wants to understand whether that growth is translating into healthy profitability.
Business question
> \*\*Where is QuickBasket creating revenue, where is it losing margin, and what should management change next?\*\*
This project demonstrates an entry-level analyst workflow using Python and Pandas:
Clean → Validate → Calculate → Compare → Visualize → Conclude
---
2. Objectives
The analysis focuses on:
Cleaning and validating messy transactional data
Measuring revenue, orders, AOV, gross margin and margin %
Comparing business performance across cities and months
Understanding the relationship between discounts and profitability
Identifying profitable and loss-making product categories
Identifying products with high margin contribution
Examining delivery time and customer ratings
Applying RFM customer segmentation as an optional extension
---
3. Dataset
The project uses five CSV files:
File	Approx. rows	Grain
`customers.csv`	6,000	One registered customer
`products.csv`	139	One product / SKU
`orders.csv`	25,028	One order
`order\_items.csv`	101,989	One product line inside an order
`marketing\_spend.csv`	21,930	One marketing channel/city/day record
The dataset is synthetic/simulated and is intended for analytics practice. It should not be presented as real QuickBasket company data.
See `data\_dictionary.md` for column-level definitions.
---
4. Tools Used
Python
Pandas
NumPy
Matplotlib
Jupyter Notebook / Google Colab
---
5. Analysis Workflow
Phase 1 — Data Cleaning & Validation
The notebook checks and handles:
Dataset shapes and data types
Missing values
Duplicate records
Duplicate order IDs
Inconsistent city labels
Mixed date formats
Invalid quantities and prices
Unrealistic delivery times
Cancelled and returned orders
Table joins and master-table validation
The profitability analysis uses delivered orders as the revenue base. Cancelled and returned orders remain available in the source order table for operational analysis.
Phase 2 — Business Performance
The notebook calculates:
Total revenue
Total delivered orders
Average Order Value (AOV)
Total gross margin
Overall margin %
Active customers
Monthly revenue and margin trend
Weekday vs weekend behaviour
Phase 3 — Profitability Deep Dive
The core diagnostic analysis covers:
City profitability — revenue, margin %, AOV and delivery time
Discount analysis — revenue, margin %, margin and revenue share by discount band
Category profitability — revenue, margin and margin % by category
Product contribution — products ranked by margin contribution
Delivery experience — relationship between delivery time and customer rating
Phase 4 — Customer Analytics (Optional Extension)
RFM analysis is included as an extension:
Recency
Frequency
Monetary value
RFM scoring
Customer segmentation
It is not required to understand the core profitability story.
---
6. Key Findings
Based on the current dataset and cleaned delivered-order analysis:
Revenue is approximately ₹10.15 crore.
Gross margin is approximately ₹1.01 crore, giving an overall margin of about 9.91%.
Average Order Value is approximately ₹4,412.
Hyderabad is the only city with a negative margin percentage, at approximately −5.88%.
Mumbai has the strongest city margin percentage at approximately 18.52%.
Margin becomes negative in the 21–30% and >30% discount bands.
The two highest discount bands together account for about 19.86% of revenue.
Staples is the largest revenue category but has a negative margin percentage of approximately −1.70%.
Personal Care has the strongest category margin percentage at approximately 28.55%.
Delivery time and customer rating have a strong negative correlation of approximately −0.75 in this dataset.
These findings should be read together rather than in isolation. Revenue size, profitability, basket size, discounting and service performance answer different business questions.
---
7. Business Recommendations
1. Review high-discount transactions
Margins turn negative at higher discount levels. Management should test a controlled discount ceiling and use targeted promotions rather than broad discounts where the economics do not work.
2. Investigate Hyderabad separately
Hyderabad has negative margin. Its problem should be diagnosed using AOV, delivery time and product mix before choosing an intervention. A city-level problem should not automatically be treated as a discount problem.
3. Protect profitable categories and products
High-margin categories and high-contribution products should receive appropriate inventory and assortment attention. Cross-selling can also be used to improve basket economics.
4. Improve delivery performance
The strong negative association between delivery time and rating indicates that service speed deserves operational attention. The result is an association, not proof that delivery time alone causes lower ratings.
---
8. Visualizations
The portfolio notebook includes charts for:
Monthly revenue and margin %
City margin %
Margin % by discount band
Category revenue and margin %
Top products by margin
Delivery time vs customer rating
The charts are generated directly in the notebook using Matplotlib, so they can be reproduced when the notebook is run.
---
9. Repository Structure
```text
QuickBasket-Analytics/
│
├── QuickBasket\_Portfolio.ipynb
├── README.md
├── data\_dictionary.md
├── requirements.txt
│
├── customers.csv
├── products.csv
├── orders.csv
├── order\_items.csv
└── marketing\_spend.csv
```
`QuickBasket.ipynb` can be retained as the original learning notebook if desired. `QuickBasket\_Portfolio.ipynb` is the polished portfolio version.
---
10. How to Run
Google Colab
Upload the notebook and all five CSV files into the same working directory.
Open `QuickBasket\_Portfolio.ipynb`.
Run the notebook from top to bottom.
Review the tables, charts, executive summary and recommendations.
Local Jupyter
Install the required packages:
```bash
pip install -r requirements.txt
```
Place the five CSV files in the same folder as the notebook and run the notebook from top to bottom.
---
11. Interview Talking Points
Be prepared to explain:
Why duplicate records can inflate revenue
Why date parsing requires validation
Why missing ratings should not be replaced with an invented rating
Why cancelled/returned orders are excluded from the delivered-sales base
Why the order-item grain affects AOV calculation
The difference between revenue, cost, margin and margin %
Why discount bands are useful
Why high revenue does not necessarily mean high profitability
What Pareto analysis tells management
What a negative correlation means and why it does not prove causation
How Recency, Frequency and Monetary value work in RFM
---
12. Limitations
The dataset is synthetic and therefore does not represent real company performance.
Gross margin here is based on product cost and does not represent full operating profit.
Correlation analysis does not establish causality.
The RFM segment rules are project-specific business rules.
Marketing spend is included in the data package but is not part of the core portfolio analysis.
---
13. Project Outcome
The project demonstrates how an analyst can move from messy transactional data to:
Reliable data → Business metrics → Diagnostic analysis → Visual evidence → Management recommendations
