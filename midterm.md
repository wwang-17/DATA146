### Import libraries I need
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import KFold
from sklearn.model_selection import train_test_split as tts
from sklearn.preprocessing import StandardScaler as SS
from sklearn.datasets import fetch_california_housing
from sklearn.linear_model import Ridge
from sklearn.linear_model import Lasso
from sklearn.metrics import mean_squared_error
```

### Create your DoKFold
```
def DoKFold(model, your_feature_obj, your_target_obj, k, standardize = False, random_state = 146):
    kf = KFold(n_splits=k, shuffle=True, random_state=random_state)

    if standardize:
        ss = SS()

    # add an object for your training scores
    train_score = []
    # add an object for your testing scores
    test_score = []
    # add an object for your training MSE
    train_mse = []
    # add an object for your testing MSE
    test_mse = []

    # add your for loop where you create idxTrain & idxTest using kf.split with your features
    for idxTrain, idxTest in kf.split(X):
        Xtrain = X[idxTrain, :]
        Xtest = X[idxTest, :]
        ytrain = y[idxTrain]
        ytest = y[idxTest]

        if standardize:
            Xtrain = ss.fit_transform(Xtrain)
            Xtest = ss.fit_transform(Xtest)
            
        # fit your model on this line using your training data
        model.fit(Xtrain, ytrain)
        
        train_score.append(model.score(Xtrain, ytrain))        
        # use your feature and target testing data to calculate your model score and append it to the test score object
        test_score.append(model.score(Xtest, ytest))
        
        y_train_predict = model.predict(Xtrain)
        y_test_predict = model.predict(Xtest)

        #train_mse.append(mean_squared_error(ytrain, y_train_predict))
        #test_mse.append(mean_squared_error(ytest, y_test_predict))
        
        train_mse.append(np.mean((ytrain - y_train_predict) ** 2))
        test_mse.append(np.mean((ytest - y_test_predict) ** 2))
        
    return train_score,test_score,train_mse,test_mse
```
### import the data, set X as features and y as target
```
data = fetch_california_housing()

housing = pd.DataFrame(data.data)
housing.columns = data.feature_names
housing['target'] = data.target

X = np.array(housing.iloc[:, :8])
y = np.array(housing['target'])
```

### Question 15
To calculate the correlations between every feature and target, we could just calculate correlations between all variables
```
housing.corr()
```
which gives us the following output
