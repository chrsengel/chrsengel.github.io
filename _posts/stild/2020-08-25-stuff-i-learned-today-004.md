---
title: Stuff I learned today 004
date: 2020-08-25 19:32:00 +0200
categories: [stuff i learned today]
tags: [stild, machine learning]
math: true
---

The last week I had a short vacation but today I was back at the deep learning handbook. So this post is coming in hot with Linear Regressions.

# Linear Regression

## Definition

Linear Regression is a machine learning algorithm that attempts to find the coefficients $$w_i$$ of the function

$$y = \sum_{i=1}^{n} w_i * x^i + b$$

where $$x^i$$ defines a given feature in a dataset with $$n$$ elements.

## Fitting

Fitting is the learning act of the algorithm. Simply put, the algorithm tries to figure out a function that fits well into the training data. It does so by trying out many functions with different coefficients and summing up the distance squared between the input points (the features) and the position of the current function. Once it found a function that has the lowest total sum, the model is done learning and can be used to predict values.

### What can go wrong when fitting data?

For one, you can run into the risk to 'underfit' the model. This is essentially having a too small polynomial degree in your prediction function that misses much of the input data and has a rather large error score. To 'overfit' is the opposite extreme, where the algorithm models a function that apparently fits well into the training data, but is way too complex for the use case and therefore mispredicts future inputs. The solution is simple: More training data!

I made this illustration based on the illustration in the book. It explains the fitting types. Notice that this illustrates linear regression with only **a single feature $$x_0$$**. In practical examples (see below), many more features will be used in what is called **Multiple Linear Regression**.

![Fitting](/assets/img/stild/2020/08-25/fitting.png)

## How performance is measured

The most widely used measurements are the rooted mean squared error (RMSE) and the coefficient of determination $$R^2$$.

### RMSE

The RMSE is the square root of the residual sum of squares that result from comparing the predictions $$\hat y$$ with the known outcome $$y$$[^rmse-def].
$$ RMSE = \sqrt{\sum_{i=1}^N (y_i - \hat y_i)^2} $$

Here's a representation of residuals:

![residuals](/assets/img/stild/2020/08-25/residuals.png)

### R-squared

The R-squared value ($$R^2$$) is a metric that describes the scatter of the data points around the fitted regression function[^r-squared]. It is given as a value between 0 and 100%. The higher the value, the better the model. For more information, check out Jim Frost's take on the r-squared measurement[^r-squared].

## Example

To get my hands dirty I tried to solve the Graduate Admissions Challenge on Kaggle[^kaggle-challenge]. The challenge is to train a model that can reliably predict the chance of a student to get admitted into an university. I had to wrap my head around the perks of `sklearn` and `pandas` but I think this is the best way to learn. And I got quite successful with my model.

> I used jupyter notebook to do the challenge. You can download both [the PDF](/assets/pdf/admissions-challenge.pdf) and the [file](/assets/python/admissions-challenge.ipynb).

First, handle the imports. I used the popular python libraries for this task. To easily install all of the needed modules at once, I recommend getting the Anaconda pack[^anaconda].

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn import linear_model
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error, r2_score

import seaborn as sns
sns.set()
```

Then have a look at the data:

```python
# load data
df = pd.read_csv("./data/Admission_Predict.csv")  # load data
df = df.drop(['Serial No.'], axis = 1)            # drop unneeded column
df.describe(include='all')
```

This will return the following table:

|       | GRE Score | TOEFL Score | University Rating | SOP      | LOR      | CGPA     | Research | Chance of Admit |
| ----- | --------- | ----------- | ----------------- | -------- | -------- | -------- | -------- | --------------- |
| count | 400       | 400         | 400               | 400      | 400      | 400      | 400      | 400             |
| mean  | 316.8075  | 107.41      | 3.0875            | 3.4      | 3.4525   | 8.598925 | 0.5475   | 0.72435         |
| std   | 11.473646 | 6.069514    | 1.143728          | 1.006869 | 0.898478 | 0.596317 | 0.498362 | 0.142609        |
| min   | 290       | 92          | 1                 | 1        | 1        | 6.8      | 0        | 0.34            |
| 25%   | 308       | 103         | 2                 | 2.5      | 3        | 8.17     | 0        | 0.64            |
| 50%   | 317       | 107         | 3                 | 3.5      | 3.5      | 8.61     | 1        | 0.73            |
| 75%   | 325       | 112         | 4                 | 4        | 4        | 9.0625   | 1        | 0.83            |
| max   | 340       | 120         | 5                 | 5        | 5        | 9.92     | 1        | 0.97            |

As we can see, we want to predict the value of the `Chance of Admit` column. Therefore, the function our algorithm has to figure out the coefficients to, is the following:

$$chance = w_1 * GRE Score + w_2 * TOEFL Score + ... + m_7 * research  $$

Let's define some functions before we go any further.

```python
# define function to train the model
def train_model(X, Y):
    reg = linear_model.LinearRegression()
    reg.fit(X, Y)
    return reg

# define function to test the model
def test_model(reg, X_test, Y_test):
    # predict
    Y_pred = reg.predict(X_test)

    # measure performance
    mse = mean_squared_error(Y_test, Y_pred)
    rmse = np.sqrt(mse)

    r2 = r2_score(Y_test, Y_pred)
    print('RMSE: %f' % mse)
    print('r2:   %f' % r2)
```

Now we can split the raw data into training and testing data and train the model using our `train_model` method. Note, that we do not modify any of the columns for now.

```python
# split the data
train,test = train_test_split(df, test_size=0.2)

# train the model
X = train[['GRE Score', 'TOEFL Score', 'University Rating', 'SOP', 'LOR ', 'CGPA', 'Research']]
Y = train[['Chance of Admit ']]
reg = train_model(X, Y)
```

Once the model is trained we can start test process using the `test_model` method:

```python
X_test = test[['GRE Score', 'TOEFL Score', 'University Rating', 'SOP', 'LOR ', 'CGPA', 'Research']]
Y_test = test[['Chance of Admit ']]
test_model(reg, X_test, Y_test)
```

In my case this returned the following output:

```
RMSE: 0.004481
r2:   0.786817
```

As we can see, the RMSE is already pretty low at `0.004481`. The $$R^2$$ value however is rather low. Remember: We want RMSE to go as low as possible and get the $$R^2$$ as close to `1` as possible. In order to get better results we can apply a process that is called feature scaling. The topic deserves it's own post and to be honest I am still a total beginner so I have to look further into it myself.

Essentially, feature scaling can be used 'to normalize the range of independent variables or features of data'[^feature-scaling]. Since the Linear Regression algorithm uses the distance between two points to come up with an approximation function, it will run into problems if the data has a broad range of values. Feature Scaling helps mitigate this issue by making sure that 'each feature contributes approximately proportionately to the final distance'[^feature-scaling].

In the challenge data I noticed, that both the columns 'GRE Score' and 'TOEFL Score' had two properties:

- both highly correlate with the chance of getting admitted to the university and
- both have a broad range of values

To normalize both columns to a range of 0-100% I applied the min-max normalization.

```python
from sklearn.preprocessing import MinMaxScaler

def scale_data(df):
    scaler = MinMaxScaler()
    df['scaled_gre'] = scaler.fit_transform(df['GRE Score'].values.reshape(-1,1))
    df['scaled_toefl'] = scaler.fit_transform(df['TOEFL Score'].values.reshape(-1,1))
    return df
```

If we run the training and testing methods again with these new columns, we achieve a much better performance.

```python
# scale data
df = scale_data(df)

# split data again
train,test = train_test_split(df, test_size=0.2)

# train model
X = train[['scaled_gre', 'scaled_toefl', 'University Rating', 'SOP', 'LOR ', 'CGPA', 'Research']]
Y = train[['Chance of Admit ']]
reg = train_model(X, Y)

# Predict on the test data
X_test = test[['scaled_gre', 'scaled_toefl', 'University Rating', 'SOP', 'LOR ', 'CGPA', 'Research']]
Y_test = test[['Chance of Admit ']]

test_model(reg, X_test, Y_test)
```

This time it returned:

```
RMSE: 0.003121
r2:   0.805031
```

I attempted multiple other normalizations but none gave me better results than the ones above.

# Summary

The Linear Regression seems like an easy-to-understand algorithm that serves as a great entry point into the field of machine learning. I am sure I can iterate on the things I learned today in the future as I progress with the Deep Learning Book[^book] and my Bachelor thesis.

---

There is no comment section on this blog as it's just static content, but please feel free to hit me up on [Twitter](https://twitter.com/chrsengel) and tell me your best RMSE and $$R^2$$ values for the challenge!

# Footnotes

[^rmse-def]: [Performance Measures](https://www.datascienceblog.net/post/machine-learning/performance-measures-model-selection/)
[^kaggle-challenge]: [Kaggle Challenge](https://www.kaggle.com/mohansacharya/graduate-admissions)
[^r-squared]: [Interpretation of $$r^2$$](https://statisticsbyjim.com/regression/interpret-r-squared-regression/)
[^feature-scaling]: [Feature Scaling Wiki Entry](https://en.wikipedia.org/wiki/Feature_scaling)
[^anaconda]: [Anaconda](https://docs.anaconda.com/anaconda/install/)
[^book]: [https://www.deeplearningbook.org/](https://www.deeplearningbook.org/)
