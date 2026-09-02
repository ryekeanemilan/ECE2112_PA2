# ECE2112_PA1
Milan, Rye Keane Lorenzo | 2ECE-D

# Problem 1: Reproducible Normalization Problem
Create a reproducible random 5x5 integer ndarray named X. Normalize the complete array  where x̄ is the mean of all 25 elements, and σ is their population standard deviation as returned by NumPy's default std() call. Store the normalized array in X_normalized.   

To approach the problem, it is crucial to make sure that the randomly generated numbers inside the array are going to be the exact same set every time the code runs by setting a specific seed. A 5x5 array is then generated where it has random integers from 10 up to, but not including, 101.

```
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))
```

Next, the built-in NumPy functions are used to easily solve for the average (mean) and the standard deviation of all the numbers inside the array.

```
mean = np.mean(X)
std = np.std(X)
```

Once the values are ready, the normalization formula is applied. By virtue of how NumPy handles math across arrays, subtracting the mean and dividing by the standard deviation is applied to every single element at once. This avoids the need for any loops in the solution. 

```
mean = np.mean(X)
std = np.std(X)
```

The processed array is then saved as an `.npy` file. 

```
np.save('X_normalized.npy', X_normalized)
```
