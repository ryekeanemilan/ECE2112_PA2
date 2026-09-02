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
X_normalized = (X-mean)/std
```

The processed array is then saved as an `.npy` file. 

```
np.save('X_normalized.npy', X_normalized)
```

# Problem 2: Cubes Divisible by 4 Problem
Using NumPy, create the first 100 positive integers, cube every element, and reshape the result into a 10x10 ndarray named C. Use a Boolean condition on C to obtain every cubed value divisible by 4 and store the selected values in div_by_4.  

To approach the problem, a sequence of numbers from 1 to 100 must be generated, which was achieved through the use of `np.arange`. To be more efficient in cubing all of the numbers from 1 to 100, a NumPy math function is used to raise the entire set of numbers to the power of 3, after which they were gathered and organized into a 10x10 grid. 

```
C = np.power(np.arange (1,101), 3).reshape(10, 10)
```

To hunt down the cubed numbers that are completely divisible by 4, a modulo operator is used. The modulo operator checks the remainder when a specific number is divided by 4; should the remainder be exactly zero, it would automatically be known that the number is divisible by 4. 

```
np.mod(C, 4) == 0
```

To print out the numbers that have been confirmed to be divisible by 4, a boolean condition is required. However, a boolean condition alone would only print the array where it says true or false, depending on whether the number fulfills the divisible by 4 condition. 
```
div_by_4 = np.mod(C, 4) == 0
```
```
 [[False  True False  True False  True False  True False  True]
 [False  True False  True False  True False  True False  True]
 [False  True False  True False  True False  True False  True]
 [False  True False  True False  True False  True False  True]
 [False  True False  True False  True False  True False  True]
 [False  True False  True False  True False  True False  True]
 [False  True False  True False  True False  True False  True]
 [False  True False  True False  True False  True False  True]
 [False  True False  True False  True False  True False  True]
 [False  True False  True False  True False  True False  True]]
```
To work around this issue, the condition is placed inside the brackets to allow NumPy to act like a filter. It searches the entire array and extracts only the numbers that meet the condition; these numbers are then gathered into a new array.

```
div_by_4 = C[np.mod(C, 4) == 0]
```

```
 [      8      64     216     512    1000    1728    2744    4096    5832
    8000   10648   13824   17576   21952   27000   32768   39304   46656
   54872   64000   74088   85184   97336  110592  125000  140608  157464
  175616  195112  216000  238328  262144  287496  314432  343000  373248
  405224  438976  474552  512000  551368  592704  636056  681472  729000
  778688  830584  884736  941192 1000000]
```

# Problem 3: Above-Mean Squares Problem
Create a 6x6 ndarray named S containing the squares of the first 36 positive integers in increasing row-major order. Compute the mean of all elements of S and store it in S_mean. Then use Boolean filtering to select only the elements strictly greater than S_mean and store these values in above_mean

