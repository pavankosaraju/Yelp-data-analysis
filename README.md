# PGN-YELP -- Data Analysis and Usefulness prediction of YELP Reviews

## Technologies Used: 

[Python, Spark]( https://spark.apache.org/docs/latest/api/python/index.html) - ETL and Data Analysis

[Spark MLlib](http://spark.apache.org/docs/2.0.0/api/python/pyspark.mllib.html) - Machine Learning
 
[NLP](https://spark.apache.org/docs/2.1.0/ml-features.html) - for text processing

[Tableau](https://www.tableau.com/) - Visualization


## Running the files
Data provided by YELP is stored in /user/rsooram/YELP folder

#### 1. Data Processing

json_to_parquet.py converts json files to parquet files. These processed data is located in /user/rsooram/YELP_PAR HDFS folder.

spark-submit json_to_parquet.py YELP/yelp_academic_dataset_business.json YELP_PAR
spark-submit json_to_parquet.py YELP/yelp_academic_dataset_user.json YELP_PAR
spark-submit json_to_parquet.py YELP/yelp_academic_dataset_reiew.json YELP_PAR

#### 2. Data Analysis

top10_categories.ipynb - generates top 10 categories by count

spark-submit top_users_top_business_review.py YELP_PAR topusers_category10 - generates top 10 users for each category

spark-submit toptenreview_businesses.py YELP_PAR TopReviewedBusinesses - generates top 10 businesses by review count

spark-submit top_users_top_business_review.py YELP_PAR topusers_review10 - generates top 10 users for each business

spark-submit user_location.py YELP_PAR UserState - generates user demographics by state in USA

spark-submit top_business_trends.py YELP_PAR business_trends - generates average rating by month for businesses

spark-submit word_clouds.py [Business name] [all/postal code] - generates unigram and bigram word count for a particular business
Ex:spark-submit word_clouds.py Starbucks all

Files are saved as [TopReviewedBusinesses/UserState/....].csv and present in CSV files folder

#### 3. Predicting Usefulness of reviews

Data processing -

spark-submit generate_ml_data.py YELP_PAR - Process data for Multiclass Classification
spark-submit ml_data_binaryclass.py YELP_PAR - Process data for Binary Classification

Class balancing, Model Building, Classification, and Evaluation are done in the below files

ML-Useful.ipynb - Predictions using Multiclass targets
ML-Useful-Binary.ipynb - Predictions using Binary targets

Models are saved in BestModelUseful(Multiclass), Model_Useful_Binary(Binary) folders

#### 4. Visualization

Demo story can be visualized using project.twb file present in Tableau folder


## Authors

* *Rohith Sooram*
* *Pavan Kosaraju*
