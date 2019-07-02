# DATA_SCIENTIST_Customer_Segmentation
This project is part of the Openclassrooms DataScientist Curriculum together with CentraleSupélec

### by Jérôme d'Harveng

## Dataset

> For this project, we used a DB of more than 500.000 commercial transactions of a retail company in the UK between December 2010 and September 2011. The **goal** here was knowing one or a few commercial transactions of a customer being able to classify him in a certain segment.

## Feature Engineering before exploration:
> We added the variable _total value_ of an orderline being the _Quantiy_ times the _UnitPrice_.

## Data exploration:
> After having cleaned the data, and before moving to the customer segmentation itself, we first did some exploration to get a better understanding of our data.

> _Some interesting insights concerning the invoices in this DB were:_
> - Logically the country with most order lines is UK. But if we take a look at the countries starting from the second position, we see for example that although Germany is the second country with most order lines, it’s the Netherlands which is the second with most sales.
> - If we look at the ranking based on the average amount per invoice this time, Japan is first with more than 500 pounds and then comes the Netherlands with round 200 pounds.
> - 75% of the unit prices are lower than 3.75 pounds.
> - 50% of the order lines are concerning quantities less than 6 units and 75% less than 12 units.
> - Regarding the distribution of the total amount per order, we see that 50% of the orders cost less than 301.6 pounds and 75% less than 463 pounds.
> - Looking at the distribution of the sales over the different customers, we observe that the 10 best customers did 17.4% of the total sales that year.
> - During the week, _Tuesday and Thursday_ are the days with biggest percentage of the sales.
> - During the year, we see that most sales are concentrated _from September till December_.

## Feature Engineering specific to our customer segmentation 
> - First of all, to better characterize each customer, we used the RFM model. With **R** standing for **Recency**, and being the time since the last order (in days), **F** for **Frequency** being the total number of transactions and **M** for **Monetary** the total transactions value.
> - We added also for each customer the amount of different products, they had already ordered. Thinking that a customer buying only 1 type of product, could be perhaps less loyal than one buying several different products.


## Customers segmentation
> - We applied then a **K-means++** to our customer database characterized with the help of the feature engineering discussed before.
> - We used then the our different segments obtained as label for some **supervised ensemble methods**:
 - 1. _Random Forest_
 - 2. _Gradient Boosting_
> - We used _GradientSearchCV()_ for the tuning of the hyperparameters

## Evaluation metrics
> - For the evaluation part, we applied _cross-validation_, and used several different metrics such as _precision, recall, F1-score_ and the _confusion matrix_.
