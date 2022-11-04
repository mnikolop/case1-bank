# Next Best Offer (NBO) using the Bank of Portugal dataset

## Project description

This project was performed as an internal case for Adage ab. It aimed to create a Next Best Offer (NBO) model. It was run as a data science project simulating interactions with the client and processes.

Dataset: [UCI bank management data set](https://archive.ics.uci.edu/ml/datasets/bank+marketing)  
Duration: 2022.10.02 - 2022.11.03

---

# Project

## Situation

During a marketing campaign calls are made to customers to advertise the new product. Data is being collected from each of these calls that describes the customer, the call itself, the outcome of the campaign as well as that of the previous one.
At the moment, for each new campaign all customers are being contacted until

- they accept (yes)
- they decline (no)
- the campaign expires (unknown)

The data so far indicates that the customers decline more often than they accept the offering.

## Complication

Targeting all customers the same way does not yield a high success for the campaigns.
Allocating operatives to contact all customers consumes time they could have spent assisting existing customers. This results in higher ques in the call centers, resulting to lowered satisfaction rates from the customers. Additionally, the time spent calling customers that do not accept the offering is a lost investment since they do not generate any revenue.

## Question

NBO models give us the probability of a customer buying a specific product, based on information about them and their interactions with other products, They are mainly used to get a better insight into one's customers. Campaigns that have been run using NBO model recommendations, give the customer the feeling they have been tailored and personalized to their needs.  
We are hypothesizing that by using an NBO model to get recommendations on how likely is a customer to buy a product or not, we can increase the success rate of a marketing campaign.

## Answer

### Ways of working

This project was sun using the agile methodology.

### Analytics process

<img src='presentations\value effort matrix.webp'>

Deciding what aspect of a project to tackle first can be overwhelming, that is why we are using an "effort-value chart".  
From this process we identified that creating the NBO model based on the current campaign would be the lowest effort for the highest value return.

#### Data investigation & descriptive analysis

The first step in the analytics process was to perform a data investigation.
Through that the content of the data was identified.
One of the main findings from the initial steps of this process as that the failures are a a lot higher than the successes. This can result to over classification of the final model.
![](graphs\yCount.png)  
This step also included the creation of a decision tree to help identify the most important features. The result of this tree was that the features were ranked in their importance so they can be used more productively in the model creation.
![](graphs\feature_importance.png)

#### Model generation

Due to a time constraint only one model was created, logistic regression.
The features used int he model were the ones identified by the decision tree as the most important. Specifically, `'duration', 'poutcome', 'month', 'pdays', 'age', 'balance', 'housing', 'day', 'contact'`.

#### Results

![](graphs\confusion_Testing.png)
As it can be seen from the confusion matrix the logistic regression model is very good at identifying clients that are not going to buy this product.
The bottom row in the diagram shows the people that actually accepted the campaign split into 2 groups depending on if the model identified them correctly or not.

### Steps forward

1. Model implementation
   - Move model to a production environment
1. Storage of results
   - For use in future iterations
1. Change management organization
   - Use of model in select call centers to verify usefulness
   - Use of model in select call centers to verify usefulness
   - Train specific call center employees to establish usability of results
   - Use the model for other types of campaigning (e-mail, SMS, flyers etc.)
   - Create training material for the whole organization, about what the model is, how it can be used and what the benefits are
1. Monitoring
   - Model
     - To ensure its performance
   - Value
     - To ensure it produces the outcome we are looking for

---

## Next steps

Due to the short timeline of this project a lot of avenues were not able to be explored.
The following have been marked as topics for further investigation:

1. Decision tree library in python  
   1.1. [XGBoost](https://xgboost.readthedocs.io/en/stable/tutorials/model.html#decision-tree-ensembles)
1. Cyclical encoding
1. Parameters investigation for logistic regression
1. Lift chart
1. Classification on imbalanced data
1. [SCQA framework](https://analytic-storytelling.com/12-dos-and-donts-for-your-scqa/)
1. Model competition
