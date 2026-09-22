# Objective Functions

The **objective function** is the mathematical function that defines what an optimization problem attempts to minimize or maximize. It provides a quantitative measure of the quality, cost, error, risk, utility, or performance associated with a particular choice of decision variables.

For an optimization problem

$$ \min_{x} \quad f_0(x), $$

the function

$$
f_0:\mathbb{R}^n\rightarrow\mathbb{R}
$$

is called the **objective function**, while

$$
x=(x_1,\ldots,x_n)
$$

is the optimization or decision variable.

The objective function maps every feasible decision vector to a scalar value that can be compared across candidate solutions.

---

## 1. Role of an Objective Function

Consider the general optimization problem

$$
\begin{aligned}
\min_{x} \quad & f_0(x) \\
\text{subject to} \quad & f_i(x) \leq b_i, \qquad i=1,\ldots,m.
\end{aligned}
$$

The objective function determines **what constitutes a better solution**.

If

$$
f_0(x_1)<f_0(x_2),
$$

then $$x_1$$ is preferred over $$x_2$$ in a minimization problem, provided both are feasible.

For a maximization problem,

$$ \max_{x} \quad f_0(x), $$

the solution with the larger objective value is preferred.

A maximization problem can equivalently be expressed as a minimization problem:

$$
\max_{x}\; f(x)
\quad\Longleftrightarrow\quad
\min_{x}\; -f(x).
$$

---

# 2. Decision Variables and Objective Value

Suppose

$$
x=
\begin{bmatrix}
x_1\\
x_2\\
\vdots\\
x_n
\end{bmatrix}
$$

is the decision vector.

The objective function

$$
f(x)
$$

assigns a scalar value to each possible decision vector.

For example,

$$
f(x_1,x_2)=x_1^2+x_2^2.
$$

For

$$
x=
\begin{bmatrix}
2\\
3
\end{bmatrix},
$$

the objective value is

$$
f(2,3)=2^2+3^2=13.
$$

The optimization algorithm searches for a value of \(x\) that minimizes or maximizes this scalar quantity.

---

# 3. Minimization Objective

A minimization problem has the form

$$
\boxed{x^\star = \arg\min\limits_{x\in\mathcal{F}} f(x)}
$$

where $${F}$$ denotes the feasible set.

The optimal solution satisfies

$$
f(x^\star)\leq f(x)
$$

for every feasible \(x\).

Typical quantities formulated as minimization objectives include:

* cost,
* error,
* loss,
* variance,
* energy,
* distance,
* computational time,
* tracking error,
* risk.

---

# 4. Maximization Objective

A maximization problem is written as

$$
\boxed{x^\star = \arg\max\limits_{x\in\mathcal{F}} f(x)}
$$

with

$$
f(x^\star)\geq f(x)
$$

for every feasible \(x\).

Typical quantities formulated as maximization objectives include:

* profit,
* utility,
* return,
* efficiency,
* likelihood,
* reward,
* information gain.

---

# 5. Common Types of Objective Functions

Objective functions can have many mathematical forms. Their structure has a major influence on which optimization algorithms are appropriate.

---

## 5.1 Linear Objective Function

A linear objective function has the form

$$
f(x)=c^Tx
$$

where

$$
c=
\begin{bmatrix}
c_1 & c_2 & \cdots & c_n
\end{bmatrix}^T.
$$

Explicitly,

$$
f(x)=
c_1x_1+c_2x_2+\cdots+c_nx_n.
$$

For example,

$$
\min_x \quad 3x_1+5x_2.
$$

Linear objectives form the basis of **linear programming** when the constraints are also linear.

---

# 6. Quadratic Objective Functions

A quadratic objective function can be written as

$$
f(x) = \frac{1}{2}x^T Q x + c^T x + d,
$$

where

* \(Q\) is an \(n\times n\) matrix,
* \(c\) is a vector,
* \(d\) is a scalar.

A common example is

$$
f(x_1, x_2) = x_1^2 + 2x_2^2.
$$


Quadratic objectives are important in:

* portfolio optimization,
* least-squares problems,
* control,
* signal processing,
* machine learning,
* quadratic programming.

If \(Q\) is positive semidefinite,

$$
Q\succeq0,
$$

then the quadratic objective is convex.

If

$$
Q\succ0,
$$

the objective is strictly convex and has a unique global minimizer when the feasible region is appropriate.

---

# 7. Least-Squares Objective

One of the most common objectives in statistics and machine learning is the **least-squares objective**.

Given observations \(y\), design matrix \(X\), and parameter vector \(\beta\),

$$
f(\beta) = \|X\beta - y\|_2^2.
$$

Equivalently,

$$
f(\beta) = (X\beta - y)^T(X\beta - y).
$$

The optimization problem is

$$
\boxed{
\min_\beta
\|X\beta-y\|_2^2
}
$$

which seeks the parameter vector that minimizes the squared prediction error.

Least-squares objectives appear in:

* linear regression,
* curve fitting,
* parameter estimation,
* signal reconstruction,
* calibration.

---

# 8. Loss Functions in Machine Learning

In machine learning, the objective function is often called a **loss function**, **cost function**, or **empirical risk**.

For a dataset containing \(N\) observations, a general empirical loss can be written as

$$
L(\theta) = \frac{1}{N} \sum_{i=1}^{N} \ell(y_i, \hat{y}_i),
$$

where

* $y_i$ is the observed target,
* $\hat{y}_i$ is the model prediction,
* $\theta$ represents model parameters,
* $\ell$ is the individual sample loss.

The optimization problem becomes

$$
\min_\theta L(\theta).
$$

Common loss functions include:

### Mean Squared Error

$$
\text{MSE} = \frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2
$$

### Mean Absolute Error

$$
\operatorname{MAE} = \frac{1}{N} \sum_{i=1}^{N} |y_i - \hat{y}_i|.
$$

### Binary Cross-Entropy

$$
L = -\frac{1}{N} \sum_{i=1}^{N} \left[ y_i \log(\hat{y}_i) + (1 - y_i) \log(1 - \hat{y}_i) \right].
$$

---

# 9. Regularized Objective Functions

An objective function can include a **regularization term** to discourage undesirable solutions.

A general regularized objective has the form

$$
\min_x
\quad
f(x)+\lambda R(x),
$$

where

* \(f(x)\) is the original loss,
* \(R(x)\) is the regularization function,
* \(\lambda\geq0\) controls the strength of regularization.

### L2 Regularization

$$
R(x)=\|x\|_2^2.
$$

Therefore,

$$
\min_x
\quad
f(x)+\lambda\|x\|_2^2.
$$

### L1 Regularization

$$
R(x)=\|x\|_1
=
\sum_i|x_i|.
$$

Therefore,

$$
\min_x
\quad
f(x)+\lambda\|x\|_1.
$$

L1 regularization can encourage sparse solutions, while L2 regularization generally penalizes large parameter magnitudes.

---

# 10. Convex Objective Functions

An objective function \(f\) is **convex** if

$$
f(\alpha x+(1-\alpha)y)
\leq
\alpha f(x)+(1-\alpha)f(y)
$$

for all \(x,y\) in its domain and

$$
0\leq\alpha\leq1.
$$

Geometrically, the line segment connecting two points on a convex function lies above or on the graph of the function.

For a differentiable function, convexity is also characterized by

$$
f(y)
\geq
f(x)+\nabla f(x)^T(y-x).
$$

This means that the first-order Taylor approximation provides a global lower bound on the function.

For twice-differentiable functions, a sufficient and, on convex domains, equivalent condition is

$$
\nabla^2 f(x)\succeq0.
$$

---

# 11. Strictly Convex Objective Functions

A function is strictly convex if

$$
f(\alpha x+(1-\alpha)y)
<
\alpha f(x)+(1-\alpha)f(y)
$$

for

$$
x\neq y,
\qquad
0<\alpha<1.
$$

Strict convexity is important because, when a minimizer exists, it is unique.

For a twice-differentiable function, positive definiteness of the Hessian,

$$
\nabla^2f(x)\succ0,
$$

is a common sufficient condition for strict convexity.

---

# 12. Non-Convex Objective Functions

A non-convex objective does not satisfy the convexity condition over its domain.

Such functions can contain:

* multiple local minima,
* local maxima,
* saddle points,
* flat regions,
* oscillatory regions.

For example,

$$
f(x)=x^4-x^2
$$

is non-convex over \(\mathbb{R}\).

Non-convex objectives occur frequently in:

* neural networks,
* engineering design,
* portfolio optimization with nonlinear constraints,
* clustering,
* control,
* quantitative model calibration.

The presence of non-convexity generally makes the optimization landscape more complicated.

---

# 13. Smooth and Non-Smooth Objectives

The differentiability of the objective function is another important property.

## Smooth Objective

A smooth objective has sufficiently well-behaved derivatives.

For example,

$$
f(x)=x^2
$$

is differentiable everywhere.

Gradient-based algorithms can directly use

$$
\nabla f(x).
$$

## Non-Smooth Objective

A non-smooth objective may not have a gradient at every point.

For example,

$$
f(x)=|x|
$$

is not differentiable at

$$
x=0.
$$

Such objectives may require methods based on:

* subgradients,
* proximal operators,
* coordinate descent,
* specialized non-smooth optimization methods.

---

# 14. Unimodal and Multimodal Objectives

A **unimodal** objective has a single basin of optimality over the region being considered.

A **multimodal** objective contains multiple local optima.

A multimodal objective can be represented conceptually as

$$
f(x)
$$

with several local minima.

This distinction is particularly important for global optimization and metaheuristic methods because local optimization methods may converge to different solutions depending on their initialization.

---

# 15. Objective Function Geometry

The geometry of the objective function determines how an optimization algorithm moves through the search space.

Consider the two-dimensional function

$$
f(x_1,x_2)=x_1^2+x_2^2.
$$

Its contours are concentric circles centered at the global minimum.

A more complicated function such as the Rosenbrock function,

$$
f(x,y)
=
(1-x)^2
+
100(y-x^2)^2,
$$

contains a narrow curved valley.

Different optimization algorithms can behave very differently on these landscapes.

For example:

* gradient-based methods follow local derivative information,
* Newton-type methods use curvature,
* derivative-free methods compare function evaluations,
* stochastic methods introduce randomness into the search.

---

# 16. Gradient of an Objective Function

For a differentiable objective

$$
f:\mathbb{R}^n\rightarrow\mathbb{R},
$$

the gradient is

$$
\nabla f(x)
=
\begin{bmatrix}
\frac{\partial f}{\partial x_1}\\
\frac{\partial f}{\partial x_2}\\
\vdots\\
\frac{\partial f}{\partial x_n}
\end{bmatrix}.
$$

The gradient points in the direction of steepest local increase of the objective.

Therefore,

$$
-\nabla f(x)
$$

points in the direction of steepest local decrease.

This is the fundamental principle behind Gradient Descent.

---

# 17. Hessian of an Objective Function

For a twice-differentiable objective, the Hessian is the matrix of second-order partial derivatives:

$$
\nabla^2 f(x)
=
\begin{bmatrix}
\frac{\partial^2f}{\partial x_1^2}
&
\cdots
&
\frac{\partial^2f}{\partial x_1\partial x_n}
\\
\vdots
&
\ddots
&
\vdots
\\
\frac{\partial^2f}{\partial x_n\partial x_1}
&
\cdots
&
\frac{\partial^2f}{\partial x_n^2}
\end{bmatrix}.
$$

The Hessian describes local curvature.

Its properties are useful for determining the local structure of an objective:

$$
\nabla^2f(x)\succ0
$$

indicates positive curvature in all directions, while

$$
\nabla^2f(x)\prec0
$$

indicates negative curvature in all directions.

An indefinite Hessian indicates that the function curves upward in some directions and downward in others, which is characteristic of saddle-point behavior.

---

# 18. Objective Scaling

The numerical scale of an objective function can affect optimization.

Suppose

$$
f(x)=10^6g(x).
$$

The minimizer is unchanged because multiplying the objective by a positive constant does not change the location of its optimum:

$$
\operatorname{arg\,min}_x f(x)
=
\operatorname{arg\,min}_x g(x).
$$

However, the magnitude of gradients and other numerical quantities changes:

$$
\nabla f(x)=10^6\nabla g(x).
$$

Therefore, scaling can influence numerical stability and the appropriate choice of algorithm parameters.

---

# 19. Multi-Objective Functions

Some problems involve several objectives simultaneously.

For example,

$$
\min_x
\begin{bmatrix}
f_1(x)\\
f_2(x)
\end{bmatrix}.
$$

The objectives may conflict with one another. For example:

$$
f_1(x)=\text{risk}
$$

and

$$
f_2(x)=-\text{return}.
$$

Instead of a single solution that simultaneously minimizes every objective, such problems generally involve a set of **Pareto-optimal solutions**.

A common scalarization approach is the weighted objective:

$$
F(x)
=
\lambda_1f_1(x)
+
\lambda_2f_2(x),
$$

where

$$
\lambda_1,\lambda_2\geq0.
$$

Multi-objective optimization is discussed separately in the repository's multi-objective optimization section.

---

# 20. Penalty and Composite Objectives

Constraints can sometimes be incorporated into an objective through penalty terms.

Suppose the original problem is

$$
\min_x f(x)
$$

subject to

$$
g(x)\leq0.
$$

A penalty formulation may be written as

$$
\min_x
\quad
f(x)
+
\lambda
\max(0,g(x))^2.
$$

The second term penalizes violations of the constraint.

More generally,

$$
F(x)
=
f(x)
+
\lambda P(x),
$$

where \(P(x)\) measures constraint violations.

Penalty and augmented-objective methods are important in constrained optimization.

---

# 21. Objective Function and Optimization Landscape

The **optimization landscape** refers to the values and geometry of the objective function over the search space.

For a two-dimensional objective,

$$
f:\mathbb{R}^2\rightarrow\mathbb{R},
$$

the landscape can be visualized using:

* surface plots,
* contour plots,
* heatmaps.

An optimization algorithm generates a sequence

$$
x_0,x_1,x_2,\ldots,x_T
$$

through this landscape.

The corresponding objective values are

$$
f(x_0),f(x_1),\ldots,f(x_T).
$$

A typical convergence analysis therefore examines

$$
f(x_t)
$$

as a function of iteration \(t\).

---

# 22. Objective Function Evaluation

Optimization algorithms repeatedly evaluate the objective function.

For an algorithm producing iterates

$$
x_0,x_1,\ldots,x_T,
$$

the objective evaluations are

$$
f(x_0),f(x_1),\ldots,f(x_T).
$$

For computationally expensive problems, the number of objective evaluations can become a significant part of the total computational cost.

Therefore, optimization experiments should often record:

* number of objective evaluations,
* number of gradient evaluations,
* number of Hessian evaluations,
* total runtime,
* final objective value,
* convergence tolerance.

---

# 23. Common Objective Functions

| Application            | Objective Function   | Typical Optimization Goal |
| ---------------------- | -------------------- | ------------------------- |
| Linear Regression      | Squared Error        | Minimize                  |
| Classification         | Cross-Entropy        | Minimize                  |
| Portfolio              | Variance / Risk      | Minimize                  |
| Portfolio              | Expected Return      | Maximize                  |
| Engineering            | Design Cost          | Minimize                  |
| Control                | Tracking Error       | Minimize                  |
| Clustering             | Within-Cluster Error | Minimize                  |
| Neural Networks        | Training Loss        | Minimize                  |
| Calibration            | Parameter Error      | Minimize                  |
| Reinforcement Learning | Expected Return      | Maximize                  |

---

# 24. Properties to Examine Before Optimization

Before selecting an optimization algorithm, the objective function should be examined for its mathematical and numerical properties.

Important questions include:

1. Is the objective continuous?
2. Is it differentiable?
3. Is it convex?
4. Is it strictly convex?
5. Is it smooth?
6. Is it deterministic or noisy?
7. Is it unimodal or multimodal?
8. Is the gradient available?
9. Is the Hessian available?
10. Is the objective expensive to evaluate?
11. Is the objective numerically well-scaled?
12. Does the objective contain discontinuities?
13. Does the objective have multiple local minima?
14. Are the decision variables continuous, discrete, or mixed?

These properties strongly influence algorithm selection.

---

# 25. Summary

The objective function is the central mathematical component of an optimization problem. It defines the quantity that the optimization algorithm attempts to improve.

The same general optimization framework can contain very different objective structures:

$$
\boxed{
\text{Objective Function}
\rightarrow
\begin{cases}
\text{Linear}\\
\text{Quadratic}\\
\text{Convex}\\
\text{Non-Convex}\\
\text{Smooth}\\
\text{Non-Smooth}\\
\text{Unimodal}\\
\text{Multimodal}\\
\text{Single-Objective}\\
\text{Multi-Objective}
\end{cases}
}
$$

Understanding these properties is essential because optimization algorithms are not independent of the problem structure. The choice of algorithm depends strongly on the mathematical characteristics of the objective function, the constraints, the available derivative information, and the computational cost of evaluating the objective.

The next topic, **constraints**, extends this discussion by introducing equality and inequality restrictions, feasible regions, active constraints, and the mathematical structure of constrained optimization.
