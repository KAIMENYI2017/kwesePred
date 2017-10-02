# kwesePred
modelling kwese's popularity and predicting its popularity in the future.
#I omitted the lines used to extract data from google
rate=kim$V1
plot(kwese1,type="l")#plot original data
kwese1=ts(rate,freq=4)#create a ts object
kwese1
      class(kwese1)#check str
    start(series1)
      end(series1)
        cycle(series1)
   plot(aggregate(series1, FUN=mean))
 boxplot(kwese1~cycle(kwese1))
  abline(reg=lm(kwese1~time(kwese1))) #fitting line of best fit on plot
 kwese2=diff(log(kwese1))
 kwese3=log(kwese1)
 
 plot(kwese2,type="l")#plot stationary series

 adf.test(kwese4)#check stationarity
 {acf(kwese2, main='acf of stationary')      #plot acf and pacfs
  pacf(kwese2, main='pacf of stationary')}
  auto.arima(log(kwese1))#find a model using automatic arima fn
fit=arima(kwese3, c(1,1,1), seasonal = list(order=c(1,1,1),period=4))
fit
fit2=arima(kwese3, c(0,1,1), seasonal = list(order=c(0,1,1),period=4))
fit2
   Box.test(fit$residuals) 
       shapiro.test(fit$residuals)
          auto.arima(fit$residuals)
       qqnorm(fit2$residuals)
         qqline(fit2$residuals)
   future=forecast(fit, level=95)
     future
plot(future,type="l",main='Current and future popularity')#plot predicted series
