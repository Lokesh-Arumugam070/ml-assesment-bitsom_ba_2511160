Problem Formulation:
1)  Here the key area of focus is items sold and it is influenced by parameters like month,year,season,festival etc. It is regeression problem as output is continuous numerical variable.
2)  Revenue parameter here is influenced or affected by discount, pricing across stores in different areas and product sold. However, item sold is directly related to profit and cudtomer satisficstion which helps company to improve better in future
3) Other approcahes include cluster based(group store as per location) and hierarchial model. Benefits include:
•	Reagional wise behaviour differnce
•	Learing across states that allows customisation
  
 
Data and EDA Strategy:
1)  Join tables using common keys:
o	transactions and store_attributes 
o	using store_id,promotion_details using promotion_id / promotion_type
o	calendar using transaction_date

Grain of Final Dataset:
    The grain of a dataset refers to the lowest level of detail or the exact definition of what a single record (row) in a table represents
Aggregations:
From transaction-level (monthly store-level):
I.	items_sold =sum
II.	revenue =sum
III.	footfall=sum / avg
	promotion_type=most frequent / assigned campaign
	is_weekend, is_festival=aggregated counts or flags
	competition_density, store_size=static (no aggregation)




2) Sales by Promotion Type:
Influence:
o	Feature importance
o	Interaction features
Sales vs Location Type:
Influence:
o	Need for segmentation or clustering
Time Series Plot: 
Influence:
o	Add time-based features (month, seasonality)
Correlation:
Influence:
o	Feature selection
o	Remove redundant features
  
3) Problems faced is bias towards no promotion and can't learn promtion imapcat
Steps to overcome imbalance:
o	Resampling
o	Feature Engineering
o	Modelling

Model Evaluation and Deployment:

1)  Train-Test Split:-time-based split
•	Train: First ~2–2.5 years
•	Test: Last ~6–12 months

     Random Split disadvantage:
•	Data Lekage
•	Future data may influence past predictions
•	Ignores seasonality and trends

Evaluation Metrics:   
MAE (Mean Absolute Error):
•	Avg absolute difference between predicted and actual sales
•	Easy to interpret 

RMSE (Root Mean Squared Error):
•	Penalizes large errors more
•	Useful when big mistakes are costly

MAPE (Mean Absolute Percentage Error):
•	Percentage error relative to actual sales
•	Helps compare across stores



2) Different Promotions for Same Store:
Model considered include:
	Season
	Festival periods
	Customer behavior changes
	Past performance of promotions

Using Feature Importance:
1.	Check global feature importance
   	 Identify key drivers (month, promotion type, location)
2.	 Use local explanations 
    For January:
       Festival season -Loyalty Points works better
    For June:
    Lower demand - Flat Discount drives sales



3) First save the odel and serialize using:
I.	Job library or pickle
    Store with:
A.	Model version
B.	Feature pipeline
Prepare new monthly data which include the following:
	Store data
	Promotion options
	Calendar features



