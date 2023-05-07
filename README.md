Download Link: https://assignmentchef.com/product/solved-math565-homework-4
<br>
1.   (Fixed point algorithm.) Consider the fixed-point iteration

xk+1 = g(xk).

applied to solving the problem g(x) = x for a given g(x).

(a)    Show analytically that for g(x) = ax+b, |a| &lt; 1, the fixed point iteration converges to the solution x = b/(1 − a).

(b)    Show that for any fixed point problem, the error ek+1 ≡ xk − x satisfies ek+1 = ake0.

(c)    The result in the Problem 1b is not very useful, since we don’t know the initial error. Show thatwe can approximate the error using

Hint: Start with ek+1 = xk+1−x. Add and subtract xk to the right hand side to get an expression involving ek. Then use the fact that ek+1 = aek to solve for ek+1.

(d)   Show that for the linear problem g(x) = ax+b, the error estimate in Problem 1c is exactly equal to the true error you found in Problem 1b.

(e)   How many iterations does the fixed point algorithm require to solve  to a tolerance of 10−8? For this problem, you do not need to code anything. Just use the fact that you know e0.

2.   (Steffensen’s Method) From Problem 1, you might conclude that the fixed point method isn’t very useful if it takes so many iterations to solve a simple linear problem. Steffensen’s Method, given by

(1)

improves on the fixed point algorithm by solving the linear problem in one step.

(a)   Show analytically that for any g(x), the iteration used in Steffensen’s Method satisfies

where x satisfies g(x) = x.

(b)   Show analytically that Steffensen’s iteration converges in one step for the fixed point problemg(x) = ax + b = x, for |a| &lt; 1.

(c)    Code Steffensen’s Method and solve the fixed point problem . Show that you get convergence in one step. Compare this to the number of iterations required in Problem 1d.

(d)   Use Steffensen’s method to accelerate the convergence of a fixed-point algorithm used to solve the√

root-finding problem f(x) = x3 +x2 −3x−3. Use the function g(x) = 3 3 + 3x − x2. See lecture notes on the fixed-point iteration for a suitable starting guess. Use a tolerance of 10−8.

• Create a loglog plot showing the error en+1 verses en for both the fixed-point method and the accelerated fixed-point method (Steffensen’s algorithm). Compute the slope of each plot and show that the fixed-point algorithm is linearly convergent, whereas Steffensen’s method is quadratically convergent.

Note: In Homework #3 (Problem 3), we showed that for a superlinear scheme, the error can be approximated as

|ek+1| = |xk+1 − x| ≈ |xk+1 − xk|

3.   (LU Decomposition). In class, we used ”elementary matrices” to derive the LU decomposition. An example of a 4 × 4 elementary matrix is

(2)

where `21 is a multiplier computed during the elimination process.

Consider the matrix

(3)

(a)   Show that

(b)   Choose multipliers `1j so that applying applying E41E31E21 to A zeros out the entries below a11.

(c)    Show that the inverse of E41E31E21 is

Hint : Use the formula B−1 = CT/det(B) where C is the co-factor matrix of B.

(d)   From the above steps, derive the LU decomposition of a general 4×4 matrix. Use these to derive the LU decomposition for a general 4 × 4 matrix.

(e)   Find the LU decomposition of the matrix in (3).

4.   (Partial Pivoting) The basic LU decomposition algorithm may fail if it hits a zero pivot, or can lead to significant errors for very small pivots.

(a)   The code lu bug pp.m on the course website implements the partial pivoting algorithm. Find the three bugs in the code to implement partial pivoting correctly.

(b)   The code lu  solve.m on the course website carries out forward and backward substitutions needed to solve Ax = b using LU decomposition. Modify this to use L and U obtained from the partial pivoting algorithm.

(c)    Solve the linear system Ax = b for A and b given by

b

using LU decomposition both without and with partial pivoting. Compute the true solution and use this to compute the errors using the LU decomposition both without and with partial pivoting. Show that the results using partial pivoting are significantly smaller than the errors obtained without partial pivoting.

(d)   (Math 565). At what step in the LU decomposition process without partial pivoting do errors (due to catastrophic cancellation) enter the calculations?

5.   (Jacobi Method). Assume that the following 2 × 2 matrix A is strictly diagonally dominant.

.

(a)   Show that ρ(I − D−1A) &lt; 1. From this conclude that the Jacobi iteration will converge.

6.   (Gauss-Seidel Method). Write a code that implements the Gauss-Seidel method to solve a 4 × 4 matrix equation Ax = b for a symmetric positive definite matrix A and right hand side vector b of your choice.

(a)   Solve the system to a tolerance of 10−8. Report on the number of iterations required to solve your system, as well as the final solution.

To generate your matrix A, use the rand function in Matlab (or the equivalent in Python) to create a matrix B with random entries. Then set A = BTB. Show that A is symmetric positive definite. Hint: Show that xTAx &gt; 0 for any vector x.

7.   (Math 565). The iteration step in a general stationery iterative method for solving the linear system Ax = b can be written as

xk+1 = (I − M−1A)xk + M−1b

(a)   Show that if M = A, the iteration converges in one step.

(b)    Show that Aek = −rk, where rk = b − Axk, ek = xk − x, and x solves Ax = b exactly. (c) Show that the iteration for the error ek is given by

ek+1 = (I − M−1A)ek

(d) Show that

kekk ≤ kI − M−1Akkke0k

where k · k is a matrix norm. Hint: Use the following properties of matrix norms:

i.     kABk≤kAkkBk for matrices A and B.

ii.   kAxk≤kAkkxk for matrix A and vector x.

(e)   Show that we can estimate the number of iterations needed for a stationery iterative method toachieve a desired error tolerance ε using the formula

.

Figure 1: Plot of iterations required by a Gauss-Seidel method for random, 4 × 4 SPD matrices.

(f)    The plot in Figure 7 shows the number of iterations required to solve a series of 4×4 symmetric positive definite systems using the Gauss-Seidel method. From the plot, you see that generally, the number of actual iterations required increases as the spectral radius of the matrix I −M−1A approaches 1. But the estimated number of iterations seems to underestimate the actual number for many larger values of ρ(I − M−1A). What is the reason for this?

8.   (Math 565). The conjugate gradient algorithm improves on the Steepest Descent Algorithm by choosing A-conjugate directions rather than just orthogonal directions.

(a)   Show analytically that the update to the residual rk+1 in the Conjugate Gradient algorithm is equal to b − Axk.

(b)   Show that the directions pk satisfy p              = 0. That is, the directions are A-conjugate.

(c)    Code the conjugate gradient algorithm and use it to solve a 100 × 100 linear positive definite system Ax = b. Construct A and b using random entries.

(d)   Compare the number of iterations needed using CG to the number required by Gauss-Seidel.