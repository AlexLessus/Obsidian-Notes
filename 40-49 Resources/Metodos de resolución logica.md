Alexis De Jesus Perez Carmona

El **método de resolución** es una técnica matemática de demostración de teoremas utilizada en la lógica proposicional y la lógica de primer orden. Fue introducida por John Alan Robinson en 1965 y es la base teórica de cómo "piensan" y deducen los lenguajes de programación lógica.

## El Principio Base: Reducción al Absurdo
La resolución no intenta probar que algo es directamente verdadero. En su lugar, utiliza una prueba por contradicción (reducción al absurdo):

1. Tomas todo tu conocimiento (las reglas y hechos).    
2. Tomas la pregunta o hipótesis que quieres probar y **la niegas**.    
3. Intentas combinar estas sentencias hasta encontrar una contradicción lógica (llamada "cláusula vacía").
4. Si encuentras una contradicción, significa que la negación de tu hipótesis era falsa, por lo tanto, **tu hipótesis original es verdadera**.

La regla matemática de resolución toma dos cláusulas con literales opuestos y los cancela:

$$\frac{A \vee B, \quad \neg A \vee C}{B \vee C}$$
## Estrategias y Métodos de Resolución
Dado que intentar combinar todas las reglas posibles en una base de datos grande llevaría una eternidad (explosión combinatoria), existen diferentes "estrategias" o métodos para guiar esta resolución de manera eficiente:

- **Resolución Básica (General):**    
    Es el método de fuerza bruta. Compara todos los pares posibles de cláusulas buscando opuestos para cancelar. Es completo (siempre encuentra la respuesta si existe), pero computacionalmente muy ineficiente para programas reales.
    
- **Resolución Unitaria:**    
    Esta estrategia exige que, en cada paso de resolución, al menos una de las dos cláusulas que se van a combinar sea una **cláusula unitaria** (una sentencia que contiene un solo literal, por ejemplo, un hecho simple como $humano(socrates)$). Ayuda a reducir el tamaño del problema rápidamente, pero no siempre es capaz de resolver todos los tipos de problemas lógicos.
    
- **Resolución Lineal:**    
    En este método, se establece una cadena estricta. Comienzas con la meta que quieres probar (negada) y la resuelves con una cláusula de la base de datos para generar un resultado intermedio (resolvente). En el siguiente paso, **debes** usar obligatoriamente ese resultado intermedio recién generado. Esto evita que el sistema pierda tiempo combinando hechos aleatorios que no tienen que ver con la consulta actual.
    
- **Resolución SLD (Selective Linear Definite clause resolution):** Este es el método más importante para tu investigación, ya que es el algoritmo que utilizan lenguajes como Prolog internamente.
    
    - Es una variante altamente optimizada de la resolución lineal.        
    - Solo funciona con un tipo específico de sentencias lógicas llamadas **Cláusulas de Horn**.        
    - Su nombre indica cómo opera: **S**elecciona un literal objetivo específico a resolver, de manera **L**ineal (usa siempre el resultado del paso anterior), operando sobre cláusulas **D**efinitivas (Cláusulas de Horn).

