# Predicting Customer Lifetime Value (CLV)

## Installation
- Python 3.7.3
- Data: [Online Retail II Data Set, UCI Machine Learning Repository](http://archive.ics.uci.edu/ml/datasets/Online+Retail+II)
- Libraries: pandas, NumPy

## File Descriptions
Because the dataset is large and publicly available, I did not upload it here. 

The analysis can be found as Jupyter Notebook here:

* [CLV_prediction.ipynb](https://github.com/k-bosko/CLV_prediction/blob/master/CLV_prediction.ipynb)

## Project Description
In this project, I analyzed customer behavior for online retail store that sells unique all-occasion gift-ware in the UK. 

The dataset consists of 1,067,371 transactions and has the following variables:

| Variable | Description |
| :--- | :--- |
| **InvoiceNo** | Invoice number. Nominal. A 6-digit integral number uniquely assigned to each transaction. If this code starts with the letter 'c', it indicates a cancellation.|
| **StockCode** | Product (item) code. Nominal. A 5-digit integral number uniquely assigned to each distinct product. <br>
| **Description** | Product (item) name. Nominal.|
| **Quantity** | The quantities of each product (item) per transaction. Numeric.|
| **InvoiceDate** | Invice date and time. Numeric. The day and time when a transaction was generated. |
| **UnitPrice** | Unit price. Numeric. Product price per unit in sterling. |
| **CustomerID** | Customer number. Nominal. A 5-digit integral number uniquely assigned to each customer.|
| **Country** | Country name. Nominal. The name of the country where a customer resides.|



I calculated three types of revenue-based CLV, assuming Average Lifespan for Basic and Granular CLV being 36 months:

**Basic CLV** = Average Revenue per Month * Average Lifespan <br>

**Granular CLV** = (Average Revenue per Transaction * Average Frequency per Month) * Average Lifespan <br>

**Traditional CLV** = Average Revenue * (Retention Rate / Churn Rate)


## Results

Basic CLV gave unrealistically high CLV - 21725.62 USD per customer. Granular CLV is much lower - with only 1865.33 USD per customer. Still, both Basic and Traditional CLV relied on an arbitrary value of lifespan per customer, which we assumed here to be 3 years. <br>

Traditional CLV, however, gave a more realistic number - only 141.69 USD per customer and was based on the real retention to churn ratio as a proxy for the customer lifespan. <br>

Still, the traditional CLV method assumed that the churn is final, i.e. customers that churn do not come back later. Hence, it might underreport actual CLV, especially with low retention rates as in our case (19%).

## Acknowledgement

This project is part of ["Machine Learning for Marketing" course on Data Camp](https://learn.datacamp.com/courses/machine-learning-for-marketing-in-python) taught by Karolis Urbonas, Global Head of Machine Learning and Science at Amazon Web Services (AWS).
