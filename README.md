# Flight Arrival Delay Prediction Using Machine Learning (Project 4)

## Project Objective
To develop a model to predict flight arrival delays for flights departing from Arizona airports using 3 years of flight data. 

## Team Members (Team 9)
- Angelina Wright
- Eylem Yildirim
- Pushpa Chhetri

## Deliverable(s)
[Data Cleaning and Analysis](https://github.com/wrighang/predicting_flight_arrival_delay_ml/blob/main/Flight_Delays.ipynb)
[Presentation Slide Deck](https://github.com/wrighang/predicting_flight_arrival_delay_ml/blob/main/Flight%20Delays.pdf)

## Tools/Technologies
- Python, Tableau
- Pandas, Matplotlib, Tableau, Seaborn, Tensorflow, sci-kit learn

## Data Visualizations
Tableau visuals helped to understand dataset more from trends perspective.
- Operational Carrier Frequency:
                   
     Displays the number of flights operated by each airline (Op Unique Carrier vs. Count of Op Carrier Fl Num).

- Causes for arrival Delays
    Compares delay causes (impacts of Weather, Security, Carrier, NAS, Late Aircraft delay) by count of flights.

- Departure Delays by Origin City:

    Examines how departure delays vary among Arizona cities (Avg Dep Delay vs. Origin City).

- Arrival Delays by Day of the Week:

    Identifies which days experience the most delays (Avg Arr Delay vs. Day of the Week).
- Arrival Delays Throughout the Day:

    Analyzes how delays change in a 24-hour window (Avg Arr Delay vs. Time of Day).

## Preprocessing Data
**DATA INTEGRATION**
- Merged Monthly Files: Combined monthly csv files into a single dataset.
- Filtered for Arizona Departures: Retained columns where ORIGIN_STATE_ABR = "AZ". <br>
**FEATURE ENGINEERING ENHANCEMENTS:**
- Introduced new columns to enhance analysis: 
 - ARR_DELAY: 0 = on-time, 1 = delayed
 - DAY_PART: Departure Time to “Early Morning”, “Morning”, “Midday”, “Afternoon”, “Evening”, “Night”, “Late Night”
 - FLIGHT_TRAFFIC: Count of flights every hour leaving the origin airport
 - SEASON: Based on month - Fall, Winter, Spring, Summer
 - SC_DEP_TIME: Scheduled departure time
 - SC_HOUR: Scheduled hour flight departing <br>
**DATA CLEANING & ENCODING:**
- DEPT_TIME - date time format & removed missing values.
- Mapped Carrier Codes: Added airline names for improved readability.
- Encoding Data: Applied label encoding to categorical variables.


## Target and Features for Our Model
**Target:** ARR_DELAY: 0 = on-time, 1 = delayed <br>
**Features:** <br>
1. YEAR
2. MONTH
3. DAY_OF_MONTH
4. DAY_OF_WEEK
5. AIR_TIME: Flight time (minutes)
6. DEP_DELAY_NEW: Delay time (minutes)
7. DEST: Destination airport, city name
8. DEST_STATE_ABR: Destination state 
9. DISTANCE: Distance between airports (miles)
10. OP_CARRIER_FL_NUM: Flight number
11. ORIGIN: Origin Airport
12. TAXI_OUT: Taxi out time (minutes)
13. WHEELS_OFF: Time aircraft took off <br>
**NEW COLUMNS ADDED FOR INCREASED GRANULARITY:** 
15. DAY_PART: Departure Time to “Early Morning”, “Morning”, “Midday”, “Afternoon”, “Evening”, “Night”, “Late Night”
16. FLIGHT TRAFFIC: Count of flights every hour leaving the origin airport
17. OP_UNIQUE CARRIER: Carrier mapped from carrier code to carrier name
18. SC_HOUR: Scheduled hour flight departing
19. SEASON: Based on month - Fall, Winter, Spring, Summer

## Machine Learning Models Applied:
1. Random Forest Model
2. Gradient Boosting Model
3. Decision-Tree Model
4. K-Neighbors Model
5. Logistic Regression
6. Neural Network Model

 On our initial test, Random Forest model achieved the best and consistent performance. We looked at a few different scores:
 - Accuracy score
 - Out-Of-Bag Score (for Random Forest)
 - Precision and Recall Scores

   
### Random Forest Model Optimization
We applied variety of optimization techniques:
1. Hyperparameter Tuning
2. Feature Selection:
    - Feature Importance
    - Spearman Correlation
4. SMOTE to handle class imbalance

Comparison of successful results:
![image](https://github.com/wrighang/predicting_flight_arrival_delay_ml/blob/main/Resources/rf_results.png)

### Best Model
Best Model is the Random Forest Model after using SMOTE to balance the data. It aligned better with our objective which was to correctly identify delayed flights.

**Overall Accuracy:** Model accurately classifies 89% of flights. <br>
**OOB Score:** A high 91% suggests strong performance on unseen data. Model generalizes well.

**Precision:** When predicting flight status:
- On-time flights: Correct 89% of the time
- Delayed flights: Correct 87% of the time

**Recall:** The model successfully identifies:
- 93% of actual on-time flights
- 81% of actual delayed flights



## Resources
Dataset: [Bureau of Transportation Statistics: On-Time : Reporting Carrier On-Time Performance](https://www.transtats.bts.gov/DL_SelectFields.aspx?gnoyr_VQ=FGJ&QO_fu146_anzr=b0-gvzr)
