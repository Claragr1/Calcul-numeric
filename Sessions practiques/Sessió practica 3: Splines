import numpy as np
import matplotlib.pyplot as plt
import scipy.interpolate

dataX = np.array([0, 1, 3, 4, 5, 7])
dataY = np.array([1, 1.25, 1, 0.5, 0, 0.4])


def calculaDerivada(x,y):
    n = len(x) - 1
    der = np.zeros(n + 1)
    der[0] = (y[1] - y[0]) / (x[1] - x[0])
    # for i in range(1,len(x)-1):
    #    der[i] = (y[i+1] - y[i-1]) / (x[i+1] - x[i-1])
    i = np.arange(1, n)
    der[i] = (y[i+1] - y[i-1]) / (x[i+1] - x[i-1])
    der[n] = (y[-1] - y[-2]) / (x[-1] - x[-2])
    return der

#------------------------------------------------------------
# Spline cubic amb aproximació de les derivades
#------------------------------------------------------------
der = calculaDerivada(dataX, dataY)
splineCubicC1 = scipy.interpolate.CubicHermiteSpline(dataX, dataY, der)
print('Coeficients del spline: ', splineCubicC1.c)

x = np.arange(0,7.02,0.05)
y1 = splineCubicC1(x)
dy1 = splineCubicC1(x, nu = 1)   # primera derivada del spline
d2y1 = splineCubicC1(x, nu = 2)  # segona derivada del spline
plt.plot(dataX, dataY,'k*')
plt.plot(x,y1,label = 'S')
plt.plot(x,dy1,label = 'dS')
plt.plot(x,d2y1, label = 'd2S')
plt.title('Spline cubic C1 i les seves derivades')
plt.grid()
plt.legend()
plt.show()

#Tasca 1

'''                                                                                   
Com s'han aproximat les derivades? (DIFERENCIES FINITES)                              
- Als extrems, fa servir la pendent entre el punt i el seu veí.                                                                        
- Pels punts interiors, fa servir una diferència centrada però saltant-se el punt central:                                                                                  
(dataY[i+1] - dataY[i-1]) / (dataX[i+1] - dataX[i-1]).                                
Això és aproximadament el pendent de la recta secant que uneix el punt anterior i el posterior.                                                                             
                                                                                      
Quina continuïtat té la funció obtinguda?                                             
NOTA: La funció CubicHermiteSplinegenera un spline cúbic a trossos                    
      que garanteix interpolar el valor () i la derivada () a cada node.              
La funcio es C1, ja que la primera deriva és continua, pero la segona en canvi 
no ho és, ja que té salts de discontinuitat.                                                                       
        
'''

#Tasca 2

#La funció Phi2 té valor 1 al x2 i zero a la resta.
