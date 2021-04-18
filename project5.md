### Question 1
Use read_csv to read csv file as a dataframe.
```
pns = pd.read_csv('persons.csv')
```

Then check if there are any null values in the variable age, and drop those if there are any. Then convert all values in age and education from float to integers. Select all variables except for wealthC and wealthI as features, and select wealthC as the target.
```
check_nan = pns['age'].isnull().values.any()
pns.dropna(inplace = True)

pns['age'] = pns['age'].astype(int)
pns['edu'] = pns['edu'].astype(int)


X = pns.drop(["wealthC", "wealthI"], axis = 1)
y = pns.wealthC
```

### Question 2
* Linear regression w/o standardization of features
  * MSE: 0.44281007841525455
  * R^2: 0.7358226925730341

  * the coefficients for this model are:
```
array([ 3.01812923e-02,  1.07882853e-02, -5.57603897e-04,  8.37880684e-02,
        4.04701739e-02,  6.37198352e-02, -1.40023112e-01,  9.99896825e-02,
        1.85515805e-01, -2.49517259e-01, -2.47122665e-01, -7.30324831e-02,
        3.09612080e-01, -1.29375995e-01,  3.53607318e-01,  2.33225714e-01,
       -1.34364084e-01, -1.92558301e-01, -1.20146711e-01,  3.59279100e-02,
        1.46004504e-01, -1.81932414e-01,  1.05944573e-01,  4.00186663e-01,
        1.72822325e-01,  2.29943453e-02,  1.03043774e-01, -1.15888783e-01,
       -2.18966624e-01, -2.90949455e-01, -3.83672661e-01, -3.84737293e-01,
        3.07519898e-01,  2.55401258e-02,  2.56163113e-01,  3.95033383e-01,
        3.60442298e-01,  1.90435535e-01,  3.86891012e-01,  1.53405264e-01,
       -2.09042764e-02,  5.43122461e-02, -1.27172669e-01, -5.40268677e-01,
       -5.63637093e-01, -1.58355761e-01, -1.08923385e-01, -2.12578757e-02,
       -3.26132080e-01,  3.26132080e-01, -6.44297719e-02,  6.44297719e-02,
       -2.76390443e-01,  4.32693258e-01,  6.03439291e-02,  4.07576086e-01,
       -6.37787977e-01,  1.35651470e-02, -2.47897601e-01,  2.47897601e-01])
```

* Linear regression w/ standardization of features
  * MSE: 0.4428132426395805
  * R^2: 0.7358208048195631

  * the coefficients for this model are:
```
array([ 1.12548658e-01,  5.24358116e-03, -1.08884589e-02,  6.92579735e-02,
        7.36951509e+10,  8.66257201e+10,  7.69209583e+10,  7.91372426e+10,
        8.45473781e+10,  7.89854838e+10,  7.88333540e+10,  8.76583681e+10,
        8.66134726e+10,  8.54267349e+10,  1.16140874e+11,  1.01070442e+11,
        7.65053798e+10,  7.51091695e+10,  8.19133567e+10,  4.80000747e+10,
        7.26531241e+10,  7.87003037e+10, -6.56609287e+09, -6.60161265e+09,
       -1.20447035e+10, -1.40140921e+10, -7.23238899e+10, -3.56557715e+10,
       -1.50138208e+10, -2.23537221e+10, -6.34833466e+10, -4.69533271e+09,
       -7.80211026e+09, -1.23673099e+10, -1.59629508e+10,  5.30991560e+10,
        2.31813714e+11,  8.95044996e+10,  4.32553262e+10,  1.67206073e+10,
        3.49539754e+11,  2.11161816e+11,  2.27988135e+11,  4.41825617e+11,
        1.81354767e+10,  2.62747629e+10,  1.66594092e+11,  3.43909538e+10,
       -2.42890031e+11, -2.42890031e+11,  1.82248582e+10,  1.82248582e+10,
        1.21238081e+10,  5.65381739e+09,  1.10197079e+10,  2.38345511e+11,
        2.39952072e+11,  3.49669495e+10, -4.32651302e+10, -4.32651302e+10])
```

From the above, we can conclude that although standardizing features makes coefficients change a lot, it does not significantly improve the MSE/R^2 of the fitted model.

### Question 3
For all models I used testing score to judge the performance of the model, and also check the corresponding MSE as an additional criteria for the model performance. For all model I've chosen to use 10-fold, since according to previous experience changing k would nott bring a significant difference to the result.

* Features not standardized
  * optimal alpha = 1.918
  * test score = 0.7351243213874814
  * corresponding mse for testing set = 0.4437601409048126

* Features standardized
  * optimal alpha = 178.367
  * test score = 0.7347978838768205
  * corresponding mse for testing set = 0.44431512189470557

### Question 4

* Features not standardized
  * optimal alpha = 0
  * test score = 0.7351221624062736
  * corresponding mse for testing set = 0.4437638151795899

* Features standardized
  * optimal alpha = 0
  * test score = 0.7346360932167861
  * corresponding mse for testing set = 0.44458667410775776

  While I know is not normal to get 0 for the optimal alpha, I checked the code and ran for a bunch of times, but I still got that result.


### Question 5
* Linear regression
  * w/o features standardized
    * R^2: 0.8258271939658526
    * MSE: 1750276834.9304745
  * w/ features standardized
    * R^2: 0.8258260281336447
    * MSE: 1750288550.4740968

  From those results we can see that although R^2 improve with using WealthI as feature, the MSE becomes extremely huge, which is not helpful for making predictions.

* Ridge regression
  * w/ features standardized
    * optimal alpha(testing score maximized): 138.673 
    * testing score: 0.8251526252146713
    * corresponding mse for testing set: 1754638528.101476
  * w/o features standardized
    * optimal alpha(testing score maximized): 1.061
    * testing score: 0.8251540421390537
    * corresponding mse for testing set: 1754626085.3042407

* Lasso regression
  * w/ features standardized
    * optimal alpha(testing score maximized): 0
    * testing score: 0.8251517646558494
    * corresponding mse for testing set: 1754646342.5832162
  * w/o features standardized
    * optimal alpha(testing score maximized): 69.388
    * testing score: 0.8245432140374891
    * corresponding mse for testing set: 1760767666.9810853
 
 ### Question 6
 First of all, all the model using WealhI as the target should not be used since they all have extremely large MSE, even those corresponding to the optimal alpha in ridge and lasso regression. 
 
 For models using WealthC as the target, there is not significant difference between the testing score or MSE for all 6 types of model(three types of regression with or without features standardized). Actually, if we just look at three digits after the decimal point, they are exactly the same. Thus, all these 6 models can be seen as the "best" model.
 


