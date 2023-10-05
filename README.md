# I-phone-sales-analysis
i phone sales data cleaning, framing and analysis 
### import pandas as pd 
import numpy as np 
import plotly.express as px
import plotly.graph_objects as go 

raw_data = pd.read_csv("D:/python/archive/apple_products.csv")
raw_data

# Identification of Null or Missing values 

print(raw_data.isnull().sum())

raw_data = pd.read_csv("apple_products.csv")
print(raw_data.describe())

# Top 10 Apple iphone sold in India

Highest_rated = raw_data.sort_values(by = ["Star Rating"], ascending = False)
Highest_rated = Highest_rated.head(10)
print(Highest_rated["Product Name"])

# lets have number of ratings of heighest rated products in flipkart 

iphones = Highest_rated ['Product Name'].value_counts()
labels = iphones.index
counts= Highest_rated["Number Of Ratings"]
figure = px.bar(Highest_rated, x= labels, y= counts, 
                title= "Top 10 products")
figure.show()            

# Relationship between sales price and number of ratings 

figure = px.scatter(data_frame= raw_data,x="Number Of Ratings", y ="Sale Price", size = "Discount Percentage", trendline = 'ols', 
                title= "Relationship between Sales Price and Number of ratings")

figure.show()   


# Relationship between Number of rating and discount 


figure = px.scatter(data_frame= raw_data,x="Discount Percentage", y ="Number Of Reviews", size = "Mrp", trendline = 'ols', 
                title= "Relationship between Sales Price and Number of ratings")

figure.show()  

