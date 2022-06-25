# module_14_challenge
Challenge assignment for module 14


# Original Algorithm Analysis

## Graph of Returns
![Graph of Cumulative Returns](Starter_Code/Resources/baseline.png)

Analyzing this graph, this algorithm did not provide any different returns until around 2018, where the algorithm's returns began to overtake the actual.  It is a decent algorithm, since it provides greater returns than simply holding the stock.



# Tuning the Baseline

## Adjusting the size of training dataset

## Decreasing the size
![Decreasing the size](Starter_Code/Resources/tuned_dataset_size_smaller.png)

Decreasing the size of the dataset provided increased returns for the beginning of the dataset and greater returns towards the end of the dataset.

## Increasing the size
![Increasing the size](Starter_Code/Resources/tuned_dataset_size_larger.png)

Increasing the size of the dataset gave equally sized returns to the baseline up to a certain point, but it began to return much less than the baseline in 2020, possibly due to high volatility.


Assumption: Decreasing the size of the dataset could be beneficial to a point, to avoid sensitivity to big changes.



## Adjusting the SMA windows

## Decreasing the window
![Decreasing the window](Starter_Code/Resources/tuned_sma_fewer.png)

Decreasing the window provided similar returns to the baseline, except for a period where it returns less. The returns are overall smaller. 


## Increasing the window
![Increasing the window](Starter_Code/Resources/tuned_sma_greater.png)

Increasing the window was around the baseline for the earliest and latest dates in the data, but provided outsized returns in the middle dates.

Assumption:  A greater window for the SMA is likely to smooth out some of the noise and decrease sensitivity to change to provide a greater return in the end.


# Tuned Baseline
![Tuned Baseline](Starter_Code/Resources/tuned_baseline.png)

For this new algorithm, the short window for the SMA was increased (7) and the long window was decreased (90).  It seemed that having a tighter window between the short and long moving averages offset returns to the positive.  A shorter window captures too many changes, and a longer long window seemed to not be able to react quickly enough.  The dataset is also smaller (DateOffset(months=1)), allowing the algorithm to adjust to minor changes without sensitivity.  In conclusion, this tuning helped increase the algorithm's returns.



# Alternate Classifier

![Alt Classifier](Starter_Code/Resources/alt_classifier.png)

For this model, I chose to use the AdaBoost classifier, and ensemble learning method.  I thought it would be a better classifier because it iterates over weak classifiers to learn from their mistakes and create stronger ones.  This algorithm provided much greater returns than when using the prior method, but it takes a sharp downturn and returns much less as time goes on.  It might need to be constantly adjusted.

## Alt 2

![Alt Classifier](Starter_Code/Resources/alt_classifier_2.png)

I wanted to see if I could improve the sharp loss towards the end of the dataset, so I attempted to use the SMA windows and dataset size from the previous model, but it caused the algorithm to realize losses.  Instead, I increased the spread between the moving averages (short=3, long=110), and it caused outsized returns and no reversal towards the later dates.  I think increasing the spread between the moving averages helps the model get a better picture of the patterns over time for small and large changes.  Then, making the dataset smaller (months=1) helped it to tighten the predictions even further by decreasing its sensitivity to changes.

### Conclusion

Overall, the AdaBoost method seems to be an improvement upon the SVC method, simply because it reiterates over the classifiers to make them better at predicting.  Changing the SMA windows and dataset size affects the algorithms in different ways, also.