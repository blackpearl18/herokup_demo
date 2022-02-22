# Stock Price Prediction using Logistic Regression
The aim of this project is to predict whether the stock is in profit or loss by using today's Closing Price and Yesterday's Closing Price.

## Authors

- Mujeeb Ur Rehman
- Asswin CR
- M Priyanka
- Purva Chouhan
- Shivam Himanshu

## Content

1. Project Methodology
2. Exploratory Data Analysis
3. Logistic Regression 
4. Model Performance
5. Conclusion


## Data Collection
As per the project requirements, five Years of Data was collected from 14th Nov 2016 to 12th Nov 2021

#### Link to Raw Data
 - [Stock Price Data](https://drive.google.com/drive/folders/1iDffZ_dpV-8QZLCJJHMPo5kMM7n45jQ4?usp=sharing)

The Data was downloaded from [Yahoo Finance](https://finance.yahoo.com/)

Data include following columns

- Date
- Close
- Volume
- Open
- High
- Low


![Image](https://github.com/Mujeeb-Khalil/Deep-Reinforcement-Learning-in-Algorithmic-Trading/blob/main/Pictures/Data.png)

## Data Preprocessing

### Adding New Close Price Column
```
df["Date"] = pd.to_datetime(df["Date"])
df.sort_values(by = "Date",ignore_index= True,inplace= True)
df["Close/Last"] = df["Close/Last"].str.replace("$","").astype(float)close_list = list(df["Close/Last"])
new_close_list = []
for i in range(len(close_list)):
  if i ==0:
    new_close_list.append(0)
  else:
    new_close_list.append(close_list[i]-close_list[i-1])
df["New Closing Price"] = new_close_list
df.head()
```

### Data Distribution

![Image](https://github.com/Mujeeb-Khalil/Deep-Reinforcement-Learning-in-Algorithmic-Trading/blob/main/Pictures/Data_Distribution.png)

### Open Price 
![Image](https://github.com/Mujeeb-Khalil/Deep-Reinforcement-Learning-in-Algorithmic-Trading/blob/main/Pictures/Open_Price.png)

### Data Normalization
![Image](https://github.com/Mujeeb-Khalil/Deep-Reinforcement-Learning-in-Algorithmic-Trading/blob/main/Pictures/Data_Normalization.png)

### Adding Target Variable
![Image](https://github.com/Mujeeb-Khalil/Deep-Reinforcement-Learning-in-Algorithmic-Trading/blob/main/Pictures/Target_Variable.png)

## Logistic Regression
Logistic Regression Model was trained and it got the accuracy of 98%
### Classification Report
![Image](https://github.com/Mujeeb-Khalil/Deep-Reinforcement-Learning-in-Algorithmic-Trading/blob/main/Pictures/Classification_report_lr.png)

### Hyperparameter tuning
After Hyperparameter tuning model got the accuracy of 100%

### Classification Report after hyperparameter tuning
![Image](https://github.com/Mujeeb-Khalil/Deep-Reinforcement-Learning-in-Algorithmic-Trading/blob/main/Pictures/Classification_report_hp.png)

### Comparison before and after Hyperparamter tuning
#### Before Hpyarameter tuning
![Image](https://github.com/Mujeeb-Khalil/Deep-Reinforcement-Learning-in-Algorithmic-Trading/blob/main/Pictures/hm_before_hp.png)
#### After Hpyarameter tuning
![Image](https://github.com/Mujeeb-Khalil/Deep-Reinforcement-Learning-in-Algorithmic-Trading/blob/main/Pictures/hm_after_hp.png)

## Model Deployment 
Flask and Heroku are used to deploy the model.

[Stock Price Data Model](https://stock-price-prediction-07.herokuapp.com/)

![Image](https://github.com/Mujeeb-Khalil/Deep-Reinforcement-Learning-in-Algorithmic-Trading/blob/main/Pictures/Deploy.png)

![Image](https://github.com/Mujeeb-Khalil/Deep-Reinforcement-Learning-in-Algorithmic-Trading/blob/main/Pictures/Deploy_profit.png)

## Conclusion
- Conditions were the H value is higher than open value will lead to profit most of the times

- For further research and development work we must explore tools to incorporate rising and falling trends in legacy data and history of a particular stock's price.

- Logistic Regressor may have limited applicability in a real world scenario.

- Possibility of including other sources of information like News Articles, Forum comments, Feredal Rates, Gold Price etc may also be used to make predictions.




