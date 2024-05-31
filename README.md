# Car Sales -Dashboard

### Dashboard Link : https://github.com/itsJeromeJ/PowerBi_car_sales/blob/main/CAR%20SALES%20DASHBOARD.pbix

## Background: 

Our company is a car dealership that sells various car models. To effectively track and analyse our sales performance, we need a comprehensive Car Sales Dashboard in Power BI. 

## Objective:

 The objective of this project is to design and develop a dynamic and interactive Car Sales Dashboard using Power BI. The dashboard will visualize critical KPIs related to our car sales, helping us understand our sales performance over time and make data-driven decisions.


## Problem Statement 1: KPI’s Requirement

The dashboard should provide real-time insights into key performance indicators (KPIs) related to our sales data. This will enable us to make informed decisions, monitor our progress, and identify trends and opportunities for growth.
1.	Sales Overview:
•	Year-to-Date (YTD) Total Sales   
•	Month-to-Date (MTD) Total Sales  
•	Year-over-Year (YOY) Growth in Total Sales  
•	Difference between YTD Sales and Previous Year-to-Date (PTYD) Sales

2.	Average Price Analysis:
•	YTD Average Price  
•	MTD Average Price  
•	YOY Growth in Average Price  
•	Difference between YTD Average Price and PTYD Average Price

3.	Cars Sold Metrics:
•	YTD Cars Sold  
•	MTD Cars Sold  
•	YOY Growth in Cars Sold  
•	Difference between YTD Cars Sold and PTYD Cars Sold  

## Problem Statement 2: Charts Requirement

1.	YTD Sales Weekly Trend: Display a line chart illustrating the weekly trend of YTD sales. The X-axis should represent weeks, and the Y-axis should show the total sales amount.
2.	YTD Total Sales by Body Style: Visualize the distribution of YTD total sales across different car body styles using a Pie chart.
3.	YTD Total Sales by Color: Present the contribution of various car colors to the YTD total sales through a pie chart.
4.	YTD Cars Sold by Dealer Region: Showcase the YTD sales data based on different dealer regions using a map chart to visualize the sales distribution geographically.
5.	Company-Wise Sales Trend in Grid Form: Provide a tabular grid that displays the sales trend for each company. The grid should showcase the company name along with their YTD sales figures.




### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a xlsx file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 :Replace 'double overhead' engine in engine column. creating the calendar table by DAX , because it will have all the dates  of sales and it will give all the ability to perform different date operations.

- Step 5 : Creating the calendar table by DAX , because it will have all the dates  of sales and it will give all the ability to perform different date operations.

- Step 6 :DAX expression for creating calendar table 

         calendar table = CALENDAR(MIN(car_data[Date]),MAX(car_data[Date])).

- Step 7 :then extract year( year = year('calendar table'[Date])), month(month = FORMAT('calendar table'[Date],"mmmm")),week(week = WEEKNUM('calendar table'[Date])) from car data 

- Step 8 :Now connect car data table and calendar table using one-to-many relationship operation.

![Screenshot 2024-05-30 203502](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/8e88ef9b-2200-4305-a28f-df178c212780)

 ## Real-time insights     
- Step 9 : New measure was created To Find Sales Overview Year-to-Date (YTD)  total sales 

Following DAX expression was written for the same,
        
         YTD total sales = TOTALYTD(sum(car_data[Price ($)]),'calendar table'[Date])
        
A card visual was used to represent  Year-to-Date (YTD)  total sales.

![Screenshot 2024-05-30 204211](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/523c3761-fea6-49d1-b217-5ac9b48a29c6)
        
 - Step 10 : New measure was created to find Month-to-Date (MTD) Total Sales
 
 Following DAX expression was written to find Month-to-Date (MTD) Total Sales
 
         MTD Total sales = TOTALMTD(sum(car_data[Price ($)]),'calendar table'[Date])
 
 A card visual was used to represent MTD Total sales.
 
 
 ![Screenshot 2024-05-31 183116](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/db8d84b1-627b-43eb-a475-26ab7907125e)

 
 - Step 11 : New measure was created to calculate Year-over-Year (YOY) Growth in Total Sales.
 
 Following DAX expression was written to find Year-over-Year (YOY) Growth in Total Sales
 
         YoY sales growth = [sales difference]/[PYTD Total sales]
    
 A card visual was used to represent this Year-over-Year (YOY) Growth in Total Sales.
 




 ![Screenshot 2024-05-31 183432](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/b951a6c6-e0f7-45b1-b4d2-84810c9c860f)

 
 - Step 12 : New measure was created to  Difference between YTD Sales and Previous Year-to-Date (PTYD) Sales.
 
Following DAX expression was written to find Difference between YTD Sales and Previous Year-to-Date (PTYD) Sales.


         sales difference = [YTD total sales]-[PYTD Total sales]

 A card visual was used to represent this Year-over-Year (YOY) Growth in Total Sales.
 
 ![Screenshot 2024-05-31 184343](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/23a9338f-1221-41f8-8444-a031fc7d1dee)



 Step 13 : New measure was created to find YTD Average Price

 
Following DAX expression was written to find YTD Average Price



         YTD avg sales = TOTALYTD([AVG price],'calendar table'[Date])

 A card visual was used to represent this YTD Average Price.


 ![Screenshot 2024-05-31 204824](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/be78fb2d-3f9d-4b06-a05b-a1d9ea336f56)



Step 14 : New measure was created to find MTD Average Price

 
Following DAX expression was written to find MTD Average Price



         MTD avg price = TOTALMTD([AVG price],'calendar table'[Date])

 A card visual was used to represent this MTD Average Price


  ![Screenshot 2024-05-31 204204](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/5e739afb-fbdc-4369-8068-3f7f72b9242d)



Step 15 : New measure was created to find YOY Growth in Average Price

 
Following DAX expression was written to find YOY Growth in Average Price



         YoY avg price growth = [avg price diff]/[PYTD avg price]


 A card visual was used to represent this YOY Growth in Average Price


![Screenshot 2024-05-31 185619](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/915b188a-82f0-493e-a2a5-a320ec2ea1bb)



Step 16 : New measure was created to find Difference between YTD Average Price and PTYD Average Price

 
Following DAX expression was written to find Difference between YTD Average Price and PTYD Average Price



         MTD diff avg sales = [YTD total sales]-[PYTD avg price]


 A card visual was used to represent Difference between YTD Average Price and PTYD Average Price


![Screenshot 2024-05-31 185341](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/b916a77a-56b0-47c1-95f2-1b7cef5bf5ae)


Step 17 : New measure was created to findYTD Cars Sold

 
Following DAX expression was written to findYTD Cars Sold



         YTD cars sold = TOTALYTD(COUNT(car_data[Color]),'calendar table'[Date]) 


 A card visual was used to representYTD Cars Sold


![Screen![Screenshot 2024-05-31 205219](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/e052d011-3a9f-450c-813f-edcbc88431a0)


Step 18 : New measure was created to find MTD Cars Sold    

Following DAX expression was written to find MTD Cars Sold



         MTD car sold = TOTALMTD(COUNT(car_data[Car_id]),'calendar table'[Date]) 


 A card visual was used to represent MTD Cars Sold


![Screenshot 2024-05-31 205352](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/1f7354a6-482e-4861-9337-5c0566eccfa3)

Step 19 : New measure was created to find YOY Growth in Cars Sold

Following DAX expression was written to find YOY Growth in Cars Sold



        YoY car sold growth = [cars sold diff]/[YTD cars sold]


 A card visual was used to represent YOY Growth in Cars Sold


![Screenshot 2024-05-31 205602](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/ddb6cee3-b194-4730-8823-1b9b46b28022)

Step 20 : New measure was created to find  Difference between YTD Cars Sold and PTYD Cars Sold


Following DAX expression was written to find  Difference between YTD Cars Sold and PTYD Cars Sold



        cars sold diff = [YTD cars sold]-[PYTD cars sold]


 A card visual was used to represent  Difference between YTD Cars Sold and PTYD Cars Sold


![Screenshot 2024-05-31 205749](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/029d31d8-cd31-41cc-b8be-14fa7ae628d1)


# Problem Statement 2: Charts Requirement

Step 21: YTD Sales Weekly Trend:

 Display a line chart illustrating the weekly trend of YTD sales. 

The X-axis  represent weeks, and the Y-axis  show the total sales amount

A card visual was used to   Display a line chart weekly trend of YTD sales.

![Screenshot 2024-05-31 210144](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/a47fe841-3261-40ea-b161-13bdbc47b004)

Step 22: YTD Total Sales by Body Style: Visualize the distribution of YTD total sales across different car body styles using a Pie chart.

A card visual was used to   Display a Donut chart YTD Total Sales by Body Style.

![Screenshot 2024-05-31 210724](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/baf8d84f-28a1-457d-b4ec-eb4afd514711)

Step 23: YTD Total Sales by Color: Present the contribution of various car colors to the YTD total sales through a pie chart.

A card visual was used to   Display a Donut chart YTD Total Sales by Color.

![Screenshot 2024-05-31 210834](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/bf4e3971-6484-4a2b-9b19-f282966c281e)

Step 24: YTD Cars Sold by Dealer Region:

 Showcase the YTD sales data based on different dealer regions using a map chart to visualize the sales distribution geographically.

A card visual was used to   Display a map chart YTD Cars Sold by Dealer Region.

![Screenshot 2024-05-31 211008](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/44d36782-9751-4e14-bcb5-ffa0d79d405e)

Step 25: Company-Wise Sales Trend in Grid Form:

 Provide a tabular grid that displays the sales trend for each company. The grid should showcase the company name along with their YTD sales figures.

A card visual was used to   Display a tabular grid chart.

![Screenshot 2024-05-31 211235](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/c71cea39-840f-4153-a721-6b95b1adafb6)



# Snapshot of Dashboard-Overview (Power BI Service)

![Screenshot 2024-05-31 212024](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/fcb0a53c-4bc1-4258-9fa3-93cc9450381d)


 
 # Dashboard-Detail Snapshot (Power BI DESKTOP)

 
![Screenshot 2024-05-31 212202](https://github.com/itsJeromeJ/PowerBi_car_sales/assets/146847635/44beb458-37a4-4218-935e-3e68503e66c4)
