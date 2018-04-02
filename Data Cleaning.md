It is common that the data we are going to analyze are not complete, here we will study how to clean data.    
### Handling Missing Values  

1.check some data . 
    sf_permits = pd.read_csv("../input/building-permit-applications-data/Building_Permits.csv")
    sf_data.samples(5)  
![Data Samples](https://i.imgur.com/Y9dRpwo.png) 

2.have a general idea about the missing data we have 

    #get the number of missing data points per column
    missing_values_count = sf_permits.isnull().sum()

    #look at the # of missing points in the first ten columns
    missing_values_count[0:10] 
    #how many total missing values do we have?
    total_cells = np.product(sf_permits.shape)
    total_missing = missing_values_count.sum()

    #percent of data that is missing
    (total_missing/total_cells) * 100  
 26.26002315058403 
 
3.figure out why the data is missing  
**Is this value missing becuase it wasn't recorded or becuase it dosen't exist?**   
If not recorded, then let's try to guess what it might have been based on the other values   
in that column and row.  

4.drop missing values  

    #remove all the rows that contain a missing value
    nfl_data.dropna() 
    
 But the result could be empty since there could be empty values in each row. Maybe better just  
 remove all the columns that have at least one missing value instead.  
    #remove all columns with at least one missing value
    columns_with_na_dropped = sf_permits.dropna(axis=1)
    columns_with_na_dropped.head() 
 We can check how much data we lose:    
    sf_permits.shape[1]  
    columns_with_na_dropped.shape[1] 
5.filling in missing values automatically  
Another option is to try and fill in the missing values. For this next bit, let's get a small  
subsection of the data so that it will print well.  
    #get a small subset of the dataset
    subset_sf_data = sf_data.loc[:, 'EPA':'Season'].head()
    subset_sf_data 
    
We can use the Panda's fillna() function to fill in missing values in a dataframe for us. One option we have is to specify what we want the `NaN` values to be replaced with. Here, I'm saying that I would like to replace all the `NaN` values with 0.  
    #replace all NA's with 0
    subset_nfl_data.fillna(0) 
To be a bit more savvy and replace missing values with whatever value comes directly after it in the same column to have kind of logical order.   
    #Try replacing all the NaN's in the sf_permits data with the one that
    #comes directly after it and then replacing any remaining NaN's with 0
    sf_permits.fillna(method='bfill', axis=0).fillna(0)
