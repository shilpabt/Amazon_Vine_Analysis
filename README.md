# Amazon_Vine_Analysis
Big Data analysis with Google Colab, Pyspark, Postgres/pgAdmin, AWS RDS, Pandas and SQL

Data : https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Office_Products_v1_00.tsv.gz


# Overview

Purpose of this project was to determine if there is any bias toward favorable reviews from Vine members in our dataset. 
Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies like SellBy pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

For this project, I have collected amazon_reviews_us_Office_Products dataset and used PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Then used PySpark to determine if there is any bias toward favorable reviews from Vine members in our dataset. 

# Results

### Performed ETL on Amazon Product Reviews
 In the cloud ETL process,
 - Created an AWS RDS database with tables in pgAdmin, picked a US office product dataset from the set of Amazon Review datasets Links to an external site.,
 - Extracted the dataset into a DataFrame. 
 - Then transformed the DataFrame into four separate DataFrames that match the table schema in pgAdmin.
 - Then, uploaded the transformed data into the appropriate tables and ran queries in pgAdmin to confirm that the data has been uploaded.

 Us office products dataset is extracted into a dataframe is as below,
*office_products_df*

 !["office_products_df"](Resources/office_products_df.png?raw=true)

 All 4 dataframes and the data from the tables are as below,

Customer_df                          |  Customer_table
:-------------------------------------:|:-------------------------:
![](Resources/customer_df.png?raw=true)|  ![](Resources/customers_table.png?raw=true )



product_df                            |  products_table
:-------------------------------------:|:-------------------------:
![](Resources/product_df.png?raw=true)|  ![](Resources/products_table.png?raw=true)


reviews_id_df                            |  review_id_table
:-------------------------------------:|:-------------------------:
![](Resources/reviews_id_df.png?raw=true)|  ![](Resources/review_id_table.png?raw=true )

vine_df                               |  vine_table
:-------------------------------------:|:-------------------------:
![](Resources/vine_df.png?raw=true)|  ![](Resources/vine_table.png?raw=true)


Using the above dataframe, we can address the following questions,

* ### How many Vine reviews and non-Vine reviews were there? 

There are 43745 unpaid reviews and 969 paid reviews.

!["Reviews count" ](Resources/paid_unpaid_review_count.png?raw=true "Reviews count")



* ### How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?

430 of the Vine reviews were 5 star.  
19233 of the non-Vine reviews were 5 star.

!["5-star reviews count" ](Resources/unpaid_paid_5star_reviews_count.png?raw=true "5-star reviews count")



* ### What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?

44.37% of the 5 star reviews were Vine.  
43.96%(almost 44%) of the 5 star reviews were non-Vine.

!["percentage of 5-star reviews" ](Resources/percentage%20_of_5star_reviews.png?raw=true "percentage of 5-star reviews")



# Summary

44.37% of the reviews in the Vine program were 5 stars reviews whereas the percentage in the non-Vine reviews is only 43.97%. As per the percentage calculated, we can conclude that there is *no positive bias* for reviews of US Office Products in the Vine program.

One additional analysis that could do with the given dataset is *statistical analysis* which includes mean, meadian and mode of the star ratings reviews. 




