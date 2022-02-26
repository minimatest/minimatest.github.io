---
layout: post
title: "Gradients and linear approximations" 
categories: misc 
---


## Chapter 11 Notes 


### Definition of Gradient

-   Wouldn’t it be nice to save all the partial derivatives in some data structure for easy retrieval later?! Now you can with something called the **gradient** which is a vector-valued function of the form $\mathbf{R}^{n} \rightarrow \mathbf{R}^{n}$ (of a scalar valued function) and stores all the partial derivatives of $f$ where $f: \mathbf{R}^{n} \rightarrow \mathbf{R}$). It is denoted as

$$ \nabla f=\left[\begin{array}{c}\frac{\partial f}{\partial x_{1}} \\\frac{\partial f}{\partial x_{2}} \\\vdots \\\frac{\partial f}{\partial x_{n}}\end{array}\right]. $$

-   This is all nice and dandy. However, there is some intense geometric meaning behind the gradient which we will discuss. The primary thing to know is that it gives the direction of steepest increase. Why? Let’s find out. (See third section).
	- Another important thing to know: gradient gives vector perpindicular to the tangent line on the curve at some point (see image below). 

### Linear approximation

-   In calculus I, we used derivatives and the meaning of “rate of change” to locally approximate the value of some complicated input (e.g. $x=0.999$) with some nearby value ($x=1$). We have a multivariable analogue given by the following formula.

> **Linear approximations (multivariable)**: To approximate $f(\mathbf{x})$ with some value $\mathbf{a}$ (remember that $\mathbf{a,x}$ are vectors meaning this is function takes in $n$-inputs), use the following: $$ f(\mathbf{x}) \approx f(\mathbf{a})+((\nabla f)(\mathbf{a})) \cdot(\mathbf{x}-\mathbf{a}) $$

- Note: $\mathbf{x}$ and $\mathbf{a}$ must be sufficiently close for this to work well. 

#### Linear approximation example

Let $f: \mathbf{R}^{n} \rightarrow \mathbf{R}$. Approximate $f(\mathbf{x})$ near $\mathbf{a}$ for $\mathbf{a}=(1,1)$ and $\mathbf{x}=(1.3,0.9)$ with $f(x, y)=x^{2}+2 y^{2}+x y$. 

- $(\nabla f)(x, y)=\left[\begin{array}{l}2 x+y \\ 4 y+x\end{array}\right]$ and therefore $(\nabla f)(1,1)=\left[\begin{array}{l}3 \\ 5\end{array}\right]$. 
Thus, by the formula given for a linear approximation of a multivariable function (defined above), we have 
$$\begin{aligned} f(1.3,0.9) & \approx f(1,1)+(\nabla f)(1,1) \cdot\left[\begin{array}{c}.3 \\ -.1\end{array}\right] \\ &=4+\left[\begin{array}{l}3 \\ 5\end{array}\right] \cdot\left[\begin{array}{c}.3 \\ -.1\end{array}\right] \\ &=4.4 . \end{aligned}$$ 


### 3. Geometric interpretation of gradient 

We will discuss how the gradient vector is normal to the contours (i.e. the visual significance of the gradient). 

Important thing to know: gradient gives vector perpindicular to the tangent line on the curve at some point.
> ![[Pasted image 20220202005732.png]]

- If you were to draw level curves for $f: \mathbf{R}^{2} \rightarrow \mathbf{R}$, then **the gradient gives you the normal vector to the level curve at some point $\mathbf{a}$**. 
	- Here are some examples of gradients at various points on a sample level curve: ![[Pasted image 20220202003919.png]]
- What this means is that we can find a tangent line to the level curve (which is 2-dimensional) at some point $(a,b)$ by $(\nabla f)(a, b) \cdot\left[\begin{array}{l}x-a \\ y-b\end{array}\right]=0$ which simplifies to $f_{x}(a, b)(x-a)+f_{y}(a, b)(y-b)=0$. 
- When we generalize to $\mathbf{R}^3$, we get a **tangent plane** to the level curve given by $(\nabla f)\left(a_{1}, a_{2}, a_{3}\right) \cdot\left[\begin{array}{l}x-a_{1} \\ y-a_{2} \\ z-a_{3}\end{array}\right]=0$ and simplifying: $z=h(a, b)+h_{x}(a, b)(x-a)+h_{y}(a, b)(y-b)$. 
	- This pattern is further generalized to $\mathbf{R}^n$ via tanget "hyper"-planes. 

Enumerating examples from the textbook: 
- Find equation of tangent line using normal vector to some curve in $\mathbf{R}^2$: Example 11.2.3., 11.2.4.  
- Same as above but with parametric representation for line is given in example 11.2.5. 
- Tangent planes is given in 11.2.6. 

#### Skill 1: find normal vector to curve at some point 

- Just take the gradient of the curve and plug in the point. 

Consider $x^{2}+x y+y^{3}=7$. We want to find the normal vector to the curve at $(2,1)$.  

$$(\nabla h)(x, y)=\left(2 x+y, x+3 y^{2}\right),$$

$$(\nabla h)(2,1)=(5,5)$$ 

That is our answer. Geometrically speaking, ![[Pasted image 20220202010231.png]]


#### Skill 1.b: parameterize vector normal to the tangent line 

How to parameterize the gradient? Parameterization of a line is given by $\mathbf{x}(t)=\mathbf{p}+t \mathbf{v}$. So to parameterize the normal vector (gradient) at some point $\mathbf{p}$, we plug in the gradient for $\mathbf{v}$ at the point and the point itself for $\mathbf{p}$. 

Example: consider the point $(2,1)$ whose gradient vector to the curve at that point is $(\nabla h)(2,1)=(5,5)$. We have 

$$\mathbf{x}(t)=\left[\begin{array}{l}2 \\ 1\end{array}\right]+t\left[\begin{array}{l}5 \\ 5\end{array}\right]=\left[\begin{array}{l}2+5 t \\ 1+5 t\end{array}\right].$$ 

#### Skill 2: find equation of tangent line to curve at some point 

- Take gradient to get normal vector, than develop some general vector along the tangent line which means that this vector must be perpindicular to the gradient (see drawing above for intuition) so the dot product equals 0. Then this gives us the equation! 

Consider $h(x, y)=x^{2}+y^{2}$. We want to find the equation of the tangent line to the curve (circle) at the point $(3,4)$. 

$$\nabla h=\left[\begin{array}{l}2 x \\ 2 y\end{array}\right],$$ 

$$(\nabla h)(3,4)=\left[\begin{array}{l}6 \\ 8\end{array}\right].$$ 

So this gives us the vector that is perpindicular to the curve at $(3,4)$. But we want the equation of the tangent line to the curve at $(3,4)$. To do this, **form a general vector that lies on the tangent line**. How do you do this? If $\left[\begin{array}{l}x \\ y\end{array}\right]$ is some point on this tangent line, then the *difference* vector $\left[\begin{array}{l}3 \\ 4\end{array}\right]$ to $\left[\begin{array}{l}x \\ y\end{array}\right]$ is *perpindicular* to the normal vector (gradient) which we found to be $\left[\begin{array}{l}6 \\ 8\end{array}\right]$. Thus, their dot product must equal $0$. And so we have the following: 

$$\left[\begin{array}{l}x-3 \\ y-4\end{array}\right] \cdot\left[\begin{array}{l}6 \\ 8\end{array}\right]=0$$ so $6(x-3)+8(y-4)=0$ is the equation of the tangent line to the curve at some point $(3,4)$. All done using gradients! 



#### Skill 3:  find equation of tangent *plane* to curve at some point 

We have been working with functions of the form $f: \mathbf{R}^{2} \rightarrow \mathbf{R}$. But we can also have functions of the form $f: \mathbf{R}^{3} \rightarrow \mathbf{R}$. In this case, we find a tangent *plane* instead of a line. How to do this? Exact same thing but add a $z$ component to the gradient and general vector that lies on the plane. 

Example: consider $f(x, y, z)=x^{2}+y^{2}+z^{2}$ at the point $(2,1,1)$. 

$$\nabla f=\left[\begin{array}{l}2 x \\ 2 y \\ 2 z\end{array}\right],$$ 

$$(\nabla f)(2,1,1)=\left[\begin{array}{l}4 \\ 2 \\ 2\end{array}\right],$$

$$
\left[\begin{array}{l}
4 \\
2 \\
2
\end{array}\right] \cdot\left[\begin{array}{l}
x-2 \\
y-1 \\
z-1
\end{array}\right]=0,
$$
$$2 x+y+z=6.$$ 


--- 

### 11.3 - Gradient descent 

Machine learning... woohoo! 

- Main goal of differential multivariable calculus is to solve real-world optimization problems of many input variables. However, in the real-world, such functions arre so complicated, that this cannot be solved using analytic methods. So we must *approximate* the solution numerically. Gradient descent gives us a way to do that. 
- How to minimize complicated function numerically? Picture a raindrop travelling down a mountain. It will eventually end up at a local minimum. How so? It starts at some position and moves some steps in the direction of the steepest descent (given by the negative gradient). It continiously does this until it lands at a minimum. 
- So we need two things during each iteration: **where to go**, and **how far to step** (learning rate): 
	- **Where to go (direction)**: As mentioned, we step in the direction of the negative gradient. But we only want the direction information of this vector--not the magnitude. So we make it a unit vector by dividing by its length. 
	- **How far to step**: in other words, how much should we "scale" the unit gradient vector by? And we step in this direction by that amount: $\mathbf{a}+t(\nabla f)(\mathbf{a})$ where $t$ is this scalar parameter and is called the "learning rate" and $\mathbf{a}$ is the point we are currently at. 
		- To step in the negative direction, we just multiply the gradient by a negative: $\mathbf{a}+-t(\nabla f)(\mathbf{a})$

(1) What is $\mathbf{a}-$ **where do we start**? We have no idea here; let's try $\mathbf{a}=(0,0)$.
(2) What is $t$ - **how far do we go at each step**? Again, we have no idea. In a realistic interpretation of gradient descent, one tries several values of $t$ and seeks the best one. (In machine learning contexts, $|t|$ is sometimes called the learning rate.) In the bare-bones version here, let's use $t=-(0.1)$.

For an example, see 11.3.5. 
