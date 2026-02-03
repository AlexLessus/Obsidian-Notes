Tags: [[Coffee Journal]] [[Kotlin]]

| **Concepto**           | **Java ☕**                                     | **Kotlin 🟣**                     |
| ---------------------- | ---------------------------------------------- | --------------------------------- |
| **Variable Inmutable** | `final String x = "A";`                        | `val x = "A"`                     |
| **Variable Mutable**   | `String x = "A";`                              | `var x = "A"`                     |
| **Nullable**           | `String x = null;` (Peligro)                   | `val x: String? = null`           |
| **Check Null**         | `if (x != null) x.len();`                      | `x?.length`                       |
| **Default value**      | `x != null ? x : "B";`                         | `x ?: "B"`                        |
| **Función**            | `public int sum(int a, int b) { return a+b; }` | `fun sum(a: Int, b: Int) = a + b` |
| **Void**               | `void`                                         | `Unit` (o se omite)               |
| **Constructor**        | `public User(String n) { this.n = n; }`        | `class User(val n: String)`       |
| **POJO**               | 50 líneas de getters/setters/equals            | `data class User(val n: String)`  |
| **Switch**             | `switch(x) { case 1: ... }`                    | `when(x) { 1 -> ... }`            |
| **String Template**    | `String.format("Hola %s", name);`              | `"Hola $name"`                    |
| **Casting**            | `(String) obj`                                 | `obj as String`                   |
| **Safe Casting**       | `(check types...)`                             | `obj as? String` (null si falla)  |
| **Static**             | `public static void main...`                   | `companion object { ... }`        |
| **Instance Check**     | `obj instanceof String`                        | `obj is String`                   |
| **Loops**              | `for (int i : list)`                           | `for (i in list)`                 |
| **Ranges**             | `for (int i=0; i<=10; i++)`                    | `for (i in 0..10)`                |
