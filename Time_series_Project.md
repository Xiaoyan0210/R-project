

```R
# read and transform data 
library(tseries)
cof <- read.csv("COF.csv") 
boa <- read.csv("BAC.csv")
wfc <- read.csv("WFC.csv")
cof <- ts(cof, start=c(1994, 11), end=c(2019, 10), frequency=12)
boa <- ts(boa, start=c(1994, 11), end=c(2019, 10), frequency=12)
wfc <- ts(wfc, start=c(1994, 11), end=c(2019, 10), frequency=12)
```

```r
# plot of data
par(mfrow=c(3,1))
plot.ts(cof,main="Capital One Financial Corporation")
plot.ts(boa,main="Bank of America Corporation")
plot.ts(wfc,main="Wells Fargo Corporation")
```
```r
#check stationary
adf.test(cof)
adf.test(boa)
adf.test(wfc)
```


### Capital One 
```r
#detect changepoints of cof
library(changepoint)
cof1 <- cpt.meanvar(cof,method="PELT",penalty="CROPS",pen.value=c(1,150)) 
plot(cof1,ncpts=5)
```
```r
summary(cof1)
pen.value.full(cof1)
```



```r
plot(cof1,diagnostic=T)
```



### Bank of America 
```r
boa1 <- cpt.meanvar(boa,method="PELT",penalty="CROPS",pen.value=c(1,150))
plot(boa1,ncpts=3)
summary(boa1)
plot(boa1,diagnostic=T)
```



### wells fargo
```r
wfc1 <- cpt.meanvar(wfc,method="PELT",penalty="CROPS",pen.value=c(1,150))
plot(wfc1,ncpts=3)
```
