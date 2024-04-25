## This project demonstrates the creation of a comprehensive credit card dashboard using Power BI. It covers data extraction from a SQL database, data processing and DAX queries, dashboard design, and sharing insights. The project aims to provide real-time insights into credit card operations, enabling stakeholders to monitor and analyze performance efficiently.  


- Devlope Comprehensive credit card weekly dashborad provides real time weekly insight  insights 
- insight into key performance matrix and trend 
- Enable to stasck honder to moniter and analyze credit card operation effectively  


## 1. Project objective
## 2. Data from SQL
## 3. Data processing & DAX
## 4. Dashboard & insights
## 5. Export & share project

### Project Objective

- To develop a comprehensive credit card weekly dashboard that
provides real-time insights into key
performance metrics and trends,
enabling stakeholders to monitor
and analyze credit card operations
effectively.

### step. 1 import dta from sql   

### step.2 load data tables from sql 

### step. 3 Data processing and DAX queries   
- age_group wrt to their age categories to see the data interm of group 
- IncomeGroup --//-- 
- 

- public_CC_table 
    - revenue :- Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned] 



#### we ake these dashbord wrt week and week 
- to calculate revenue week on week 

Dax_Query :- 

- IncomeGroup = SWITCH(
    TRUE() , 
    'public cust_detail'[income] < 35000 , "LOW" ,
    'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] < 70000 , "MED" ,
    'public cust_detail'[income] >= 70000 , "HIGH" , 
    "unknow"
)

- Age group = SWITCH(
     TRUE() ,
     'public cust_detail'[customer_age] < 30 ,"20-30"  ,  
     'public cust_detail'[customer_age] >=30 && 'public cust_detail'[customer_age]< 40 , "30-40" ,    
     'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] <50 ,"40-50" , 
     'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] <60 ,"50-60" , 
     'public cust_detail'[customer_age] >= 60 , "60+" , 
     "unknow" 
        )
- Current_week_Revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[Week_num2] = MAX('public cc_detail'[Week_num2])
    )
)

- Previous_week_Revenue = CALCULATE(
    SUM('public cc_detail'[Revenue]),
    FILTER(
        ALL('public cc_detail'),
        'public cc_detail'[Week_num2] = MAX('public cc_detail'[Week_num2])-1
    )
)

- Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned] 

- Week_num2 = WEEKNUM('public cc_detail'[week_start_date])

- wow_revenue = DIVIDE(([Current_week_Revenue] - [Previous_week_Revenue]) , [Previous_week_Revenue])




Project Insights- Week 53 (31st Dec)
WoW change:
- • Revenue increased by 28.8%,
- • Total Transaction Amt & Count increased by xx% & xx%
- • Customer count increased by xx%
- Overview YTD:
- • Overall revenue is 57M
- • Total interest is 8M
- • Total transaction amount is 46M
- • Male customers are contributing more in revenue 31M, female 26M
- • Blue & Silver credit card are contributing to 93% of overall transactions
- • TX, NY & CA is contributing to 68%
- • Overall Activation rate is 57.5%
- • Overall Delinquent rate is 6.06% 

 



