### Question 1
Given that there are 715 rows in total, I have tried 8, 10, 12, 15 folds and the corresponding average of train and test scores are as the following:

k = 8: train score: 0.019477178686178; test score: -0.024545646835335944

k = 10: train score: 0.019514638368914018; test score: -0.037502267848572614

k = 12: train score: 0.019399126134301125; test score: -0.025932644957946994

k = 15: train score: 0.019206809563629627; test score: -0.036841997269859754

For all the above choices of folds, the scores are all pretty far from 1. For test scores those are even below zero. Those indicate that linear model fitted in this way is not able to produce reliable result.

### Question 2
Same choices of number of folds is applied here, and the corresponding average of train and test scores are as the following:

k = 8: train score: 0.01947717868617793; test score: -0.024545646835334625

k = 10: train score: 0.019514638368914004; test score: -0.037502267848572315

k = 12: train score: 0.019399126134301115; test score: -0.025932644957947327

k = 15: train score: 0.019206809563629655; test score: -0.03684199726985993

All the training and testing scores are still extremely small or even negative. In fact, there is not much difference between the scenario with and without the standardizaiton of features. Standarzing features is not the way to improve the performance of model.

### Question 3
If features are not standardized, the optimal alpha value and the correponding training and testing score are as the following:

k = 8: optimal alpha value: 523.232(alpha chosen between [0,700]); train score: 0.019; test score: -0.023

k = 10: optimal alpha value: 523.232; train score: 0.019; test score: -0.023
