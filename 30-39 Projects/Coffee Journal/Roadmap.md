
1) start form your goal:
	1) Why am i making this project ?
	2) Who this project is for ?
	3) What is going to make it valuable ?
	- Write them down and think on them not just surface level problems
2) Write down what the users must be able to do with the  project 
	1) features
	2) guardrails
	3) don't overthink with tech stack etc only what features that is needed 
	4) user centric approach
3) Define the data models
	1) don't think about the databases
	2) think about the data what you need and how you want to handle it
	3) draw the relationships
4) Nail an MVP
	1) Look back on all the features above and strip it to the barebones and what is needed to make it function : absolute minimum version
5) Wireframe the project for the most basic user 
	1) think more about UX than UI
	2) paper is cheap but code is expensive
6) Understand the future of the project:
	1) Do you plan to add more features in the future
	2) Do you plan to work on this for months or just a few days ?
		1) don't over or under engineer
7) How is you project going to be presented 
	1) is it a script or a mobile app or a website or a extension
	2) understand how the users will be interacting and base your architecture on that
8) Tech Stack :
	1) Use the points above to choose the tech stack
	2) don't let the tech stack define the project 
	3) best tool for the project not the other way round
	4) Can you deploy this ?
		1) is the tech stack you are choosing viable for deployment and easy to do so so that you don't spend your time more deploying that building
9) The development process
	1) Bare bones
		1) Folder structure
		2) naming conventions
		3) dev environments
		4) version control
	2) setting up the database and creating the data models
	3) backend routes :
		1) API endpoints
		2) test them
	4) Frontend
	5) Project integration and version
	6) CI/CD
	7) test at all steps

# Goal
* Why am I making this project?
	* I want a way to make everyone to get their own perfect cup of coffee and method 
* Who is this project for?
	* People who are starting in the world of coffee and people with a lot of experience and need a way to keep track of their brews
* What is gonna make it valuable
	* It will help you to have real data about the brews and will let you identify the brews that you actually enjoy and how to replicate those cups

# User stories
* Calculate coffee ratios
* Create a note-journal where they can register: 
	* Coffee beans variables
	* Grind variables
	* Water variables
	* Brew variables
	* Flavour
* 


# Data models
* Coffee log model
[[Room (Database)]]


# MVP
### 1. La Calculadora Reactiva (El "Gancho")
Esta es la pantalla principal. Debe funcionar sin internet y ser inmediata.
- **Sliders vinculados:** 3 controles (Café, Agua, Ratio). Si mueves uno, los otros se recalculan matemáticamente en tiempo real.    
- **Selector de Unidades Básico:** Gramos (g) y Mililitros (ml). (Ignora onzas por ahora).
    - **Botón "Comenzar/Guardar":** Un botón flotante (FAB) que diga "Log Brew" (Registrar preparación). Al darle click, te lleva al formulario de registro llevándose los datos calculados (para que el usuario no tenga que volver a escribirlos).    

### 2. Formulario de Registro (El "Input")
Aquí implementas tu idea del "Modo Avanzado".
- **Datos Básicos (Siempre visibles):** Nombre del Grano, Método (Dropdown: V60, Prensa, etc.), Rating (5 estrellas).    
- **Switch "Modo Barista" (Tu función avanzada):** Un toggle que, al activarse, despliega una sección oculta (usando `AnimatedVisibility` en Compose).
    - _Campos del MVP en avanzado:_ Solo incluye los 3 más importantes para empezar: **Temperatura**, **Molienda (Clicks)** y **Tiempo Total**. (Deja los sliders de sabor y retención para la v1.1).
- **Validación:** Que no deje guardar si no hay nombre de grano.

### 3. Historial de "Mis Cafés" (El "Output")
- **Lista Cronológica (`LazyColumn`):** Tarjetas simples ordenadas de la más reciente a la más antigua.
- **La Tarjeta (Card):** Debe mostrar solo lo vital: Nombre del grano, Método, Fecha (ej. "Hoy") y las Estrellas.
- **Acción de Borrar:** Deslizar a la izquierda para eliminar (Swipe to dismiss). Es una función nativa de Compose muy vistosa y fácil de implementar.

### 4. Detalle de la Preparación
- Al tocar una tarjeta del historial, se abre una pantalla de "Detalle".
- Aquí muestras **toda** la información (incluyendo los datos avanzados si los hubo).
- _Objetivo:_ Que el usuario pueda ver qué hizo la última vez para repetirlo.


# Sketch


# Mobile app 
Android native 
Kotlin
* Front: Jetpack Compose
* Backend: Room (Local storage)

# Overall Dev Process
### FASE 0: Configuración y Cimientos (1-2 días)
_El objetivo es tener el entorno listo antes de escribir lógica._
1. **Creación del Proyecto:**    [
    - Android Studio > New Project > "Empty Activity" (Asegúrate de que tenga el logo de Jetpack Compose).        
    - Lenguaje: Kotlin.        
    - Build Configuration Language: Kotlin DSL.        
2. **Inyección de Dependencias (Gradle):**    
    - Agrega las librerías al `libs.versions.toml` y `build.gradle`:        
        - **Room:** (Para la base de datos).            
        - **Navigation Compose:** (Para moverte entre pantallas).            
        - **ViewModel & Lifecycle:** (Para la gestión de estado).            
        - **KSP:** (El procesador de anotaciones moderno para Kotlin).            
3. **Estructura de Carpetas (Package Structure):** Crea estos paquetes vacíos dentro de `com.tu_nombre.brewtrack`:    
    - `data` (Aquí vivirá Room).        
    - `model` (Tus clases de datos).        
    - `ui` (Tus pantallas).        
        - `ui/theme` (Colores y tipografía).            
        - `ui/calculator`            
        - `ui/history`            
        - `ui/addlog`

---

### FASE 1: La Capa de Datos (Backend Local) (2-3 días)
_Construimos la "memoria" de la app. Sin esto, la UI no tiene qué mostrar._
4. **Modelo de Datos (Entity):**    
    - Crea la `data class CoffeeLog` en la carpeta `model`.        
    - Añade la anotación `@Entity` de Room.        
    - Define los campos (incluyendo los nulos para el modo avanzado).        
5. **El DAO (Data Access Object):**    
    - Crea la interfaz `CoffeeDao`.        
    - Escribe los métodos: `@Insert`, `@Query("SELECT * FROM...")`, `@Delete`.        
6. **La Base de Datos:**    
    - Crea la clase abstracta `AppDatabase` que hereda de `RoomDatabase`.        
7. **El Repositorio (Repository Pattern):**    
    - _Crucial:_ Crea una clase `CoffeeRepository`.        
    - Esta clase será la única que hable con el DAO. El ViewModel le pedirá datos al Repositorio, no al DAO directamente. Esto es "Clean Architecture".        

---

### FASE 2: Feature - Calculadora (2-3 días)
_La primera funcionalidad visible. Es pura lógica y estado._
8. **Calculator ViewModel:**    
    - Crea `CalculatorViewModel`.        
    - Define variables de estado (`StateFlow` o `MutableState`): `waterAmount`, `coffeeAmount`, `ratio`.        
    - Implementa la lógica matemática: Cuando cambia `ratio`, recalcula `water`.        
9. **UI de Calculadora:**    
    - Diseña la pantalla usando `Column`, `Slider` y `Text`.        
    - Conéctala al ViewModel: Los Sliders deben leer y modificar los valores del ViewModel.        

---

### FASE 3: Feature - Guardado y Formulario (3-4 días)
_El corazón de la app. Aquí unes la calculadora con la base de datos._

10. **Navegación:**    
    - Configura el `NavHost`.        
    - Define las rutas: `"home"`, `"add_log"`, `"history"`.        
    - Haz que el botón "Log Brew" de la calculadora navegue a `"add_log"`. _Reto:_ Pasa los valores calculados (gramos/agua) como argumentos de navegación.       
11. **Log ViewModel:**    [[View model]]
    - Crea un ViewModel que pueda llamar a `repository.insertLog()`.        
12. **UI del Formulario:**    
    - Crea los campos de texto (`OutlinedTextField`).        
    - Implementa el **Switch "Advanced Mode"**:        
        - Usa `var showAdvanced by remember { mutableStateOf(false) }`.            
        - Envuelve los campos extra en un `AnimatedVisibility(visible = showAdvanced)`.   
13. **Conexión:**    
    - Al dar click en "Guardar", llama al ViewModel para insertar en la BD y regresa a la pantalla de inicio.        

---
### FASE 4: Feature - Historial y Visualización (2-3 días)
_Cerrar el ciclo mostrando los datos._
14. **Lectura de Datos:**    
    - En tu ViewModel, expón un `Flow<List<CoffeeLog>>` que venga del repositorio.        
15. **UI de Lista (LazyColumn):**    
    - Crea un Composable `CoffeeLogCard` (el diseño de cada fila).        
    - Usa `LazyColumn` para mostrar la lista que viene del ViewModel.        
    - Usa `collectAsStateWithLifecycle()` para que la lista se actualice sola si agregas algo nuevo.        

---

### FASE 5: Pulido Final (1-2 días)
_Hacer que parezca una app de verdad._
16. **Recursos:**    
    - Cambia el icono de la app (busca uno en Flaticon o diseñalo).        
    - Cambia el nombre en `strings.xml` ("BrewTrack").        
17. **Testing Manual:**    
    - Prueba el "Happy Path": Calcula -> Guarda -> Verifica en lista.        
    - Prueba casos bordes: ¿Qué pasa si dejo el nombre vacío? (Validación). ¿Qué pasa si giro la pantalla?        
18. **Commit Final:**    
    - Asegúrate de haber hecho commits en Git durante todo el proceso (ej: `feat: add calculator logic`, `ui: create history screen`).


[[Lambdas Kotlin]]
[[Kotlin sintaxis]]