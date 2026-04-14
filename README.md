# banking-Dataset-Analysis  Using AI

### Dashboard Link :https://app.powerbi.com/groups/71393302-65aa-4d18-ac8f-2469e041847d/reports/bbeb4d9b-de89-48c4-b0e5-0d090bd2cb87/391a4a804cc32ad3053f?experience=power-bi

### Steps We have follow:

#### - After creating database & tables 
        
#### - inserting 10000 rows into the transactions table 
        
#### - fix Date column in all tables 
        
#### - combining data from three tables using SQL 
        
#### - loading data into powerBI desktop  from SQL 
        
#### - KPI Charts & DAX recommendation using ChatGPT :
        
### DAX:
            1 - Account Count by Type = COUNT(CombinedBankingDataset[Account_AccountID])
            2 - Count Of Transaction = COUNT(CombinedBankingDataset[TransactionID])
            3 - Customer Count by Gender = DISTINCTCOUNT(CombinedBankingDataset[CustomerID])
            4 - Inactive Accounts = CALCULATE(DISTINCTCOUNT(CombinedBankingDataset[Account_AccountID]), FILTER(VALUES(CombinedBankingDataset[Account_AccountID]),                 CALCULATE(MAX(CombinedBankingDataset[TransactionDate])) < TODAY()-90))
            5 - Monthly Transaction Amount = CALCULATE(SUM(CombinedBankingDataset[Amount]), ALLEXCEPT(CombinedBankingDataset,                                                     CombinedBankingDataset[TransactionDate].[Month]))
            6 - Monthly Transaction Balance = CALCULATE(SUM(CombinedBankingDataset[Balance]), ALLEXCEPT(CombinedBankingDataset,                                                   CombinedBankingDataset[TransactionDate].[Month]))
            7 - Total Balance = SUM(CombinedBankingDataset[Balance])
            8 - Customer Age = DATEDIFF(CombinedBankingDataset[DateOfBirth], TODAY(), YEAR)
            9 - Customer Age Group = SWITCH(TRUE(), [Customer Age]<=25, "â‰¤25", [Customer Age]<=35, "26-35", [Customer Age]<=50,"36-50","51+")

#### -- Data Cleaning  - 
                - For description Column : 
            Replace values from (null to unKnown)
            - For currency column : 
            replace value with uppercase 
            - For accountID Column : 
            Keep as Same 
            - For Account type : 
            replace values with Capitalize 
            - Changing data type of some columns :
            - TransactionDate

#### -- Cleaning Other Date Column  - 
        change datatype Phone =  to (Whole number)
        Change datatype DOB = rightclick on that column (change using Local) change to Date (eng us)
        Change datatype Opendate = rightclick on that column (change using Local) change to Date (eng us)


#### -- Number of transaction by Type  - 
         Count Of Transaction = COUNT(CombinedBankingDataset[TransactionID])

#### -- Transaction by month  - 
        Monthly Transaction Amount = CALCULATE(SUM(CombinedBankingDataset[Amount]), ALLEXCEPT(CombinedBankingDataset, CombinedBankingDataset[TransactionDate].              [Month]))

#### -- Top 2 transaction by Name  - 
        used (amount , name column) for Column Chart with filter for TOP 2 transaction by Name

#### -- Total balance by Account Type  - 
        Total Balance = SUM(CombinedBankingDataset[Balance])

#### -- inactive Accounts by year & month  - 
        Inactive Accounts = CALCULATE(DISTINCTCOUNT(CombinedBankingDataset[Account_AccountID]), FILTER(VALUES(CombinedBankingDataset[Account_AccountID]),                   CALCULATE(MAX(CombinedBankingDataset[TransactionDate])) < TODAY()-90))

#### -- Customer Count By gender  - 
         Customer Count by Gender = DISTINCTCOUNT(CombinedBankingDataset[CustomerID])

#### -- Number of customer by Age Group  - 
        DAX : 
        Customer Age = DATEDIFF(CombinedBankingDataset[DateOfBirth], TODAY(), YEAR)
        Customer Age Group = SWITCH(TRUE(), [Customer Age]<=25, "â‰¤25", [Customer Age]<=35, "26-35", [Customer Age]<=50,"36-50","51+")


#### -- Creating & Formating the Tree Map - 
        DAX Measures : 
        Account Count by Type = COUNT(CombinedBankingDataset[Account_AccountID])


#### -- Adding Remaining Charts  - 
         Created  Stacked Bar charts (Name , Balance )

        Used DAX : 
        Monthly Transaction Balance = CALCULATE(SUM(CombinedBankingDataset[Balance]), ALLEXCEPT(CombinedBankingDataset, CombinedBankingDataset[TransactionDate].[Month]))

#### -- Publish the Report     

