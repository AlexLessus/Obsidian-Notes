## Ingeniería de Características (Feature Engineering)
- **¿En qué consiste?** Es el proceso creativo y analítico de utilizar el conocimiento humano sobre un problema específico para crear **nuevas variables (características)** a partir de los datos crudos (raw data). El objetivo es resaltar la información subyacente para que el algoritmo pueda entenderla y aprender de ella más fácilmente.    
- **¿Cómo se lleva a cabo?**    
    - **Transformación matemática:** Aplicar logaritmos a datos muy dispersos o calcular porcentajes.
    - **Creación de variables compuestas:** Si tienes una columna con "Peso" y otra con "Altura", puedes aplicar ingeniería para crear una nueva columna llamada "Índice de Masa Corporal (IMC)", la cual será mucho más predictiva para un modelo de salud.
    - **Extracción de fechas:** Convertir una fecha cruda ("2026-03-25") en columnas separadas ("Es_Fin_De_Semana", "Mes", "Año").
- **Relación con el Aprendizaje Automático:** Los algoritmos solo entienden números, no el contexto del mundo real. La ingeniería de características es el "puente" que traduce el contexto humano a un formato matemático digerible, mejorando drásticamente la precisión del modelo predictivo.

---
## Extracción de Características (Feature Extraction)

- **¿En qué consiste?** Es una técnica de reducción de dimensionalidad. Consiste en tomar un conjunto grande de variables originales y comprimirlas o transformarlas en un **nuevo conjunto de variables más pequeño**, pero que matemáticamente retiene la mayor parte de la información original.
- **¿Cómo se lleva a cabo?** Se utilizan algoritmos matemáticos complejos en lugar de lógica humana.
    - El método más clásico es el **Análisis de Componentes Principales (PCA)**, que proyecta los datos en nuevas dimensiones.
    - En visión artificial, las Redes Convolucionales extraen características transformando millones de píxeles (brillo, color) en matrices numéricas que representan "bordes" o "texturas".
- **Relación con el Aprendizaje Automático:** Soluciona el problema conocido como la "Maldición de la Dimensionalidad" (cuando tienes demasiadas columnas y el modelo se confunde). Al extraer características, el modelo entrena mucho más rápido, consume menos memoria y generaliza mejor al no perderse en detalles irrelevantes.
---
## Selección de Características (Feature Selection)

- **¿En qué consiste?** A diferencia de la extracción (que crea variables nuevas), la selección consiste en **elegir y quedarse únicamente con las variables originales que son más útiles**, descartando las demás. Es literalmente un proceso de filtrado.    
- **¿Cómo se lleva a cabo?** Se emplean tres tipos de métodos principales:    
    - **Métodos de Filtro:** Usan estadística pura (como la matriz de correlación de Pearson) para eliminar variables que no tienen relación con lo que quieres predecir.        
    - **Métodos Envolventes (Wrapper):** Entrenan el modelo varias veces combinando diferentes columnas para ver qué grupo da el mejor resultado.        
    - **Métodos Integrados (Embedded):** Algoritmos (como la regularización Lasso o los Árboles de Decisión) que automáticamente penalizan y descartan variables inútiles mientras se entrenan.        
- **Relación con el Aprendizaje Automático:** Elimina el "ruido". Si intentas predecir el precio de una casa, variables como "Metros cuadrados" o "Ubicación" serán seleccionadas por su alta relevancia, mientras que "Color de la puerta" será descartada. Esto previene el **sobreajuste (overfitting)** y hace que el modelo final sea mucho más fácil de interpretar y explicar.