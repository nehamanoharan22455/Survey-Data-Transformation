# Survey-Data-Transformation

Survey monkey dataset comes in a wide format (around 100 columns), this has to be transformed into a long format which could be utilised for visualization with tools like Tableau or Power BI.

Snapshot of dataset

![survey](https://user-images.githubusercontent.com/37290809/202184948-41f5d147-9d88-4ab9-896f-43feee50609d.png)


## Main objectives

    1. Unpivot the data into long format
    
    2. Find number of respondents for each question
    
    3. Find number of respondents giving same answer


## Transformations using Excel
The excel dataset of Survey Monkey has 2 sets of headers. Second header contains the sub-questions of the survey.

![header](https://user-images.githubusercontent.com/37290809/202166772-8b3e7dac-e232-4374-8e8c-643854975d9e.png)

### Collapsing sub-questions into question + subquestion format


Steps involved:

    
   1. Copy and Paste (Paste special - Transpose) 
   
    
   2. Combining Questions and Subquestions using if 
   
    
   Sheet name: Question
![combined](https://user-images.githubusercontent.com/37290809/202169645-65405ba8-e35b-459d-842d-71346b6462f7.png)


## Transformations using Pandas


Steps involved:


  1. Importing excel file into pandas dataframe
  
  2. Removing columns which are not relevant for the analysis
  
  3. Unpivoting the dataset using [melt](https://pandas.pydata.org/docs/reference/api/pandas.melt.html?highlight=melt%20function#pandas.melt) function
  
  4. Importing and merging data from Question sheet (excel) with current dataset inorder to include the actual Question

  
     [Merge](https://pandas.pydata.org/docs/reference/api/pandas.merge.html?highlight=merge%20function#pandas.merge) function is used for this purpose, which is really efficient and useful to perform different kinds of joins of datasets.
     
  5. Calculating the number of respondents for each question using groupby method
  
  
     Aggregation of data in a pandas dataframe could be done using [groupby()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.groupby.html?highlight=groupby#pandas.DataFrame.groupby)
     
     
![respond](https://user-images.githubusercontent.com/37290809/202181353-e8759546-14b8-43af-949a-ceb21e5e6bb1.png)

  6. Number of respondents giving same answer is also calculated using groupby()
  
  7. The final dataset is cleaned and converted to excel
  
  ![final1](https://user-images.githubusercontent.com/37290809/202184384-b8e93884-eccb-442f-8f77-bd1c2a3ca4ac.png)



![final2](https://user-images.githubusercontent.com/37290809/202184523-0da20ca8-8d4a-4585-be1f-e1a8ffbc08d4.png)

