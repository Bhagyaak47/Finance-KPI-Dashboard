# Finance-KPI-Dashboard
Finance Performance Dashboard covers 14 months of  Actual &amp; Target sales analysis.i.e,Jan-23 to Feb-24 .  KPI's, Team and Sales Performance showcased dynamically.

# Problem Statement :
In this Project,I have created a dashboard in Power Bi that reflects all relevant Key Performance Indicators(KPI's) and matrics in the dataset.

# Possible KPI's & their DAX formulas :
- Total Sales Actual = SUM(Actual[Sales])
- Total Sales Target = SUM(Targets[Sales])
- Variance = [Total Sales Actual]- [Total Sales Target]
- Variance % = DIVIDE([Variance],[Total Sales Target])
- YTD Sales Actual = CALCULATE([Total Sales Actual],DATESYTD('Calendar'[Date]))
- YTD Sales Target = CALCULATE([Total Sales Target],DATESYTD('Calendar'[Date]))
- YTD Variance = CALCULATE([Variance],DATESYTD('Calendar'[Date]))
- YTD Variance % = CALCULATE([Variance %],DATESYTD('Calendar'[Date]))
- Target Status = IF([Variance]>0,1,-1)
- Months Target Reached = 
    var months_with_target_reached = filter(ALL('Calendar'),[Variance]>0)
RETURN
    COUNTROWS(months_with_target_reached)
- Variance Pct Label = 
    var up = "🟢"
    var down = "🔴"
    var formatted_var_pct = FORMAT(ABS([Variance %]),"0.0%")
return 
    formatted_var_pct & " " & IF([Variance %]>0,up,down)
- Trend Chart Title = 
    var month_count = COUNTROWS('Calendar')
RETURN
    "We Met Targets For " & [Months Target Reached] & " Out Of " & month_count.

# Data Preparation:
There are 4 Tables in Excel file which we connect through Data modeling Date & month wise neatly.14 months of  Actual & Target sales analysis.i.e,Jan-23 to Feb-24 

- Actual Tables : How Each sales person performed in each month.
- Target Table : What is the target each sales person suppose to meet in a month.
- Dates : For each month i did analysis.
- Dimpeople : Little bit more about the team i.e, name of the sales person,Team which they belongs to,their image.

# Data Cleaning:
- Use 1st row as header.
- select 1st column and unpivot other columns.
- Change column name and data types.
- in calender table only dates were mentioned so i added Year,Month,Month name column for better granularity.

# Questions to be Answered :
  Find how many months we have achieved the target ?

![Finance performance_001](https://github.com/Bhagyaak47/Finance-KPI-Dashboard/assets/152842490/0c8c832d-c3e1-499b-b722-8c88ef601186)

# Insights :
- Overall we met targets 2 months out 14 months.
- 11 Sales person out of 25 sales person succeded in achieving their target.
- "Kaine Padly" acheived the highest target by 9.0%.
- "Marney O'Breen"  acheived the least no. of target & variance % is -11.6%.
- From Team Yummies 4 sales person achieved the target.
- From Team Delish & Jucies 3 sales person achieved the target respectively.
- From Team Tempo 1 sales person achieved the target.




