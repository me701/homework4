# ME 701 - HW 4

Instructions:  Your solutions to the following should be contained in
one file named `hw4.py`.  Include a separate unit-test
file named `test_hw4.py` that you use to develop these functions.
Note, you can choose to define your solutions in separate files, and then
in `hw4.py` you can write something like 

```
from hw4_problem_1 import problem_1
from hw4_problem_2 import problem_2
# and so on
```


## Problem 1 

Write a function named `problem_1` that uses 
numerical integration to evaluate

$$
   \int^{b}_{a} g(x) dx \, ,
$$

where `a` and `b` and `g` are the function arguments.  Here, `a` should be 
less than `b`, and `g` should be a callable function.  Example use:

```
In  [1] problem_1(0.0, 2.0, lambda x: x)
Out [1] 2.0
```



## Problem 2

Consider our favorite matrix of 2's and -1's down the three central
diagonals, which can be defined for arbitrary size `n` with

```python
def make_matrix(n):
    A = np.zeros((n, n))
    for i in range(1, n-1):
        A[i, i] = 2; A[i, i-1] = -1; A[i, i+1] = -1;
    A[0, 0] = 2; A[0, 1] = -1;
    A[-1, -1] = 2; A[-1, -2] = -1;
    return A
```

So, for some `n` we have

```
A = make_matrix(n)
```

We can easily turn that into a compressed, sparse row (CSR) matrix as follows:

```
A_sparse = sp.sparse.csr_matrix(A)
```

Now, let `b = np.ones(n)`.  Use the following 3 methods 
to solve $\mathbf{Ax}=\mathbf{b}$:

  1.  Gaussian elimination via `np.solve` using `A`
  2.  Gaussian elimination via `sp.sparse.linalg.spsolve` using `A_sparse`
  3.  GMRES via `sp.sparse.linalge.gmres`
  
Your solution will be in a function called `problem_2` for which the single
argument is `n`.  Your function will return an estimate for the amount of 
time it takes each method to solve the system for a given value of `n`.
In other words, you are returning three `float` values.


## Problem 3

Use any method you like to fit the following linear model 
to measured atomic masses:

$$
  E_b = a_V A - a_S A^{2/3} - a_C \frac{Z(Z-1)}{A^{1/3}} - a_A \frac{(A-2Z)^2}{A} + \delta(N, Z)$
$$

where 

$$
\delta(N, Z) = 
  {\begin{cases} 
    +a _{\delta}& Z, N{\text{ even }}(A{\text{ even}}) \\ 
    0           & A{\text{ odd}}\\
    -a_{-\delta}& Z,N{\text{ odd }}(A{\text{ even}})\end{cases}}

$$

and 

$m = Zm_p + N m_n - \frac{E^{\text{measured}}_b}{c^2}$.  

Here, $m$ is the mass of a nuclide with mass number $A = Z+N$ with $Z$ protons and $N$ neutrons.
The binding energy $E_b$ (in MeV) tells us how strongly a nucleus is bound.

The unknown coefficients $a_V$, $a_S$, $a_C$, $a_A$, and $a_{\delta}$ are
yours to define.  

The file `atomic_masses_formatted.txt` provides three columns of data.
The first two are $Z$ and $A$.  The third is the corresponding mass in 
atomic mass units.  The proton mass is $m_p = 1.007276466621$ u while 
the neutron mass is $m_n = 1.00866491588$ u.  Note that 
1 u is equal to $931.49410242$ MeV/c$^2$.

With this data, you have 
everything required to define and solve the problem.  Your `problem_3`
function should return the coefficients in the order in which they appear 
in the formula above.  Use [Wikipedia](https://en.wikipedia.org/wiki/Semi-empirical_mass_formula)
for a sanity check on your numbers.


## Problem 4

Go find any ordinary differential equation that still haunts you from MATH 340
and solve it numerically using `odeint`.  In your function `docstring` 
make sure to tell me how you feel to conquer it.  Your function 
`problem_4` should return two arrays `x` and `y` that represent the 
independent and dependent variable of your equation.



