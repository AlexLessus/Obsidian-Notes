# K-means clustering
El **k-means** (o agrupación de k-medias) es uno de los algoritmos de aprendizaje automático no supervisado más populares y se utiliza específicamente para la **agrupación de datos (clustering)**. Su objetivo principal es dividir un conjunto de datos no etiquetados en grupos similares o "clústeres".

Es un método de agrupación "exclusivo" o "duro", lo que significa que un punto de datos específico solo puede pertenecer a un único clúster a la vez.

## **¿Cómo funciona?**
El algoritmo es de naturaleza iterativa y se basa en el uso de **centroides** (el punto central de un clúster, que representa la media o mediana de todos los puntos dentro de él). El proceso sigue estos pasos generales:
1. **Definir el valor de "K":** La letra "K" representa el número de grupos en los que se dividirá el conjunto de datos. Un valor K mayor genera grupos más pequeños y detallados, mientras que un valor K menor produce grupos más grandes con menos nivel de detalle.
2. **Inicializar los centroides:** El algoritmo selecciona aleatoriamente o mediante métodos de muestreo "K" centroides iniciales.
3. **Asignación:** Mide la distancia matemática (generalmente la distancia euclidiana) entre cada punto de datos y los centroides, asignando cada punto de datos al clúster de su centroide más cercano. El objetivo es minimizar la suma de las distancias entre los puntos y el centro de su grupo.
4. **Recálculo y maximización:** Calcula la media de todos los puntos asignados a cada clúster y reposiciona el centroide.
5. **Iteración:** El proceso de reasignar puntos y mover el centroide se repite hasta que las posiciones de los centroides dejan de cambiar (se alcanza la convergencia) o se agota el número máximo de iteraciones.