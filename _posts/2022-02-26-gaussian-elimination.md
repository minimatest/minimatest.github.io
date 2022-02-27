---
layout: post
title: "Gaussian elimination and more linear algebra" 
categories: misc 
---


#  🪃 Lay's Linear Algebra textbook notes 


## Chapter 1: Linear equations in Linear Algebra 

The point here is to learn how to solve systems of linear equations using matrix algebraic operations. This is useful for large and complex systems as we need to tell a computer step-by-step how to solve such a system. An algorithm called Gaussian Elimination (also known as row reduction) is used to convert any arbitrary coefficient matrix into an echelon form. We will then learn how to solve the system from a reduced echelon form. 

### Section 1.1: Systems of Linear Equations 

> The **augmented form** of matrix that represents a linear system, $Ax=b$, is simply the same as the coefficient matrix except that we tack on a new column vector that holds the components of $\mathbf{b}$. 

For example, consider 

$$
\begin{array}{r}
x_{1}-2 x_{2}+x_{3}=0 \\
2 x_{2}-8 x_{3}=8 \\
5 x_{1}-5 x_{3}=10
\end{array}
$$

which has a coefficient matrix: 

$$
\left[\begin{array}{rrr}
1 & -2 & 1 \\
0 & 2 & -8 \\
5 & 0 & -5
\end{array}\right]
$$

and now the *augmented* form: 

$$
\left[\begin{array}{rrrr}
1 & -2 & 1 & 0 \\
0 & 2 & -8 & 8 \\
5 & 0 & -5 & 10
\end{array}\right]. 
$$

To solve an SOE, we usually use methods like substitution and elimination like in middle school. However, there is no defined step-by-step path one can take that works for *all* systems. Instead, we use our intelligence to manipulate and reduce things to eventually solve the system. However, for very large systems, we want a computer to be able to solve it quickly so we need to define a step-by-step algorithm to solve systems. That is what we discuss in section 2.2. It relies on things called row operations which are essentially the operations we used in middle school but just applied the coefficient matrix instead. 

![[Pasted image 20220226163331.png]]


> **Definition**: a system that has one or more solutions is considered "consistent" whereas a system that has no solutions is considered "inconsistent". 

> **Theorem**: a system can either have 0, 1, or $\infty$ solutions. 

- So our two guiding questions are: 
	- Does a solution exist (i.e. is the system consistent)? 
	- If consistent, how many solutions exist (1 or $\infty$)? 

Note: we can answer these questions using the column and null space definitions, but in this textbook, we will use *algebraic* row operations on matrices instead. 

### Section 2.2: Row Reduction and Echelon Forms 

We will introduce some forms ("classifications") of matrices. Our goal is to essentially use row operations to "reduce" an arbitrary matrix to these forms. 

> **Row echelon form**: a matrix is said to be in row echelon form if the following three properties are satisfied 
> 1. All nonzero rows are above any rows of all zeros. 
> 2. For each row, the first nonzero entry (leading entry) is in a column that is to the right of the leading entry of the row above it.  
> 3. All entries in a column below a leading entry are zeros (which is implied by property 2).  

There is a special variant of the above form: 

> **Reduced row echelon form**: a matrix is said to be in *reduced *row echelon form if the above properties are satisfied in addition to the following: 
> 1. The leading entry in each nonzero row is a $1$. 
> 2. Each leading $1$ is the only nonzero entry in its *column*. 

 Note: the meaning of "echelon" is **steplike** pattern. For example, the following are row echelon matrices: 


 ![[hello.png|500]]

 and the following are reduced row echelon matrices: 

 ![[Pasted image 20220226161451.png|500]]

 Note: make sure to not confuse the reduced row echelon (abbreviated as RREF) matrices with the identity matrix (see the difference?). 

Also note that we never made any assumption about the size of the matrix yet. 

**Theorem**: each matrix maps to only one unique reduced row echelon matrix (though there can exist multiple row echelon forms). 


> **Pivot positions**: Once in RREF, a pivot position is any entry that is a leading 1. A pivot column is simply any column that contains such an entry. The pivot positions are in the same location as the leading entries of the row echelon form matrix. Thus, we can identity pivot positions directly from the REF matrix instead. 


#### The Row Reduction Algorithm 

Like mentioned, our goal is to solve linear systems using matrix algebra. We learned about RREF and REF because it makes it easier to solve the system in that form. With that intent, here we discuss a general method to take any arbitrary matrix and turn it into REF form (and optionally, RREF form). Then, we will discuss how to actually solve the systems once they are in this form (using a method called back-substitution). The terminology is ambigious across various texts so for clarity, here is what we mean when we say: 
-   **Gaussian Elimination:** The process of transforming a matrix into row echelon form
-   **Gauss-Jordan Elimination:** The process of transforming a row echelon matrix into _reduced_ row echelon form
-   **Back-substitution:** The process of directly solving a row echelon matrix, _without the need to transform it into reduced row echelon form_. 

To introduce the algorithm in a step-by-step fashion, we will walk through an example wiht the following matrix: 

$$
\left[\begin{array}{rrrrrr}0 & 3 & -6 & 6 & 4 & -5 \\ 3 & -7 & 8 & -5 & 8 & 9 \\ 3 & -9 & 12 & -9 & 6 & 15\end{array}\right]
$$

The steps involve an understanding of the elementary row operations discussed. 

> Step 1: identify the leftmost nonzero column. By requirement, we want to turn this into a pivot column meaning we need to apply row operations to get a pivot position in the topmost entry that is below the pivot positions of every row above it (which is the top entry in this case since this is the first row). 


![[Pasted image 20220226164239.png|300]]


> Step 2: Select a nonzero entry (can be any) in the pivot column as a pivot. If necessary, interchange rows to move this entry into the pivot position.  


Summarizing the last two steps: "starting from the left, find the first nonzero column. This is the first pivot column, and the position at the top of this column is the first pivot position. Switch rows if necessary to place a nonzero number in the first pivot position". 

![[Pasted image 20220226165301.png|500]]


> Step 3: use row replace operations to create zeros in all positions below the pivot (to satisfy property 3). 

This is a lot like "elimination" from middle school. How can we eliminate the nonzero entries in the pivot column? Well, we can perform a linear combination of the rows. 

In the example matrix, we simply add -1 times row 1 to row 2. 

Now we essentially just repeat this process until we are done. 



### References 

- Lay's textbook (lots of copy-pasting from there... I take no credit). 
- https://math.libretexts.org/Courses/Community_College_of_Denver/MAT_266_Differential_Equations_with_Linear_Algebra/11%3A_Systems_of_Equations/11.03%3A_Gaussian_Elimination#:~:text=A%20pivot%20position%20in%20a,that%20contains%20a%20pivot%20position. 
