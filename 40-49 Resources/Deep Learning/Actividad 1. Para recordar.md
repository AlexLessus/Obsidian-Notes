Perceptron
```` python
#perceptron compuerta or formula general a=f(Wtp+b)

import random
import numpy as np
import os

p=np.array([[1,1,1],[2,1,1],[1,2,1],[2,2,1],[4,4,1],[5,4,1],[4,5,1],[5,5,1]])#contiene el bias
sE=np.array([0,0,0,0,1,1,1,1])
W=np.array([random.random()*10,random.random()*10,random.random()*10])
aprendiendo=True
salida=0
epoca=0
tasa=0.3
archivo=open("pesosOrG.txt","w")

while aprendiendo:
    aprendiendo=False
    for i in range(len(p)):
        sumaNeta=0
        for j in range(len(p[i])):
            sumaNeta+=p[i][j]*W[j]
        if sumaNeta>0:
            salida=1
        else:
            salida=0
        error=sE[i]-salida
        if error!=0:
            for j in range(len(p[i])):
                W[j]+=tasa*error*p[i][j]        
            aprendiendo=True
        epoca+=1
        print("Aprendiendo")
  
for i in range(len(p)):
    sumaNeta=0
    for j in range(len(p[i])):
        sumaNeta+=p[i][j]*W[j]
    if sumaNeta>0:
        salida=1
    else:
        salida=0
    print(p[i][0],',',p[i][1],'=',sE[i],' perceptron=',salida)
print('epocas=',epoca)
cad=""

for i in range(len(W)):
    print('peso ',(i+1),'=',W[i])
    cad+=str(W[i])+","
cad=cad[:len(cad)-1]

archivo.write(cad)

archivo.close()
````
Prueba
![[Pasted image 20260921075810.png]]

--- 
PruebaPerceptron
```` python
#prueba perceptron compuerta or
import os
#obtenemos los datos del archivo pesosOr
archivo=open("pesosOrG.txt","r")
pesosArch=archivo.read()
archivo.close

#convertir los pesosArch a valor numerico
pesos=[float(p) for p in pesosArch.split(',')]

#pedimos datos al usario
x1=int(input('proporcionar entrada 1 '))
x2=int(input('proporcionar entrada 2 '))

#aplicamos los datos entrenados de nuestro perceptron para obtener la salida
sumaNeta=x1*pesos[0]+x2*pesos[1]+pesos[2]
if sumaNeta>1:
    salida=1
else:
    salida=0

#imprimimos resultados
print("{}, {} = {}".format(x1,x2,salida))


````
Prueba
![[Pasted image 20260921080225.png]]


