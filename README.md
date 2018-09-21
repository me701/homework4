# ME 701 - HW 4

Instructions:  Your solutions to the following should be contained in
one file named `lastname_firstname_hw4.py`.  Include a separate unit-test
file named `test_lastname_firstname_hw4.py`.


## Problem 1 (1 point)


Implement a straightforward Gaussian elimination function in Python.  It
should be a function that I can call via

```
x = gauss_elim(A, b)
```

where `A` is $n\times n$ and `b` is $n\times 1$.   Create a unit test
that shows me your function actually works!  Then

 - Show me the order of your algorithm with evidence
 - Show me how much faster `np.linalg.solve` is as a function of `n`

## Problem 2 (1 point)

Consider a function to compute the product of three matrices: $P = ABC$.  Call
that function `matrix_product(A, B, C)`.  Assume A, B, and C are NumPy arrays.
Implement your function in a way that *minimizes* the cost of the computation.
Note, $A$ is $a \times b$, $B$ is $b \times c$, and $C$ is $c \times d$.
Explain how you devise your solution.  You may (and should) use `@` for the
multiplication operator.  Include unit tests for this function, too.


## Problem 3 (2 point)

Define the same `A` matrix we've used in class (2's and -1's).  Let it be
100 x 100, and let `b` be all ones.  Implement Jacobi (`P` = `D`) and
Gauss-Seidel (`P` = `L+D`) iteration.  Plot the norm of the 
true residual (`A*x-b`) as a function of iteration.  Do the same using
GMRES.  You don't have to use unit tests, but you can (and are always
encouraged to) do so.

## Problem 4 (2 point)

Wide open problem: go find some *interesting* data, propose a model, and
determine any coefficients using any method of your choosing from those
we've investigated.

Feeling unimaginative?  How about: 

  - fitting atomic masses to the semi-empirical mass formula
    (See your NE 495 book or https://en.wikipedia.org/wiki/Semi-empirical_mass_formula)

  - Perform a numerical experiment in which a particle in 1-D land starts at 
    `x = 0` and at every step of its life goes either one to the left or one
    to the right.  It dies after 10000 steps.  Simulate this life for 100+
    particles and determine a model for the net distance traveled from `x = 0`
    as a function of step.

  - Sorry, I'm out of imagination now.




  


