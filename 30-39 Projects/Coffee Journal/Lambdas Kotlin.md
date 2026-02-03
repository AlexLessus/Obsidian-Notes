Tags: [[Kotlin]] 
- Las lambdas permiten definir variables o funciones que pueden interactuar con otras funciones.

---
Ejemplo
```
...
	val mySumFun = fun (x: Int, Y: Int): Int = x + y
	val myMultFun = fun (x: Int, Y: Int): Int = x * y
	
	print(myOperateFun(5, 10, mySumFun))
	print(myOperateFun(5, 10, myMultFun))
	

}

// Funcion que toma dos valores y una funcion, retorna el resultado de la función 
private fun myOperateFun(x: Int, y: Int, myFun: (Int, Int) -> Int): Int){
	return myFun(x, y)
}


```
