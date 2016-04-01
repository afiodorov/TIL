# Don't forget to normalise features before interpreting logistic regression

Yesterday I plotted `logit.coef_` to examine which coefficients contribute the
most towards the prediction. But I forgot that each feature varies on different
scale rending the exercise useless. Luckily, this one-liner fixed the issue for me:

```python
sklearn.preprocessing.normalize(X, axis=0)
```

read more [here](http://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.normalize.html).
