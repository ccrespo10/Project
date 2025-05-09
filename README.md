# procurement KPI Analysis Project

## Introduction

This project explores a procurement dataset to support supplier relationship management and cost optimization. The goal is to identify key business issues such as:


- Underperforming suppliers
- Cost Ienfficiencies 
- Price inflation or weak negotiation strategies
- Future princing trends
- Ordering and delivery inefficiencies


The dataset is transformed through data analysis and visualization, allowing clear insights into supplier compliance, pricing behvior, deliceryperformance, and more.


## Key Questions
- How is this data set beneficial to solving our problem? 
- What are ways we could improve the data set? 
- Which vendors are high risk? And why are they high risk?
- How can we analyze the efficiency of the supply chain?
- What is the best way to optimize costs?
- What are the causes of policy violations and how often have they happened?
- What factors seem to worsen vendor performance?
- What factors seem to make vendor performance better?
- What could we predict about prices in the near future?
- Are there significant price increases over time for the same items? Savings from bulk orders? 
- Are there duplicate purchases that can be consolidated? Are there missing orders?



## Dataset Overview 

The dataset is loaded from a csv file and includes the sollowing columns: 
- 'PO_ID': Purchase Order ID
- 'Supplier': Vendor name
- 'Order_Date', 'Delivery_Date":Order and delivery timestamps
- 'Order_Status': Delivered/Cancelled
- 'Quantity': Number of units ordered
- 'Unit_Price', 'Negotiated_Price': Price Details
- 'Defective_Units': Faulty items received
- 'Compliance': Supplier compliance status(yes/no)




## Data processing and enrichment


- Predicted price: average of unit and negotiated prices

df['Predictions'] = df[['Unit_Price', 'Negotiated_Price']],mean(axis=1)


## Supply Chain efficiency - time difference between order and delivery

- df['supply_chain_efficiency] = (df['Delivery_Date']) - df(['Order_Date]).dt.days


## High-Risk Vendors
- df.groupby('supplier')['Defective_Units'].sum().sort_values(ascending=False)

Top high-risk suppliers by defective units:
1. Delta_Logistics - 19,678 Units
2. Beta_Supplies - 13,838 Units
3. Gamma_co - 7,034 units


Supply chain efficiency analysis
- df['Supply_Chain_Efficiency'] = (df['Delivery_Date'] - df['Order_Date']).dt.days

- Gamma_co has the fastest delivery times
- Alpha_Inc has delayed or missing deliveries




## Dataset improvement Suggestions

- Add columns for trend analysis
- Track inventory levels and reorder frequency
- Identify consolidation opportunities in duplicate orders


## Importance

- monitors supplier performance over time
- Detect risk factors before they escalate
- Make informed, cost-effective purchasing decisions
- Predict price trends and optimize for bulk savings 
- improve compliance and supplier relationships


## requirements.txt
- python-pandas, matplotlib
- jupyter notebook
- CSV data source

## Findings summary:

- 93% of orders either arrived late or contained defects, particularly seen with Epsilon_Group, Gamma_Co, and Beta_Supplies
- bulk purchases did not correlate with increased savings, impacting quality control at scale
- fluctuations in monthly negotiation prices which suggest poor contract terms or inconsistent planning
- Duplicate and missing orders suggest miscommunication, over-purchasing, and unreliable vendors

## Solutions


- Reassess vendors with high policy violation rates
- track vendor performance to ensure cost efficiency and renegotiation
- Reduce bulk orders during certain periods of fluctuations in pricing
- flag and review duplicate orders before processing
- create an alert system for incomplete or pending orders 
- analyze future price trends using patterns seen of the graphs and tables and use those statistics for future operation decisions
