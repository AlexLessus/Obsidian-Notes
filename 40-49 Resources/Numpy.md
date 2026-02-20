Tags: [[Aprendizaje Automático]] [[Python]]
- NumPy arrays are used to store large amounts of numbers.
- An index is an element’s position in an array. NumPy arrays are 0-indexed.
- Slicing is where we can access parts of a sequence with `name[start:end]`.
- 2D arrays have 1D arrays as elements.

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

