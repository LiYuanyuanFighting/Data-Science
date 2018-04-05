In the course of Data Cleaning Challenge Day 2, it introduces scaling & normalization.  
## What is Scaling?  
This means that you're transforming your data so that it fits within a specific scale,   
like 0-100 or 0-1.   
For example, One US Dollar is worth about 100 Yen, but if you don't scale your prices   
methods like SVM or KNN will consider a difference in price of 1 Yen as important as a  
difference of 1 US Dollar!  
    #generate 1000 data points randomly drawn from an exponential distribution
    original_data = np.random.exponential(size = 1000)

    # mix-max scale the data between 0 and 1
    scaled_data = minmax_scaling(original_data, columns = [0])  
    
## What is Normalization?  
The point of normalization is to change your observations so that they can be described as   
a normal distribution.  
In general, you'll only want to normalize your data if you're going to be using a machine   
learning or statistics technique that assumes your data is normally distributed.  
    #normalize the exponential data with boxcox
    normalized_data = stats.boxcox(original_data)

## Scaling vs. Normalization: What's the difference?  
 In both cases, you're transforming the values of numeric variables so that the transformed   
 data points have specific helpful properties. The difference is that, in scaling, you're   
 changing the range of your data while in normalization you're changing the shape of the   
 distribution of your data.  
 
 There is answer from Quora: [link](https://www.quora.com/What-is-the-difference-between-normalization-standardization-and-regularization-for-data)
 
