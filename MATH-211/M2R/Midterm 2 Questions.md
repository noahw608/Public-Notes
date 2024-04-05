# Midterm 2 Review
## Topics
- [Homogeneous Differential Equations](#homogeneous-differential-equations)
- [Non-homogeneous Differential Equations](#nonhomogeneous-differential-equations)
- [Complexification](#complexification)
- [Laplace Transforms](#laplace-transforms)
- [Laplace IVP's](#laplace-ivps)
- [Step Functions](#step-functions)
- [Convolution](convolution)
---
# Homogeneous Differential Equations
Reminders:
- Homogenous DEQ's are always equal to zero
- A DEQ's characteristic equation allows its roots to be found which can then be plugged into its general equation
- There are three types of solutions to a Homogenous DEQ:
	- Linear - If a solution is linear such as $\lambda=2$ then the solution takes the form $c_1e^{\lambda{}t}$
	- Complex - If a solution is complex such as $\lambda=a\pm{}bi$ then the solution takes the form $e^{at}(c_1\cos{bt}+\sin{bt})$
	- Repeated - If a solution is repeated such as $\lambda=2, \lambda=2$ then then a $t$ is added for each subsequent repeated root giving the form $c_1e^{\lambda{}t}+c_2te^{\lambda{}t}$

Examples:
- Solve: $y''-y=0, y(0)=1, y'(0)=0$

- Solve: $y''+5y=0,y(0)=1,y'(0)=1$

- Solve: $y''+6y'+9y=0,y(0)=0,y'(0)=0$

# Nonhomogeneous Differential Equations
Reminders:
- A non-homogenous DE is not equal to zero
- For the side that does not have a characteristic equation you must make a "guess"
- If this guess does not work on the first try, then you may need to use the **method of undetermined coefficients** by adding a $t$ to your guess

Examples:
- $y'' - 2y' - 3y = 3 e^{2t}, y(0) = 1,  y'(0) = 0$

- $y'' + 16y = 2 \sin {2t},  y(0) = 1,  y'(0) = 0$

- $y'' - y' - 2y = 4x^2,  y(0) = -1,  y'(0) = 1$

- It may be good to also look at a problem where the method of undetermined coefficients must be used

# Complexification
Reminders:
- When the left side of a DEQ takes the form of a $\sin$ or $\cos$ function, instead of making a usual guess you can use a complex number guess.
- The definition $e^{ait}=\cos{at}+i\sin{at}$ can be used to create your complex guess

Examples:
- Find the  of $x''+6x'+5x=\sin{2t}$ using complexification
	
- Find the  of $u''+4u'+20u=−\cos{5t}$ using complexification

# Laplace Transforms
Reminders:
- A Laplace transform simplifies a function by changing its number system. This can help us solve differential equations.
- The laplace transform is denoted as: $F(s)=\mathscr{L}\left(f(t)\right)$
- The general definition of the laplace transform is: $\mathscr{L}\left(f(t)\right)=\int_{0}^{\infty}e^{-st}f(t)dt$ and can be used to find any transform the "long way" (might be required on the test)
- A chart of know Laplace transforms is given and is as follows:

|$f(t)=\mathscr{L}^{-1}(F(s))$|$F(s)=\mathscr{L}(f(t))$|
|-|-|
| $1$ | $\frac{1}{s}\quad{}(s>0)$ |
| $e^{at}$ | $\frac{1}{s-a}\quad{}(s>a)$ |
| $t^{n}\quad{}\text{(n is a positive integer)}$ | $\frac{n!}{s^{n+1}}\quad{}(s>0)$ |
| $t^{a}\quad{}(a>-1)$ | $\frac{\Gamma(a + 1)}{s^{a + 1}}\quad{}(s \gt 0)$ |
| $\sin at$ | $\frac{a}{(s^2 + a^2)}\quad{}(s\gt0)$ |
| $\cos at$ | $\frac{s}{(s^2 + a^2)}\quad{}(s\gt0)$ |
| $\sinh at$ | $\frac{a}{(s^2 - a^2)}\quad{}(s \gt \left\|a\right\|)$ |
| $\cosh at$ | $\frac{s}{(s^2 - a^2)}\quad{}(s \gt \left\|a\right\|)$ |
| $e^{at} \sin bt$ | $\frac{b}{(s-a)^2 + b^2}\quad{}(s \gt a)$ |
| $e^{at} \cos bt$ | $\frac{s-a}{(s-a)^2 + b^2}\quad{}(s \gt a)$ |
| $t^n e^{at}\quad{}(\text{n is a positive integer)}$ | $\frac{n!}{(s - a)^{n + 1}}\quad(s \gt a)$ |
| $u_c(t)$ | $\frac{e^{-cs}}{s}\quad(s \gt 0)$ |
| $u_c(t) f(t - c)$ | $e^{-cs} F(s)$ |
| $e^{ct} f(t)$ | $F(s - c)$ |
| $f(ct)$ | $(\frac{1}{c}) F(\frac{s}{c})\quad(c \gt 0)$ |
| $\delta(t - c) = \delta_c(t)$ | $e^{-cs}$ |
| $f'(t)$ | $s F(s) - f(0)$ |
| $f''(t)$ | $s^2 F(s) - sf(0) - f'(0)$ |

Examples:
- Using the definition of the Laplace transform, find the laplace transform of $f(t)=\sin{t}$
	
- Using the Laplace table, find the Laplace transform of $f(t)=e^{6t}\sin{8t}$
	
- Using the Laplace table, find the Inverse Laplace transform of $F(s)=\frac{4}{s^2+64}$
	

# Laplace IVP's
Reminders: 
- The goal of solving initial value problems using Laplace Transforms is to convert a DEQ into the laplace system and then convert it back into standard form. 
- To solve initial value problems using Laplace Transforms you need to use the definitions of derivatives: 
	- $y'=Y(t)s-y(0)$ and $y''=Y(t)s^2-y(0)s-y'(0)$
- Often **Partial Fraction Decomposition** is needed to perform the inverse laplace.
- Any DEQ can be solved using Laplace Transforms, its just a matter of how complex it becomes.

Examples:
- Solve the following IVP using laplace transforms: $y''+16y=2\sin{2t},y(0)=1,y'(0)=0$

# Step Function
Reminders:
- A stenctio alloise functions to have a laplace transform performed on them
- Step functions can be applied to other functions, causing their behavior to change
- A ste nctin $(t)$ can also be called a heaviside function and take the form $h(t-c)$

Examples:
- Q2: Find the laplace transform of $f(t)=\begin{cases}
0 & \text{if } t<6\\
9t & \text{if }t\geq{}6
\end{cases}$
- Q3: Find the laplace transform of $f(t)=\begin{cases}
0 & \text{if } t<6\\
(t-6)^3 & \text{if }t\geq{}6
\end{cases}$

- Q5: Find the inverse laplace transform of $F(s)=\frac{e^{-8s}}{s^2+s-6}$

# Convolution
Reminders:
- Convolution is an operation that is sometimes useful when dealing with laplace functions
- The definition of a convolution is the following: 
$f (t)\ast g(t)=\int_{0}^{t} f(\tau) g(t-\tau) d \tau$
- Lets simplify that definition into steps:
	-  you first turn the first function into Tau's ($\tau$) and the second function into t-Tau's ($t-\tau$) by replacing the t's in the function with the respective new term
	- Then you take the integral of the two new functions multiplied together with respect to tau from 0 to t. 
	- This will provide you with one new function in terms of t.
- The most useful application of a convolution is as an alternative to PFD
- If you have a Laplace Function such as $\frac{s+1}{s^2(s-2)}$ and need to inverse laplace it, instead of applying partial fractions, you can use a convolution definition:
	- $=\mathscr{L}^{-1}\left(\frac{s+1}{s^2}\right)\ast{}\mathscr{L}^{-1}\left(\frac{s+1}{s-2}\right)$
	- Breaking down this definition, you first take the inverse Laplace of each piece, and the convolve the results together. 
	- This will give you an original function in terms of t

Examples:
- If $f(t)=t$ and $g(t)=t$ find $f\ast{}g$

- Find the Inverse Laplace of $\frac{1}{(s-1)(s-3)}$ using convolution
- Solve the IVP: $y''+16y=g(t),y(0)=1,y'(0)=0$

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMyOTg1MzEwLDkzNzU4NDczOCwtOTgyMD
E0NDI3LC0xOTg5NDIyMDkxLC05MzA3ODgyNjAsMTI5NTIwNzcx
MF19
-->