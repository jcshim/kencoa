# kencoa
kencoa

    sd<-3
    fd<-13
    y<-c(10250,9440,9020,8450,7780);
    x<-c(sd:7)
    lm(x~y)
    #fit first degree polynomial equation:
    #first degree
    fit1<-lm(y ~ x)
    summary(fit1)
    plot(x, y,pch=19, xlim=c(3,13), ylim=c(5000,10250), xlab = "date", ylab = "Price", col="blue", yaxt='n', xaxt='n') #25~29, 1~3일 예측해 보기
    #second degree
    fit2 <- lm(y~poly(x,2,raw=TRUE))
    #third degree
    fit3 <- lm(y~poly(x,3,raw=TRUE))
    #fourth degree
    fit4 <- lm(y~poly(x,4,raw=TRUE))
    #generate range of 31 numbers starting from 19 and ending at 50
    xx <- seq(sd, fd, length=11)
    lines(xx, predict(fit1, data.frame(x=xx)), col="red")
    lines(xx, predict(fit2, data.frame(x=xx)), col="black")
    #    lines(xx, predict(fit3, data.frame(x=xx)), col="blue")
    #    lines(xx, predict(fit4, data.frame(x=xx)), col="purple")

    grid(lty=1, lwd=1, col='gray')

    axis(side=1, at=c(sd:7), labels=c(sd:7),col.axis="blue") #, lwd=2.5)
    axis(side=1, at=c(8:fd), labels=c(8:fd))#,col="red") #, lwd=2.5)

    axis(side=2, at=y, labels=y, col.axis="blue", las=2)
    title("kencoa")
    pp <- seq(8, fd, length=5)
    predict(fit1, data.frame(x=pp))
    axis(side=2, at=pp, labels=predict(fit1, data.frame(x=pp)), col.axis="blue", las=2)
