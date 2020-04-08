# ETL-
The first task we will need to complete is sourcing the data and looking to see if we can pull sufficient data to answer our questions, and refine to fit the questions we are asking.  We will also need totake steps to clean and scrub specific data. We will then analyze our findings and summarize and conclude our findings using statistical analysis and communicate our findings to be clearly understood by our colleagues.

Proposal:
Show a correlation/link between daily confirmed cases of COVID-19 to stock prices of Major international  hotels and Airlines. 

Extract Process: 
Original data sources were retrieved from direct websites listed below where we were able to download direct CSV files.
Sources:
COVID-19 Confirmed Cases: 
https://github.com/CSSEGISandData/COVID-19 ; https://docs.google.com/spreadsheets/d/1yZv9w9zRKwrGTaR-YzmAqMefw4wMlaXocejdxZaTs6w/htmlview?usp=sharing&sle=true
Hotels: 
HLT Hilton Worldwide Holdings Inc. Common Stock
https://finance.yahoo.com/quote/HLT/history?p=HLT
VAC Marriott Vacations Worldwide Corporation Common Stock
https://finance.yahoo.com/quote/VAC/history?p=VAC
Airlines: 
DAL , Delta Air Lines, Inc. Common Stock
https://finance.yahoo.com/quote/DAL/history?p=DAL
SINGF, Singapore Airlines Ltd
https://finance.yahoo.com/quote/SINGY/history?p=SINGY


Transform (Clean Up) Process: 

Download the stock prices to a csv file. 
Clean data to keep only the latest 30days
Pulled in each stock ticker into its’ own dataframe
Had to reformat date and bring in ticker symbol
Merged all data frames together
Created a new dataframe from the large merged to only bring in: adjusted closing value, ticker symbol, and date
Moved Pandas over to Mongo
Stock prices not available for Saturday/Sunday 
Clean up of 30 days COVID-19 data. 
Convert each csv file to a data frame
Loaded all 30 files as data frames then concactonated them to one dataframe 
Slice the column “last column” by removing the timestamp
Dropped unnecessary columns to keep only “confirmed”, “death”, “last updated”, and “recovered”
Rearranged and renamed the columns
We then grouped by and summed by the date column
Dropped all rows before the date “2/6”
Load Process: 
Had 2 dataframes, 1 for covid virus counts by date and the other stock adjusted closing price for hotels and airlines
We created a Covid database in Mongo DB and two collections; one for the stocks data frame and the other for the covid cases
To load the data we had to convert the individual data frames into dictionaries
Had to read each row from the dictionary and inserting into Mongo DB
Lastly, had to convert the date to string

