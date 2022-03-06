# Multiple Boosting and LightGBM
### Anne Louise Seekford
#### DATA 410 - Advanced Applied Machine Learning - Project 4
#### 03.06.22

Created and implemented my own multiple boosting algorithm to combinations of different regressors on the "Concrete Compressive Strength" dataset. Additional application of LightGBM algorithm. 


## Overview

For project four, I created and applied a multiple boosting algorithm of my creation to two regression techniques, **X** and **Y**, on the Concrete Compressive Strength Dataset. The Concrete Compressive Strength Dataset is multivariate and our aim is to answer questions relevant to concrete in civil engineering. The 
concrete compressive strength is a highly nonlinear function of age and ingredients. These ingredients include cement, blast furnace slag, fly ash, water, superplasticizer, coarse aggregate, and fine aggregate (Darlington, 2017). 

Snippet of Dataset:

<img width="517" alt="Screen Shot 2022-03-05 at 7 51 03 PM" src="https://user-images.githubusercontent.com/71660299/156904631-478a1cf1-e5d2-460c-a629-8a3ecdd8af17.png">

The input features will be 'cement', 'age', and 'superplastic' describing the cement, age - the rate of gain of strength is faster to start with and the rate gets reduced with age, and superplasticizer - used in making high-strength concrete. The target, which will be predicted, is 'strength', the median value of owener-occupied homes (in thousands of dollars).



## Multiple Boosting Algorithm
la la la 
```markdown
# MY BOOSTER
def super_booster(X, y, xnew, kern, tau, model_boosting, nboost):
  Fx = boosted_lwr(X,y,X,kern,tau,True)
  Fx_new = boosted_lwr(X,y,xnew,kern,tau,True)
  new_y = y - Fx
  output = Fx
  output_new = Fx_new
  for i in range(nboost):
    model_boosting.fit(X,new_y)
    output += model_boosting.predict(X)
    output_new += model_boosting.predict(xnew)
    new_y = y - output
  return output_new
  
model_boosting = RandomForestRegressor(n_estimators=100,max_depth=3)

super_yhat = super_booster(xtrain, ytrain, xtest, Tricubic, 1, model_boosting, 1)
```
After running this "super booster", LOWESS, Boosted LOWESS, Random Forest, and XGBOOST in a nested cross-validation loop, here are the results:

<img width="696" alt="Screen Shot 2022-03-05 at 11 07 11 AM" src="https://user-images.githubusercontent.com/71660299/156891185-99ed24b9-0f50-4441-b781-4ba800d33149.png">




## LightGBM
la la la
```markdown
mse_lgb = []

for i in range(5):
  kf = KFold(n_splits=10,shuffle=True,random_state=i)
  # this is the Cross-Validation Loop
  for idxtrain, idxtest in kf.split(X):
    xtrain = X[idxtrain]
    ytrain = y[idxtrain]
    ytest = y[idxtest]
    xtest = X[idxtest]
    xtrain = scale.fit_transform(xtrain)
    xtest = scale.transform(xtest)
    
    dat_train = np.concatenate([xtrain,ytrain.reshape(-1,1)],axis=1)
    dat_test = np.concatenate([xtest,ytest.reshape(-1,1)],axis=1)

    # LightGBM
    model_lgbm = lgbm
    model_lgbm.fit(xtrain, ytrain)
    yhat_lgbm = model_lgbm.predict(xtest)
    mse_lgb.append(mse(ytest, yhat_lgbm))

```

Returns

<p align = 'center'><img width="518" alt="Screen Shot 2022-03-04 at 4 34 53 PM" src="https://user-images.githubusercontent.com/71660299/156844798-d2d5a511-5cad-4aeb-b59d-7c58dc434fd3.png">


## References

Darlington, A. (2017, September 5). Concrete Compressive Strength Data Set. Kaggle. Retrieved March 4, 2022, from https://www.kaggle.com/elikplim/concrete-compressive-strength-data-set 


## Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
