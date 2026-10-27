Alexis De Jesus Perez Carmona

Perceptron Monocapa Matrices General
``` python
import random
import numpy as np
import os
neuronas=3 #numero de neuronas
entradas=8 #numero de entradas considerando el umbral(bias) tambien, para este ultimo
#en este caso es igual a 1
datos=np.array([
    [1, 1, 1, 1, 1, 1, 0, 1, 1, 0, 0], 
    [0, 1, 1, 0, 0, 0, 0, 1, 0, 0, 0], 
    [1, 1, 0, 1, 1, 0, 1, 1, 1, 1, 0], 
    [1, 1, 1, 1, 0, 0, 1, 1, 0, 1, 0], 
    [0, 1, 1, 0, 0, 1, 1, 1, 1, 0, 0],
    [1, 0, 1, 1, 0, 1, 1, 1, 0, 1, 0],
    [1, 0, 1, 1, 1, 1, 1, 1, 1, 0, 0],
    [1, 1, 1, 0, 0, 0, 0, 1, 0, 1, 1],
    [1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 1],
    [1, 1, 1, 1, 0, 1, 1, 1, 0, 0, 1]
    ])
pesos=np.random.rand(neuronas, entradas) * 10
aprendiendo=True

salida=np.zeros(neuronas)
error=np.zeros(neuronas)
sumaNeta=np.zeros(neuronas)

epoca=0
maxEpocas=1000
tasaAprendizaje=0.3
archivo = open("pesosNOTMono.txt", "w")
while aprendiendo and epoca < maxEpocas:
    aprendiendo = False
    for i in range(len(datos)):
        sumaNeta = np.zeros(neuronas)

        ii=0
        j=0
        for ii in range(neuronas):
            for j in range(entradas):
                sumaNeta[ii] += datos[i][j] * pesos[ii][j]
        for s in range(neuronas):
            if sumaNeta[s] > 0:
                salida[s] = 1
            else:
                salida[s] = 0
        for s in range(neuronas):
            error[s] = datos[i][entradas + s] - salida[s]
            print(datos[i][entradas + s], ", ", salida[s], ", ", error[s])
            if error[s] != 0:
                aprendiendo = True
                for jj in range(entradas):
                    pesos[s][jj] += tasaAprendizaje * error[s] * datos[i][jj]

    print("entrenando")
    epoca += 1
    sumaNeta = np.zeros(neuronas)

if aprendiendo:
    print("No convergio en", maxEpocas, "epocas.")
else:
    print("Entrenamiento convergido en", epoca, "epocas.")

for i in range(len(datos)):
    sumaNeta = np.zeros(neuronas)

    ii=0
    j=0
    for ii in range(neuronas):
        for j in range(entradas):
            sumaNeta[ii] += datos[i][j] * pesos[ii][j]
    for s in range(neuronas):
        if sumaNeta[s] > 0:
            salida[s] = 1
        else:
            salida[s] = 0

    print("bias=", datos[i][0], "; x1=", datos[i][1], "; x2=", datos[i][2], "; x3=", datos[i][3], "; x4=", datos[i][4], "; x5=", datos[i][5], "; x6=", datos[i][6], "; x7=", datos[i][7], "; objetivo=", datos[i][8:11], " perceptron=", salida)

print("epocas: ",epoca)    
"""for i in range(len(pesos1)):
    print("peso ",(i+1)," =",pesos1[i])
for i in range(len(pesos2)):
    print("peso ",(i+1)," =",pesos2[i])
"""    
#escritura de los pesos en el archivo
cadena=""
for i in range(neuronas):
    for j in range(entradas):
        cadena+=str(pesos[i][j])+","
#cadena=cadena[0:len(cadena)-1]
#print(cadena)
archivo.write(cadena[0:len(cadena)-1])
archivo.close()

```
Prueba
``` python
import os
import numpy as np
#obtener los datos del archivo
archivo=open("pesosNOTMono.txt","r")
pesosArch=archivo.read()
archivo.close()
#iniciacion de variables y arreglos
entradas=8
neuronas=3
sumaNeta=np.zeros(neuronas)
datos=np.zeros(entradas)
pesos=np.zeros((neuronas, entradas))
salida=np.zeros(neuronas)
cont=0
cont1=0

#obtener los pesos de la cadena pesosArch
for p in pesosArch.split(","):
    if cont<entradas:
        pesos[cont1][cont]=float(p)
    else:
        cont=0
        cont1+=1
        pesos[cont1][cont]=float(p)
    cont+=1

#pedir los datos
for ii in range(entradas-1):
    datos[ii]=int(input("Introduce la entrada {}: ".format(ii+1)))
datos[entradas-1]=1

#resultado de la red
ii=0
j=0
for ii in range(neuronas):
    for j in range(entradas):
        sumaNeta[ii]+=datos[j]*pesos[ii][j]
        
print("Salida:")        
for s in range(neuronas):
    if sumaNeta[s]>0:
        salida[s]=1
    else: salida[s]=0
print ("{}, {}, {}, {}, {}, {}, {}, {} = {} {} {}".format(datos[0],datos[1], datos[2], datos[3], datos[4], datos[5], datos[6], datos[7], salida[0], salida[1], salida[2]))
print(pesos)

    

```
Salidas:
![[Pasted image 20261008084247.png]]

![[Pasted image 20261008084329.png]]

![[Pasted image 20261008084358.png]]

![[Pasted image 20261008084427.png]]