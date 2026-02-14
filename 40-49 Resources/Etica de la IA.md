Tags: [[IA]] [[Aprendizaje Automático]]

La ética es un conjunto de principios morales que nos ayudan a discernir entre el bien y el mal. La ética de la IA es un campo multidisciplinario que estudia cómo optimizar el impacto beneficioso de la [inteligencia artificial (IA)](https://www.ibm.com/mx-es/think/topics/artificial-intelligence) mientras se reducen los riesgos y los resultados adversos.

### Sesgo (En general / Humano)
En un contexto amplio, el sesgo es una **inclinación o prejuicio** a favor o en contra de una persona, grupo o idea, generalmente de una manera que se considera injusta.

- **Origen:** Proviene de la cultura, experiencias personales o limitaciones cognitivas humanas.
- **Ejemplo:** Un reclutador que inconscientemente prefiere contratar a egresados de su propia universidad.
- **En Estadística:** Se refiere a la diferencia entre el valor esperado de un estimador y el valor real del parámetro (error sistemático).

### Sesgo en IA (Algorítmico / De Datos)
Es cuando un sistema de computación refleja los prejuicios humanos implícitos en los datos con los que fue entrenado, o introduce nuevos errores sistemáticos debido a un diseño defectuoso.

- **Origen:** No es que la máquina "piense mal", sino que aprende patrones de **datos históricos** que ya venían "sucios" o no representativos. El temario lo clasifica dentro de la ética porque la máquina **automatiza y amplifica** ese prejuicio a gran escala.

**La Diferencia Clave:** El sesgo humano es **subjetivo y biológico**; el sesgo en IA es **matemático y repetible**. Si los datos de entrada tienen sesgo, el modelo tendrá sesgo (Garbage In, Garbage Out).

### El Sesgo (Bias) y la Equidad (Fairness)
El sesgo en ML no siempre es un error de programación; a menudo es un **sesgo estadístico o histórico** presente en los datos de entrenamiento.

- **Sesgo de Selección:** Ocurre cuando la muestra (Train Set) no representa fielmente a la población real.
- **Sesgo Algorítmico:** Algunos modelos, como las Redes Neuronales o SVM, pueden "sobreajustar" patrones discriminatorios si la función de pérdida no penaliza estas desviaciones.
- **Analogía de Software:** Si un compilador tuviera un sesgo y solo optimizara código escrito en CamelCase, ignorando snake_case, el sistema final sería ineficiente para la mitad de los desarrolladores. En ML, esto puede significar denegar un crédito bancario injustamente.



### Responsabilidad y "Cajas Negras"
Uno de los mayores retos éticos es la **interpretabilidad**.
- **Modelos Transparentes:** Árboles de Decisión o Regresión Lineal, donde podemos trazar la lógica del resultado.
- **Modelos Opacos (Cajas Negras):** Deep Learning o Random Forest. Si un modelo de diagnóstico médico falla, ¿quién es el responsable? ¿El desarrollador, el médico o el algoritmo?.


### Privacidad y Seguridad de Datos
- Los sistemas de IA deben ser capaces de aprender patrones generales sin memorizar datos específicos de individuos que puedan ser filtrados mediante ataques de inferencia.