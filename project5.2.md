### Execute a K-nearest neighbors classification method on the data. What model specification returned the most accurate results? Did adding a distance weight help?

In order to make sure that training and testing set are kept the same to better evaluate the performance of different types of model, I set random_state = 146.

w/o distance weight

![](p5.1.png)

The test score is maximized(0.5510004880429478) when k = 65.

w/ distance weight

![](p5.2.png)

The test score is maximized(0.4924353343094192) when k = 75, so adding distance weight does not help with increasing accuracy.

### Execute a logistic regression method on the data. How did this model fair in terms of accuracy compared to K-nearest neighbors?

I got 0.5478515625 for training score and 0.550024402147389 for testing score. If we compare testing score, logistic regression is better than KNN w/ weight and is slightly less accurate than KNN w/o weight.

### Next execute a random forest model and produce the results. See the number of estimators (trees) to 100, 500, 1000 and 5000 and determine which specification is most likely to return the best model. Also produce results for your four different estimator values by both comparing both standardized and non-standardized (raw) results.

#### non-standardized

* 100 trees
  * test score = 0.4802342606149341
  * accuracy (using compare class) = 0.4807223035627135

* 500 trees
  * test score = 0.48121034651049294
  * accuracy = 0.4763299170326989

* 1000 trees
  * test score = 0.48462664714494874
  * accuracy = 0.48560273304050755

* 5000 trees
  * test score = 0.4880429477794046
  * accuracy = 0.488530990727184 

Based on both test score and accuracy, 5000 trees is most likely to return the best model.

#### standardized

* 100 trees
  * test score = 0.4851146900927282
  * accuracy (using compare class) = 0.4802342606149341

* 500 trees
  * test score = 0.48657881893606636
  * accuracy = 0.48657881893606636

* 1000 trees
  * test score = 0.48755490483162517
  * accuracy = 0.48462664714494874
 
* 5000 trees
  * test score = 0.48462664714494874
  * accuracy = 0.48462664714494874

Based on accuracy, 500 trees is most likely to return the best model. Based on test score, 1000 trees is most likely to return the best model.

### Also test the minimum number of samples required to split an internal node with a range of values.


