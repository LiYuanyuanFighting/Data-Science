It is common that the data we are going to analyze are not complete, here we will  
study how to clean data.  
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
 
