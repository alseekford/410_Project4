# Multiple Boosting and LightGBM
### Anne Louise Seekford
#### DATA 410 - Advanced Applied Machine Learning - Project 4
#### 03.06.22

Created and implemented my own multiple boosting algorithm to combinations of different regressors on the "Concrete Compressive Strength" dataset. Additional application of LightGBM algorithm. 


## Overview

For project four, I created and applied a multiple boosting algorithm of my creation to two regression techniques on the Concrete Compressive Strength Dataset. The Concrete Compressive Strength Dataset is multivariate and our aim is to answer questions relevant to concrete in civil engineering. The 
concrete compressive strength is a highly nonlinear function of age and ingredients. These ingredients include cement, blast furnace slag, fly ash, water, superplasticizer, coarse aggregate, and fine aggregate (Darlington, 2017). 

Snippet of Dataset:

<p align = 'center'><img width="517" alt="Screen Shot 2022-03-05 at 7 51 03 PM" src="https://user-images.githubusercontent.com/71660299/156904631-478a1cf1-e5d2-460c-a629-8a3ecdd8af17.png">  
  
  The input features will be 'cement', 'age', and 'superplastic' describing the cement, age - the rate of gain of strength is faster to start with and the rate gets reduced with age, and superplasticizer - used in making high-strength concrete. The target, which will be predicted, is 'strength', the median value of owener-occupied homes (in thousands of dollars).



## Multiple Boosting Algorithm
  
  
<p align = 'center'><img width="533" alt="Screen Shot 2022-03-10 at 6 05 37 PM" src="https://user-images.githubusercontent.com/71660299/157770032-5e8a1938-6bf6-40b7-a989-632fc3cc5a29.png">
<p align = 'center'><img width="471" alt="Screen Shot 2022-03-10 at 6 05 57 PM" src="https://user-images.githubusercontent.com/71660299/157770053-426045af-79ae-4946-8bc4-66f74ef9cf1e.png">
<p align = 'center'><img width="565" alt="Screen Shot 2022-03-10 at 6 06 39 PM" src="https://user-images.githubusercontent.com/71660299/157770117-7b580972-7111-486a-b927-6102a5143c9f.png">  
  
  After running this "super booster", LOWESS, Boosted LOWESS, Random Forest, and XGBOOST in a nested cross-validation loop: 
  
<p align = 'center'><img width="971" alt="Screen Shot 2022-03-10 at 6 08 19 PM" src="https://user-images.githubusercontent.com/71660299/157770308-915b35ed-ef86-4480-9b23-361290d4fb13.png">  
  
  Here are the results:
<p align = 'center'><img width="971" alt="Screen Shot 2022-03-10 at 6 08 19 PM" src="https://user-images.githubusercontent.com/71660299/157770308-915b35ed-ef86-4480-9b23-361290d4fb13.png">

<p align = 'center'><img width="696" alt="Screen Shot 2022-03-05 at 11 07 11 AM" src="https://user-images.githubusercontent.com/71660299/156891185-99ed24b9-0f50-4441-b781-4ba800d33149.png">  
  
  It is clear that the boosted algorithms performed much better than the others. Although, the Boosted Locally Weighted Linear Regression Model resulted in a slightly lower MSE resulting in a better result than the "super booster".  
  
  ## LightGBM

LightGBM is a gradient-boosting framework that utilizes a vertically-based tree structure learning algorithm. Due to the vertical flow, LightGBM can significantly outperform XGBoost and other regressors in terms of both computational speed and memory consumption (Guolin et al.). With that being said however, LightGBM is sensitive to overfitting, and is recommended to be used on larger datasets. There is a variety of parameters to include to improve results, a few examples including (Mandot, 2018): 
  - learning_rate: determines the impact each tree has on the final outcome
  - num_leaves: number of leaves in a full tree (31 is default)
  - num_boost_round: number of boosting iterations
  - boosting: defines the type of algorithm running (can choose traditional Gradient Boosting Decision Tree (gbdt), Random Forest (rf), etc.)
  

After calling the LightGBM regressor, here is the K-fold cross validation loop I ran on the LightGBM model: 
  
<p align = 'center'><img width="517" alt="Screen Shot 2022-03-10 at 6 10 16 PM" src="https://user-images.githubusercontent.com/71660299/157770539-28ee9a18-97ed-4d93-bc15-17659fb1fc15.png">  
  
  LightGBM Returns

<p align = 'center'><img width="518" alt="Screen Shot 2022-03-04 at 4 34 53 PM" src="https://user-images.githubusercontent.com/71660299/156844798-d2d5a511-5cad-4aeb-b59d-7c58dc434fd3.png"> 
  
  ### Clearly, LightGBM outpreformed all regression models and boosted regressors. 


## References

Darlington, A. (2017, September 5). Concrete Compressive Strength Data Set. Kaggle. Retrieved March 4, 2022, from https://www.kaggle.com/elikplim/concrete-compressive-strength-data-set 
  
Guolin, et al. (n.d.). LightGBM: A highly efficient gradient boosting decision tree. Retrieved March 10, 2022, from https://papers.nips.cc/paper/2017/file/6449f44a102fde848669bdd9eb6b76fa-Paper.pdf 
  
Mandot, P. (2018, December 1). What is LIGHTGBM, how to implement it? how to fine tune the parameters? Medium. Retrieved March 10, 2022, from https://medium.com/@pushkarmandot/https-medium-com-pushkarmandot-what-is-lightgbm-how-to-implement-it-how-to-fine-tune-the-parameters-60347819b7fc 


## Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
