# banking-Dataset-Analysis  Using AI

### Dashboard Link : https://app.powerbi.com/groups/71393302-65aa-4d18-ac8f-2469e041847d/reports/451b38c8-0f37-4b8a-9c0f-ad7d520dcb3b/391a4a804cc32ad3053f?experience=power-bi

### Steps We have follow:

#### after creating database & tables 

#### inserting 10000 rows into the transactions table 

#### fix Date column in all tables 

#### combining data from three tables using SQL 

#### loading data into powerBI desktop  from SQL 

#### KPI Charts & DAX recommendation using ChatGPT :

### DAX:
    1 - Account Count by Type = COUNT(CombinedBankingDataset[Account_AccountID])
    2 - Count Of Transaction = COUNT(CombinedBankingDataset[TransactionID])
    3 - Customer Count by Gender = DISTINCTCOUNT(CombinedBankingDataset[CustomerID])
    4 - Inactive Accounts = CALCULATE(DISTINCTCOUNT(CombinedBankingDataset[Account_AccountID]), FILTER(VALUES(CombinedBankingDataset[Account_AccountID]), CALCULATE(MAX(CombinedBankingDataset[TransactionDate])) < TODAY()-90))
    5 - Monthly Transaction Amount = CALCULATE(SUM(CombinedBankingDataset[Amount]), ALLEXCEPT(CombinedBankingDataset, CombinedBankingDataset[TransactionDate].[Month]))
    6 - Monthly Transaction Balance = CALCULATE(SUM(CombinedBankingDataset[Balance]), ALLEXCEPT(CombinedBankingDataset, CombinedBankingDataset[TransactionDate].[Month]))
    7 - Total Balance = SUM(CombinedBankingDataset[Balance])
    8 - Customer Age = DATEDIFF(CombinedBankingDataset[DateOfBirth], TODAY(), YEAR)
    9 - Customer Age Group = SWITCH(TRUE(), [Customer Age]<=25, "â‰¤25", [Customer Age]<=35, "26-35", [Customer Age]<=50,"36-50","51+")
