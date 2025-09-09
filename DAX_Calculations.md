/*
📊 Power BI DAX Calculations – Sales Analysis Project
Description: This file contains all the key DAX measures used in the Sports-Sales Data Analysis Power BI dashboard.
*/

/* 🏆 1. Total Sales */ Total Sales = SUM(cleaned_sport_sales[Total_Sales])

/* 💰 2. Total Profit */ Total Profit = SUM(cleaned_sport_sales[Operating_Profit])

/* 📈 3. Profit Margin (%) */ Profit Margin = DIVIDE(SUM(cleaned_sport_sales[Operating_Profit]), SUM(cleaned_sport_sales[Total_Sales]), 0) * 100

/* 📊 4. Profit by Sales Method */ Profit by Sales Method = SUM(cleaned_sport_sales[Operating_Profit])

/* 🔥 5. Monthly Sales */ Monthly Sales = CALCULATE( SUM(cleaned_sport_sales[Total_Sales]), ALLEXCEPT(cleaned_sport_sales, cleaned_sport_sales[Invoice_Date]) )

/* 📊 6. Forecasted Sales (Based on Last Month's Sales) */ Forecasted Sales = VAR LastMonthSales = CALCULATE( SUM(cleaned_sport_sales[Total_Sales]), PREVIOUSMONTH(DateTable[Date]) ) VAR GrowthRate = 1.1 -- Adjust based on business trend (e.g., 10% growth) RETURN LastMonthSales * GrowthRate

/* 🌍 12. Profit Margin by Region */ Profit Margin by Region = DIVIDE( SUM(cleaned_sport_sales[Operating_Profit]), SUM(cleaned_sport_sales[Total_Sales]), 0 ) * 100

/* 📊 Profit Margin by Sales Method */ Profit Margin by Sales Method = DIVIDE( SUM(cleaned_sport_sales[Operating_Profit]), SUM(cleaned_sport_sales[Total_Sales]), 0 ) * 100
