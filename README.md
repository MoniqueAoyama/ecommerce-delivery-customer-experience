# Delivery Performance and Customer Experience in E-commerce

Final project for CS 661 (Python Programming) at Pace University.

This project looks at what makes customers leave bad reviews on Olist,
a Brazilian e-commerce marketplace. The data has about 96,000 delivered
orders from 2016 to 2018.

The main question was whether delivery problems explain bad reviews
better than things like price, freight cost or the number of items
in the order.

## What was done

- Merged the orders, order items and reviews tables by order ID
- Calculated delivery time and delivery delay from the order dates
- Marked reviews with a score of 1 or 2 as a poor experience
- Explored the data with plots and a correlation heatmap
- Trained a logistic regression and a random forest to predict
  poor experiences (80/20 split, balanced class weights)

## Findings

Delivery time and delay were the variables most related to bad reviews.
Order value, freight cost and item count made little difference.

Most orders arrived early, about 12 days before the estimated date on
average. The estimates seem to be set on the safe side.

| Model | Accuracy | Precision | Recall | ROC-AUC |
| --- | --- | --- | --- | --- |
| Logistic regression | 75.3% | 27.8% | 58.0% | 0.732 |
| Random forest | 88.7% | 63.3% | 28.0% | 0.722 |

The random forest had higher accuracy, but it missed most of the poor
experiences. Logistic regression found about twice as many, so it was
the better model for this problem.

## Limitations

Only about 13% of the orders are poor experiences, which makes them
harder to predict. Reviews also depend on things that are not in this
data, like product quality and how the seller communicated.

## How to run

Download these three files from the
[Olist dataset on Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
and put them in this folder:

- olist_orders_dataset.csv
- olist_order_items_dataset.csv
- olist_order_reviews_dataset.csv

Libraries used: pandas, NumPy, matplotlib, seaborn, scikit-learn
