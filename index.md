# Multiple Boosting and LightGBM
### Anne Louise Seekford
#### DATA 410 - Advanced Applied Machine Learning - Project 4
#### 03.06.22

Created and implemented my own multiple boosting algorithm to combinations of different regressors on the "Concrete Compressive Strength" dataset. Additional application of LightGBM algorithm. 


## Overview

For project four, I created and applied a multiple boosting algorithm of my creation to two regression techniques, **X** and **Y**, on the Concrete Compressive Strength Dataset. The Concrete Compressive Strength Dataset is multivariate and our aim is to answer questions relevant to concrete in civil engineering. The 
concrete compressive strength is a highly nonlinear function of age and ingredients. These ingredients include cement, blast furnace slag, fly ash, water, superplasticizer, coarse aggregate, and fine aggregate (Darlington, 2017). 

The input features will be 'cement', 'age', and 'superplastic' describing the cement, age - the rate of gain of strength is faster to start with and the rate gets reduced with age, and superplasticizer - used in making high-strength concrete. The target, which will be predicted, is 'strength', the median value of owener-occupied homes (in thousands of dollars).



## Multiple Boosting Algorithm
la la la 
```markdown
 `some Code` text

```

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


## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/alseekford/410_Project4/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/alseekford/410_Project4/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
