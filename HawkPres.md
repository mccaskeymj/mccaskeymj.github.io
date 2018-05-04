Hawk Weight
========================================================
author: Matt McCaskey
date: 5/4/18
autosize: true

The Data
========================================================



I used the `Hawks` dataset from the `Stat2Data` package

The variables in this dataset are: 

  Month, Day, Year, Species, Age, Sex, Wing, Weight, Culmen, Hallux, Tail, StandardTail, Tarsus, WingPitFat, KeelFat, CaptureTime, ReleaseTime, BandNumber, and Crop

I want to predict the weight of a given hawk.


Data Cleaning and Selection
========================================================

First I removed the variables dealing with ID numbers and time of day.

```r
Data <- knnImputation(Data, k = 10)
```





```r
mod <- lm(formula = Weight ~ Wing + Culmen + KeelFat + Day + Species + Sex + Crop + WingPitFat, data = train)
yhat <- predict(mod, newdata = test)
RMSE <- sqrt(mean((test$Weight - yhat)^2))
RMSE
```

```
[1] 129.2384
```



Tree Model
========================================================

![plot of chunk unnamed-chunk-5](HawkPres-figure/unnamed-chunk-5-1.png)

Tree Model cont.
========================================================


```r
yhat <- predict(HawkHome, newdata = test)
RMSE <- sqrt(mean((test$Weight - yhat)^2))
RMSE
```

```
[1] 148.1981
```

Culmen Model
========================================================


```r
CulmenMod <- lm(Weight ~ Culmen + Species, data = train)
yhat <- predict(CulmenMod, newdata = test)
RMSE <- sqrt(mean((test$Weight - yhat)^2))
RMSE
```

```
[1] 131.3983
```
