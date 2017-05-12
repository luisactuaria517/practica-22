# practica-22
####genere una st con 252 casos
#### del 2016 al 2017 diaria con rango de 300 a 900   ##serie de ICA 8/05/16 a 8/05/17
###y obtener correlograma

ale<-sample(300:900, 252)
alet<- ts(ale, frequency = 252, start=2016)
plot(alet)
acf(alet)


ica<-read.csv(file.choose())
icas<-ts(ica, start=2016, frequency = 252)
plot(icas)
acf(icas)
##como no es estacionaria la convertimos con la diferenciación

##Para diferenciar una serie:
##x1<-diff.ts(x)
##La diferenciación se deshace con
##diffinv(x,lag,xi) 

##diferenciando la serie ICA función en R

dicas<-diff(icas)
dicas

##diferenciando la serie ICA función
f<- function(x) return(c((ica[x+1,]-ica[x,])))
x <- c(1:250)
di <- c(f(x))
di

##para comprobar vector ceros
vc=dicas-di
vc
