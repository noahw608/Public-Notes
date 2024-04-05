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
  
  - The characteristic equation is: $\lambda{}^2-1=0$ giving the roots $\lambda=\pm{}1$
  - The solution takes the form: $y=C_1e^{-t}+C_2e^{t}$
  - To solve the IVP find the derivative: $y'=-C_1e^{-t}+C_2e^{t}$
  - Then plug in the IVP values: $1=C_1+C_2$ and $0=-C_1+C_2$
  - Therefore $C_1=C_2$ and $C_1=C_2=\frac{1}{2}$
  - So the final solution is $y=\frac{1}{2}e^{-t}+\frac{1}{2}e^{t}$

- Solve: $y''+5y=0,y(0)=1,y'(0)=1$
  
  - The characteristic equation is $\lambda{}^2+5=0$ giving the roots $\lambda=0\pm{}i\sqrt{5}$
  - The solution takes the form: $y=C_1\cos{\sqrt{5}t}+C_2\sin{\sqrt{5}t}$
  - To solve the IVP find the derivative: $y=-\sqrt{5}C_1\sin{\sqrt{5}t}+\sqrt{5}C_2\cos{\sqrt{5}t}$
  - Plug in IVP values: $1=C_1$ and $1=C_2\sqrt5$ so $C_2=\frac{1}{\sqrt{5}}$
  - The final solution is $y=\cos{\sqrt{5}t}+\frac{1}{\sqrt{5}}\sin{\sqrt{5}t}$

- Solve: $y''+6y'+9y=0,y(0)=0,y'(0)=0$
  
  - The characteristic equation is $\lambda{}^2+6\lambda{}+9=0$ giving the roots $\lambda=-3,-3$
  - The solution takes the form: $y=C_1e^{-3t}+C_2te^{-3t}$
  - To solve the IVP find the derivative: $y'=-3C_1e^{-3t}+C_2(e^{-3t}+-3te^{-3t})$
  - Plug in IVP values: $0=C_1$ and $0=-3C_1+C_2$ so $C_1=C_2=0$
  - The final solution is $y=0$

# Nonhomogeneous Differential Equations

Reminders:

- A non-homogenous DE is not equal to zero
- For the side that does not have a characteristic equation you must make a "guess"
- If this guess does not work on the first try, then you may need to use the **method of undetermined coefficients** by adding a $t$ to your guess

Examples:

- $y'' - 2y' - 3y = 3 e^{2t}, y(0) = 1,  y'(0) = 0$
  
  - First find the homogenous solution:
  - Characteristic Eq: $\lambda{}^2-2\lambda{}-3$, Roots: $\lambda{}=3,-1$
  - Solution: $y_h=C_1e^{3t}+C_2e^{-t}$
  - Then make your guess: $y_p=Ae^{2t},y'_p=2Ae^{2t},y''_p=4Ae^{2t}$
  - Plug into OGEQ: $4Ae^{2t}-2(2Ae^{2t})-3(Ae^{2t})=3e^{2t}$
  - Simplify: $e^{2t}(4A-4A-3A)=3e^{2t}$
  - Solve for Constant: $-3A=3$ therefore $A=-1$
  - Plug in Constant: $y_p=-e^{2t}$
  - Add $y_h$ and $y_p$: $y=C_1e^{3t}+C_2e^{-t}-e^{2t}$
  - Find the Derivative for IVP: $y'=3C_1e^{3t}-C_2e^{-t}-2e^{2t}$
  - Plug in IVP values: $1=C_1+C_2-1$ and $0=3C_1-C_2-2$
  - Final Solution: $y=e^{3t}+e^{-t}-e^{2t}$

- $y'' + 16y = 2 \sin {2t},  y(0) = 1,  y'(0) = 0$
  
  - First find the homogenous solution:
  - Characteristic Eq: $\lambda{}^2+16$, Roots: $\lambda{}=0\pm{}4i$
  - Solution: $y_h=C_1\cos{4t}+C_2\sin{4t}$
  - Then make your guess: $y_p=a\cos{2t}+b\sin{2t},y'_p=-2a\sin{2t}+2b\cos{t},y''_p=-4a\cos{2t}-4b\sin{2t}$
  - Plug into OGEQ: $-4a\cos{2t}-4b\sin{2t}+16a\cos{2t}+16b\sin{2t}= 2 \sin {2t}$
  - Simplify: $12a\cos{t}=0$ and $12b\sin{t}= 2 \sin {2t}$
  - Simplify Again: $12b= 2$ therefore $B=\frac{1}{6}$ and $a=0$
  - Plug in Constant: $y_p=\frac{1}{6}\sin{2t}$
  - Add $y_h$ and $y_p$: $y=C_1\cos{4t}+C_2\sin{4t}+\frac{1}{6}\sin{2t}$
  - Find the Derivative for IVP: $y'=-4C_1\sin{4t}+4C_2\cos{4t}+\frac{1}{3}\cos{2t}$
  - Plug in IVP values: $1=C_1$ and $0=4C_2+\frac{1}{3}$ so $C_2=-\frac{1}{12}$
  - Final Solution: $y=\cos{4t}-\frac{1}{12}\sin{4t}+\frac{1}{6}\sin{t}$

- $y'' - y' - 2y = 4x^2,  y(0) = -1,  y'(0) = 1$
  
  - First find the homogenous solution:
  - Characteristic Eq: $\lambda{}^2-\lambda{}-2$, Roots: $\lambda{}=2,-1$
  - Solution: $y_h=C_1e^{2t}+C_2e^{-t}$
  - Then make your guess: $y_p=Ax^2+Bx+C,y'_p=2Ax+B,y''_p=2A$
  - Plug into OGEQ: $2A-2Ax-B-2Ax^2-2Bx-2C=4x^2$
  - Simplify: $-2A=4,-2A-2B=0,2A-B-2C=0$
  - Simplify Again: $A=-2,B=2,C=-3$
  - Plug in Constant: $y_p=-2x^2+2x-3$
  - Add $y_h$ and $y_p$: $y=C_1e^{2t}+C_2e^{-t}-2x^2+2x-3$
  - Find the Derivative for IVP: $y'=2C_1e^{2t}-C_2e^{-t}-4x+2$
  - Plug in IVP values: $-1=C_1+C_2-3$ and $1=2C_1-C_2+2$ so $C_1=\frac{1}{3},C_2=\frac{5}{3}$
  - Final Solution: $y=\frac{1}{3}e^{2t}+\frac{5}{3}e^{-t}-2x^2+2x-3$

- It may be good to also look at a problem where the method of undetermined coefficents must be used

# Complexification

Reminders:

- When the left side of a DEQ takes the form of a $\sin$ or $\cos$ function, instead of making a usual guess you can use a complex number guess.
- The definition $e^{ait}=\cos{at}+i\sin{at}$ can be used to create your complex guess

Examples:

- Find the  of $x''+6x'+5x=\sin{2t}$ using complexification
  
  - First we need to determine if we are looking for the real or imaginary solution: $e^{2it}=\cos{2t}+i\sin{2t}$
  - We are looking for the imaginary part of the complex solution since $i\sin{2t}$ matches $\sin{2t}$ from the OGEQ
  - Now we can make our complex guess: 
  - $x_c=Ae^{2it},x'_c=2iAe^{2it},x''_c=-4Ae^{2it}$
  - Now plug the guess in and set it equal to the desired complex solution $(e^{2it})$: 
  - $-4Ae^{2it}+12iAe^{2it}+5Ae^{2it}=e^{2it}$
  - Simplify: $-4A+12iA+5A=1$ therefore $A=\frac{1}{1+12i}$
  - Multiply by conjugate: $A=\frac{1}{1+12i}\cdot{}\frac{1-12i}{1-12i}=\frac{1}{145}-\frac{12}{145}i$
  - Plug into guess: $x_c=\left(\frac{1}{145}-\frac{12}{145}i\right)e^{2it}$
  - Remember that $e^{2it}=\cos{2t}+i\sin{2t}$: 
  - $x_c=\left(\frac{1}{145}-\frac{12}{145}i\right)\cdot{}(\cos{2t}+i\sin{2t})$
  - $x_c=\frac{1}{145}\cos{2t}+\frac{1}{145}i\sin{2t}-\frac{12}{145}i\cos{2t}+\frac{12}{145}\sin{2t}$
  - Remember that we a looking real and complex parts of the general equation and complex equation equal:
  - $x''_r+6x'_r+5x_r=\cos{2}$
  - $x_p=\frac{1}{145}\sin{2t}-\frac{12}{145}\cos{2t}$

- Find the  of $u''+4u'+20u=−\cos{5t}$ using complexification
  
  - Determine if the  is real or imaginary: $-e^{5it}=-\cos{5t}-i\sin{5t}$
  
  - We are looking for the  to this problem
  
  - Make your complex guess: $u_c=Ae^{5it},u'_c=5iAe^{5it},u''_c=-25Ae^{5it}$
  
  - Plug into OGEQ: $-25Ae^{5it}+20iAe^{5it}+20Ae^{5it}=-e^{5it}$
  
  - Simplify: $-25A+20iA+20A=-1$ therefore: $A=\frac{-1}{-5+20i}$
  
  - Multiply by conjugate: $A=\frac{-1}{-5+20i}\cdot{}\frac{-5-20i}{-5-20i}=\frac{5}{425}+\frac{20}{425}i$
  
  - Plug into complex guess: $u_c=\left(\frac{5}{425}+\frac{20}{425}i\right)e^{5it}$
  
  - $u_c=\left(\frac{5}{425}+\frac{20}{425}i\right)\cdot{}(\cos{5t}+i\sin{5t})$
  
  - $u_c=\frac{5}{425}\cos{5t}+\frac{5}{425}i\sin{5t}+\frac{20}{425}i\cos{5t}-\frac{20}{425}\sin{5t}$
  
  - Remember we are looking for the real part of the complex solution:
  
  - $u_p=\frac{5}{425}\cos{5t}\frac{20}{425}\sin{25t}$

# Laplace Transforms

Reminders:

- A Laplace transform simplifies a function by changing its number system. This can help us solve differential equations.
- The laplace transform is denoted as: $F(s)=\mathscr{L}\left(f(t)\right)$
- The general definition of the laplace transform is: $\mathscr{L}\left(f(t)\right)=\int_{0}^{\infty}e^{-st}f(t)dt$ and can be used to find any transform the "long way" (might be required on the test)
- A chart of know Laplace transforms is given and is as follows:

| $f(t)=\mathscr{L}^{-1}(F(s))$                       | $F(s)=\mathscr{L}(f(t))$                               |
| --------------------------------------------------- | ------------------------------------------------------ |
| $1$                                                 | $\frac{1}{s}\quad{}(s>0)$                              |
| $e^{at}$                                            | $\frac{1}{s-a}\quad{}(s>a)$                            |
| $t^{n}\quad{}\text{(n is a positive integer)}$      | $\frac{n!}{s^{n+1}}\quad{}(s>0)$                       |
| $t^{a}\quad{}(a>-1)$                                | $\frac{\Gamma(a + 1)}{s^{a + 1}}\quad{}(s \gt 0)$      |
| $\sin at$                                           | $\frac{a}{(s^2 + a^2)}\quad{}(s\gt0)$                  |
| $\cos at$                                           | $\frac{s}{(s^2 + a^2)}\quad{}(s\gt0)$                  |
| $\sinh at$                                          | $\frac{a}{(s^2 - a^2)}\quad{}(s \gt \left\|a\right\|)$ |
| $\cosh at$                                          | $\frac{s}{(s^2 - a^2)}\quad{}(s \gt \left\|a\right\|)$ |
| $e^{at} \sin bt$                                    | $\frac{b}{(s-a)^2 + b^2}\quad{}(s \gt a)$              |
| $e^{at} \cos bt$                                    | $\frac{s-a}{(s-a)^2 + b^2}\quad{}(s \gt a)$            |
| $t^n e^{at}\quad{}(\text{n is a positive integer)}$ | $\frac{n!}{(s - a)^{n + 1}}\quad(s \gt a)$             |
| $u_c(t)$                                            | $\frac{e^{-cs}}{s}\quad(s \gt 0)$                      |
| $u_c(t) f(t - c)$                                   | $e^{-cs} F(s)$                                         |
| $e^{ct} f(t)$                                       | $F(s - c)$                                             |
| $f(ct)$                                             | $(\frac{1}{c}) F(\frac{s}{c})\quad(c \gt 0)$           |
| $\delta(t - c) = \delta_c(t)$                       | $e^{-cs}$                                              |
| $f'(t)$                                             | $s F(s) - f(0)$                                        |
| $f''(t)$                                            | $s^2 F(s) - sf(0) - f'(0)$                             |

Examples:

- Using the definition of the Laplace transform, find the laplace transform of $f(t)=\sin{t}$
  
  - Remember the definition of the Laplace transform is $\mathscr{L}\left(f(t)\right)=\int_{0}^{\infty}e^{-st}f(t)dt$
  - Plug in: $\mathscr{L}\left(\sin{t}\right)=\int_{0}^{\infty}e^{-st}\sin{t}\space{}dt$
  - Use Integration by parts: $u=e^{-st},dv=\sin{t},du=-se^{-st},v=-\cos{t}$
  - $=-e^{-st}\cos{t}|^b_0\space{}+s\int^b_0e^{-st}\cos{t}$
  - Integration by parts x2: $u=e^{-st},dv=\cos{t},du=-se^{-st},v=\sin{t}$
  - $=-e^{-sb}\cos{b}+1+s(e^{-st}\sin{t}|^b_0+s\int^b_0e^{-st}\sin{t}\space{}dt)$
  - $\int_{0}^{b}e^{-st}\sin{t}\space{}dt=-e^{-sb}\cos{b}+1+se^{-bt}\sin{b}-s^2\int^b_0e^{-st}\sin{t}\space{dt}$
  - Apply limit to infinity: $\int_{0}^{b}e^{-st}\sin{t}\space{}dt=0+1+0-s^2\int^b_0e^{-st}\sin{t}\space{dt}$
  - Substitute $F(s)$: $F(s)=1-s^2F(s)$
  - $F(s)(1+s^2)=1$
  - $F(s)=\frac{1}{s^2+1}$

- Using the Laplace table, find the Laplace transform of $f(t)=e^{6t}\sin{8t}$
  
  - This equation matches the table entry $e^{at}\sin{bt}$ which transforms to $\frac{b}{(s-a)^2+b^2}$
  - Plugging the values for a and b into the solution gives: $F(s)=\frac{8}{(s-6)^2+64}$

- Using the Laplace table, find the Inverse Laplace transform of $F(s)=\frac{4}{s^2+64}$
  
  - This equation matches the table entry $\frac{a}{s^2+a^2}$ which transforms to $\sin{at}$
  - Before we can apply a n inverse Laplace we first need to make the equation match its table variant: $\frac{1}{2}\cdot{}\frac{8}{s^2+64}$
  - Plugging values in for a gives: $f(t)=\frac{1}{2}\sin{8t}$

# Laplace IVP's

Reminders: 

- The goal of solving initial value problems using Laplace Transforms is to convert a DEQ into the laplace system and then convert it back into standard form. 
- To solve initial value problems using Laplace Transforms you need to use the definitions of derivatives: 
  - $y'=Y(t)s-y(0)$ and $y''=Y(t)s^2-y(0)s-y'(0)$
- Often **Partial Fraction Decomposition** is needed to perform the inverse laplace.
- Any DEQ can be solved using Laplace Transforms, its just a matter of how complex it becomes.

Examples:

- Solve the following IVP using laplace trasnforms: $y''+16y=2\sin{2t},y(0)=1,y'(0)=0$
  
  - First apply a laplace transform to each side: $Ys^2-s-0+16Y=\frac{2}{s^2+4}$
  
  - Then segregate the values with $Y$: $Y(s^2+16)=\frac{2}{s^2+4}+s$
  
  - Set the entire equation equal to $Y$: $Y=\frac{2}{(s^2+16)(s^2+4)}+\frac{s}{s^2+16}$
  
  - Take the inverse laplace of each side: $\mathscr{L}^{-1}(Y)=\mathscr{L}^{-1}\left(\frac{2}{(s^2+16)(s^2+4)}+\frac{s}{s^2+16}\right)$
  
  - PFD: $\frac{2}{(s^2+16)(s^2+4)}=\frac{As+B}{s^2+16}+\frac{Cs+D}{s^2+4}$
  
  - $(As+B)(S^2+4)+(Cs+D)(S^2+16)=2$
  
  - $As^3+4As+Bs^2+4B+Cs^3+16Cs+Ds^2+16D=2$
    
    - $A+C=0$
    - $B+D=0$
    - $4A+16C=0$
    - $4B+16D=2$
    - $A=-C$
    - $-4C+16C=0$
    - $C=0,A=0$
    - $B=-D$
    - $-4D+16D=2$
    - $D=\frac{1}{6},B=-\frac{1}{6}$
  
  - $y(t)=\mathscr{L}^{-1}\left(-\frac{1}{6}\left(\frac{1}{s^2+16}\right)+\frac{1}{6}\left(\frac{1}{s^2+4}\right)+\frac{s}{s^2+16}\right)$
  
  - $y(t)=-\frac{1}{12}\sin{4t}+\frac{1}{6}\sin{2t}+\cos{4t}$

# Step Function

Reminders:

- A step function allows piecewise functions to have a laplace transform performed on them
- Step functions can be applied to other functions, causing their behavior to change
- A step function $u_c(t)$ can also be called a heaviside function and take the form $h(t-c)$

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
  \\
  See [The 3.2 Guide](https://github.com/noahw608/S2024-Diff-Eq-M2-Review/blob/master/3.2%20Guide_.pdf) for solutions of step function problems

# Convolution

Reminders:

- Convolution is an operation that is sometimes useful when dealing with laplace functions
- The definition of a convolution is the following: 
  $f (t)\ast g(t)=\int_{0}^{t} f(\tau) g(t-\tau) d \tau$
- Lets simplify that definition into steps:
  - you first turn the first function into Tau's ($\tau$) and the second function into t-Tau's ($t-\tau$) by replacing the t's in the function with the respective new term
  - Then you take the integral of the two new functions multiplied together with respect to tau from 0 to t. 
  - This will provide you with one new function in terms of t.
- The most useful application of a convolution is as an alternative to PFD
- If you have a Laplace Function such as $\frac{s+1}{s^2(s-2)}$ and need to inverse laplace it, instead of applying partial fractions, you can use a convolution definition:
  - $=\mathscr{L}^{-1}\left(\frac{s+1}{s^2}\right)\ast{}\mathscr{L}^{-1}\left(\frac{s+1}{s-2}\right)$
  - Breaking down this definition, you first take the inverse Laplace of each piece, and the convolve the results together. 
  - This will give you an original function in terms of t

Examples:

- If $f(t)=t$ and $g(t)=t$ find $f\ast{}g$
  
  - First Tauify: $f(\tau)=\tau{}$ and $g(t-\tau)=t-\tau$
  
  - Then create your integral: $=\int_{0}^{t} (\tau)(t-\tau) d \tau$
  
  - Simplify: $=\int_{0}^{t} \tau{}t-\tau^2 \space{} d \tau$
  
  - Solve: $\frac{t}{2}\tau{}^2-\frac{1}{3}\tau^3|^t_0$
  
  - $=\frac{t^3}{2}-\frac{t^3}{3}=\frac{3t^3}{6}-\frac{2t^3}{6}=\frac{t^3}{6}$

- Find the Inverse Laplace of $\frac{1}{(s-1)(s-3)}$ using convolution
  
  - First separate the denominator: $\mathscr{L}^{-1}\left(\frac{1}{(s-1)}\right)\ast{}\mathscr{L}^{-1}\left(\frac{1}{(s-3)}\right)$
  
  - Then solve each equation: $e^t\ast{}e^{3t}$
  
  - Tauify: $e^t=e^\tau{}$ and $e^{3t}=e^{3(t-\tau)}$
  
  - Integral: $\int^{t}_0e^\tau{}e^{3(t-\tau)}d\tau{}$
  
  - Simplify: $\int^{t}_0e^{3t-2\tau}d\tau{}$
  
  - Solve: $-\frac{1}{2}e^{3t-2\tau}|^t_0$
  
  - $=-\frac{1}{2}e^{t}+\frac{1}{2}e^{3t}$

- Solve the IVP: $=gt),y(0)=1,y'(0)=0$
  
  - Laplace: $s^2-6Y=G(s)$
  
  - Simplify: $(s1)G(s$$    - Separate: $Y(s)=\frac{1}{4}\frac{4}{s^2+16}G(s)+\frac{s}{s^2+16}$
  
  - Apply a convolution to the $G(s)$ term: $\frac{1}{4}\mathscr{L}^{-1}\left(\frac{4}{s^2+16}\right)\ast\mathscr{L}^{-1}(G(s))+\frac{s}{s^2+16}$
  
  - $\frac{1}{4}\left(\sin{4t}\ast{}g(t)\right)+\cos{4t}$
  
  - Tauify: $\sin{4(t-\tau)}$ and $g(\tau)$
  
  - $y=\frac{1}{4}\int^{t}_0{}\sin{4(t-\tau)g(\tau)d\tau}+\cos{4t}$ - This is where the book stops, IDK how to solve this
