# Technical description of capstone  
  
Here I give some of the technical details of my capstone.  
  
## Scraping job ads from Indeed.com  
  
A document that details my process for scraping the data, with links to the code I used, can be found [here](https://github.com/ScottWPiraino/Springboard_Data_Science/blob/master/Capstone/capstone_1_scraping_process.md).  
  
A csv file containing metadata from the jobs I scraped is [here](https://github.com/ScottWPiraino/Springboard_Data_Science/blob/master/Capstone/job_ad_metadata_v2.csv)  
  
A csv file containing the job descriptions of the jobs I scraped is [here](https://github.com/ScottWPiraino/Springboard_Data_Science/blob/master/Capstone/job_ad_descriptions_v2.csv)
  
## Text processing  
  
I built a single text processing pipeline that I applied both to job titles and job descriptions. I used a Gensim phrase model long with a the LancasterStemmer from the nltk package to process the text initially. Using the tokens identified in this way, I then transform the text into a count matrix using scikit-learn. I also extract that state in which the job was listed using string operations.  
  
## Modeling job location  
  
As the target variable for the job location, I use the state in which the job occured. For states with few jobs, I group them all into one "Other" category. To perform the supervised learning task, I use a logistic regression model with default parameters. To handle the multi-class nature of the problem, I use a one-vs-rest approach, fitting one logistic model for each class where the target is the binary variable equal to 1 when the overall target equals that class, and zero otherwise.  
  
## Model evaluation  
  
I evaluate the model in terms of accuracy score (i.e. proportion of predicts for which the predicted class equals the true class). I evaluate the model using five-fold stratified cross validation, and additionally test the informativeness of the classifier by permuting the labels (i.e. job locations) to generate a null distribution of the accuracy score.
