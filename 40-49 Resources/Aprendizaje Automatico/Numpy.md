Tags: [[Aprendizaje Automático]] [[Python]]
- NumPy arrays are used to store large amounts of numbers.
- An index is an element’s position in an array. NumPy arrays are 0-indexed.
- Slicing is where we can access parts of a sequence with `name[start:end]`.
- 2D arrays have 1D arrays as elements.

# import
``` python
import numpy as np
```

%% los tipos de datos que inician con 'u' son números sin signo
	'ubyte', 'ufunc', 'uint', 'uint16', 'uint32', 'uint64', 'uint8', 'uintc', 'uintp', 'ulong', 'ulonglong',
%%
## NumPy Array
An **array** is the core data structure of the NumPy package. It’s a grid of values.

``` python
rent = [1500, 1500, 1500, 1500, 1750, 1750]

rent = np.array([1500, 1500, 1500, 1500, 1750, 1750])

# tambien se puede inicializar con tuplas
d1 = np.array((10,15,20,25))

arr = no.array( , , ,order='c')# c Ordena en columnas - f en filas 
arr = no.array( , , ,dtype=np.float32)# define el tipo de dato
#  np.float32 np.f32
np.float32
# 
```

La base de cualquier arreglo es `ndarray`

### Inicializar array con ceros o unos
``` python
ceros = np.zeros((3,3), dtype= "uint8")
# [[0 0 0] 
#  [0 0 0] 
#  [0 0 0]]

unos = np.ones((3,3,2), dtype="float32")

```
## Indexing
In Python lists, we access individual items using the bracket notation. In NumPy arrays, we can access individual elements the same way!

The following array contains the coffee intake in a work week.
``` python
coffee = np.array([3, 2, 1, 0, 1])
```
- The element at index 0 is `3`.
- The element at index 1 is `2`.
- The element at index 2 is `1`.
- The element at index 3 is `0`.
- The element at index 4 is `1`.
To output each of the elements, we can use the `name[index]` syntax:
``` python 
print(coffee[0])   # Output: 3
print(coffee[1])   # Output: 2
print(coffee[2])   # Output: 1
print(coffee[3])   # Output: 0
print(coffee[4])   # Output: 1
```

## Slicing

Same thing with slicing! We can slice NumPy arrays the same way as Python lists.

Slicing is where we can access certain parts of a sequence. We can get multiple elements by specifying where to start slicing and where to end like `name[start : end]`.

``` python
coffee = np.array([3, 2, 1, 0, 1])

# name[start:end]
print(coffee[0:2])    # Output: [3 2]
print(coffee[2:])     # Output: [1 0 1]
print(coffee[-2:])    # Output: [0 1]
```
It starts from the `start` index (inclusive) and ends before the `end` index (non-inclusive).

## 2D Arrays
So far in this course, we’ve been only working with 1D (1-dimensional) arrays:
``` python
arr = np.array([1, 2, 3, 4, 5, 6])
```
We can also write the same 2D array in a grid format (easier for the eyes):
``` python
arr = np.array([
  [1, 2, 3], 
  [4, 5, 6],
  [7, 8, 9]
])
```
- The element at index 0 is `[1, 2, 3]`.
- The element at index 1 is `[4, 5, 6]`.
- The element at index 2 is `[7, 8, 9]`.
To output each of the elements:

```python
print(arr[0])     # Output: [1, 2, 3]
print(arr[1])     # Output: [4, 5, 6]
print(arr[2])     # Output: [7, 8, 9]
```

We can also be more specific with `arr[row][column]`. For example:

``` python
print(arr[0][0])  # Output: 1
print(arr[0][2])  # Output: 3
print(arr[2][2])  # Output: 9
```
# Operators
**basic operators:**
- `+` Addition
- `-` Subtraction
- `*` Multiplication
- `/` Division
- `%` Modulo (returns the remainder)

Suppose we have an array of food order prices and there’s a 20% discount. And we want to update every element with the discount:

``` python
import numpy as np

order = np.array([12.99, 9.99, 4.99, 12.99])

print(order * 0.8)   # Output: [10.39 7.99 3.99 10.39]
```


# NumPy Functions
NumPy also comes with a bunch of math functions ([full list here](https://numpy.org/doc/stable/reference/routines.math.html)).

Here are some of the common ones:
- `.min()` Return the minimum value of an array.
- `.max()` Return the maximum value of an array.
- `.sum()` Return the total sum of an array's values.
- `.average()` Return the average value of an array.

This is what they look like in practice:

``` python
temperatures = np.array([[50, 51, 54, 59, 59, 53, 54, 51],
                         [45, 50, 38, 44, 40, 46, 43, 39]])

print(np.min(temperatures))       # Output: 38
print(np.max(temperatures))       # Output: 59
print(np.sum(temperatures))       # Output: 776
print(np.average(temperatures))   # Output: 48.5
```

## Axis
By default, these math operations apply to the array as though it were a list of numbers. However, by specifying the `axis` parameter, we can apply an operation along the specified axis of an array:
``` python
temperatures = np.array([[50, 51, 54, 59, 59, 53, 54, 51],
                         [45, 50, 38, 44, 40, 46, 43, 39]])

np.sum(temperatures, axis=0)   # Sum of each column
np.min(temperatures, axis=1)   # Min of each row
```
- `axis=0`: each column
- `axis=1`: each row

![[Pasted image 20260219174948.png]]

## .shape
NumPy arrays have a property called `.shape` that returns a tuple containing number of elements each dimension has.

``` python
arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8]]) 

print(arr.shape)     # Output: (2, 4)
```

When we print `arr.shape`, we get `(4, 3)` because there are two dimensions:

- The 1st dimension has `4` elements (for the rows).
- The 2nd dimension has `3` elements (for the columns).

## .reshape()
If we want to change the shape of an array, we use the `.reshape()` function.

Suppose we want to convert the following 1D array into a 2D one:
``` python
arr = np.array([1, 2, 3, 4, 5, 6, 7, 8]) 
new_arr = arr.reshape(2, 4)

print(new_arr)

# Output:
# [[1 2 3 4]
# [5 6 7 8]]
```

Here we are turning the `arr` array into two dimensions:

- The 1st dimension has `2` rows.
- The 2nd dimension has `4` columns.
  
## .arange()
In Python, we have the built-in `.range()` function that we use in a `for` loop. Well, NumPy has something that looks similar called the `.arange()` function.

The `.arange()` function, short for “array range”, is a function that creates an array with evenly spaced values.

``` python
arr = np.arange(5)

print(arr)    # Output: [0 1 2 3 4]
```

You can go further with its three parameters:
- `start` is the first value in the array.
- `stop` is end of the range.
- `step` is step size of the intervals.

``` python
arr = np.arange(start=1, stop=10, step=3)

print(arr)   # Output: [1 4 7]
```
- We start with the value 1.
- We stop at the value 10.
- We go up 3 each time.


### Más Métodos
```python
d1 = np.array((10,15,20,25))

print(d1)       # Output: [10 15 20 25]

print(type(d1)) # Output:       - <class 'numpy.ndarray'>

print(d1.ndim)  # Output: 1     - numero de dimenciones

print(d1.shape) # Output: (4,)  - Estructura del arreglo

print(d1.size)  # Output:4      - Cantidad de elementos

print(d1.dtype) # Output: int64 - tipo de dato

print(d0.itemsize)#             - numero de bytes en que se almacenta
```

``` python
d2 = np.array([[2,4,6],[8,10,12],[14,16,18]])

print(d2)
print(type(d2))
print(d2.ndim)
print(d2.shape)
print(d2.size)
print(d2.dtype)
## Output
# [[ 2 4 6] 
# [ 8 10 12]
# [14 16 18]] 
# <class 'numpy.ndarray'> 
# 2 
# (3, 3) 
# 9 
# int64


# llena el array con 5.8 
otra = np.full((10), 5.8, dtype="float32")

# llena el array con numeros del 1 al 19
otro2 = np.arange(1, 11, 1)

# divide entre 10 cada numero del rango 0-3
otro3 = np.linspace(0, 3, 10) 


# Print out the mean of np_height_in
print(np.mean(np_height_in))
  
# Print out the median of np_height_in
print(np.median(np_height_in))
```


