# Mathematical Optimization

Mathematical optimization is the study of finding the best feasible solution to a problem according to a specified objective. An optimization problem consists of an **objective function**, a set of **decision variables**, and, when applicable, a collection of **constraints** that restrict the set of feasible solutions.

A general mathematical optimization problem can be written as

$$
\begin{aligned}
\min_{x} \quad & f_0(x) \\
\text{subject to} \quad & f_i(x) \leq b_i, \qquad i=1,\ldots,m.
\end{aligned}
$$

Here,

* $x=(x_1,\ldots,x_n)\in\mathbb{R}^n$ is the **optimization variable** or **decision vector**.
* $f_0:\mathbb{R}^n\rightarrow\mathbb{R}$ is the **objective function**.
* $f_i:\mathbb{R}^n\rightarrow\mathbb{R}$, $i=1,\ldots,m$, are the **inequality constraint functions**.
* $b_i\in\mathbb{R}$ represents the corresponding **constraint bound**.

The objective function specifies what we want to minimize. The constraints define which values of $x$ are permissible.

---

## Feasible Solutions

A vector $x$ is called a **feasible solution** if it satisfies all the constraints:

$$
f_i(x) \leq b_i,
\qquad i = 1,\ldots,m.
$$

The set of all feasible solutions is called the **feasible region** or **feasible set**:

$$ \mathcal{F} = \{ x \in \mathbb{R}^n \|f_i(x) \leq b_i,\quad i = 1,\ldots,m \} $$





The optimization problem can therefore be viewed as finding the point within $\mathcal{F}$ that produces the smallest value of the objective function.

---

## Optimal Solution

A feasible vector $x^\star$ is called an **optimal solution** if its objective value is no greater than that of any other feasible vector.

Formally,

$$
f_0(x^\star)\leq f_0(z)
$$

for every $z\in\mathcal{F}$.

Thus,

$$
x^\star = \arg\min_{x\in\mathcal{F}} f_0(x).
$$

The corresponding value

$$
f_0(x^\star)
$$

is called the **optimal objective value**.

The notation $x^\star$ is commonly used throughout optimization literature to denote an optimal solution.

---

## Minimization and Maximization

Although optimization problems are frequently written as minimization problems, maximization problems can be converted into minimization problems.

A maximization problem

$$
\max_{x} \quad f(x)
$$

is equivalent to

$$
\min_{x} \quad -f(x).
$$

Therefore, many optimization algorithms are formulated only for minimization, with maximization handled by changing the sign of the objective function.

---

## Objective Functions

The **objective function** represents the quantity that the optimization procedure attempts to improve.

Depending on the application, the objective may represent:

* cost to be minimized,
* error to be minimized,
* risk to be minimized,
* computational loss to be minimized,
* energy consumption to be minimized,
* profit to be maximized,
* portfolio return to be maximized.

For example, a portfolio optimization problem may minimize portfolio variance:

$$
\min_w \quad w^T\Sigma w,
$$

where $w$ represents portfolio weights and $\Sigma$ represents the covariance matrix of asset returns.

---

## Constraints

Constraints restrict the set of permissible solutions.

### Inequality constraints

The general form is

$$
f_i(x)\leq b_i.
$$

For example,

$$
x_1+x_2\leq 10.
$$

### Equality constraints

Optimization problems may also contain equality constraints:

$$
h_j(x)=c_j, \qquad j=1,\ldots,p.
$$

A general constrained optimization problem can therefore be written as

$$
\begin{aligned}
\min_{x} \quad & f_0(x)\\
\text{subject to} \quad & f_i(x)\leq b_i, \qquad i=1,\ldots,m,\\
& h_j(x)=c_j, \qquad j=1,\ldots,p.
\end{aligned}
$$

Equality constraints are particularly important in methods such as **Lagrange multipliers**, **Karush-Kuhn-Tucker (KKT) conditions**, and **constrained numerical optimization**.

---

## Local and Global Optima

An optimization problem may contain multiple locally optimal points.

A point $x^\star$ is a **global minimum** if

$$
f(x^\star)\leq f(x)
$$

for every feasible $x$.

A point $x^\star$ is a **local minimum** if there exists a neighborhood around $x^\star$ such that

$$
f(x^\star)\leq f(x)
$$

for all feasible $x$ within that neighborhood.

A global minimum is therefore optimal over the entire feasible region, whereas a local minimum is optimal only within a neighborhood.

For non-convex problems, an algorithm may converge to a local minimum rather than the global minimum.

---

## Linear and Nonlinear Optimization

Optimization problems are commonly classified according to the mathematical structure of their objective and constraint functions.

### Linear Programming

An optimization problem is called a **linear program (LP)** when the objective function and all constraint functions are linear.

A linear function satisfies

$$
f(\alpha x+\beta y) = \alpha f(x)+\beta f(y)
$$

for all $x,y\in\mathbb{R}^n$ and scalars $\alpha,\beta$.

A standard linear program can be written as

$$
\begin{aligned}
\min_{x} \quad & c^Tx\\
\text{subject to} \quad & Ax\leq b.
\end{aligned}
$$

Linear programming is widely used in resource allocation, production planning, transportation, scheduling, and portfolio construction.

### Nonlinear Programming

If the objective or one or more constraints are nonlinear, the problem is generally classified as a **nonlinear program (NLP)**.

For example,

$$
\min_{x} \quad x^2+e^x
$$

is nonlinear because the objective contains nonlinear terms.

Similarly,

$$
x_1^2+x_2^2\leq 1
$$

is a nonlinear constraint.

---

## Convex and Non-Convex Optimization

Another fundamental classification is based on **convexity**.

A function $f$ is convex if

$$
f(\alpha x+(1-\alpha)y) \leq \alpha f(x)+(1-\alpha)f(y)
$$

for all $x,y$ in its domain and $0\leq\alpha\leq1$.

For a convex optimization problem, under appropriate conditions, every local minimum is also a global minimum. This property makes convex optimization particularly important because it provides strong theoretical guarantees for optimization algorithms.

In contrast, a **non-convex optimization problem** may contain multiple local minima, saddle points, and other stationary points. Many practical problems in machine learning, engineering, finance, and scientific computing are non-convex.

---

## Continuous and Discrete Optimization

Optimization problems can also be classified according to the type of decision variables.

### Continuous Optimization

The decision variables can take real-valued values:

$$
x\in\mathbb{R}^n.
$$

Examples include:

* portfolio weights,
* model parameters,
* physical design variables,
* calibration parameters.

### Discrete Optimization

The decision variables are restricted to discrete values.

For example,

$$
x_i\in\{0,1\}.
$$

Binary optimization is frequently used for selection and allocation problems, such as choosing a subset of assets, projects, or facilities.

When both continuous and discrete variables are present, the problem is referred to as **mixed-integer optimization**.

---

## Deterministic and Stochastic Optimization

Optimization algorithms can also be categorized according to how they search the solution space.

### Deterministic Optimization

Given the same initial conditions and inputs, a deterministic algorithm follows the same sequence of operations and produces the same result.

Examples include:

* Gradient Descent,
* Newton's Method,
* BFGS,
* Simplex Method.

### Stochastic Optimization

Stochastic algorithms incorporate randomness during the optimization process.

Examples include:

* Stochastic Gradient Descent,
* Genetic Algorithms,
* Particle Swarm Optimization,
* Simulated Annealing,
* Differential Evolution.

Randomness can help exploration of large or highly non-convex search spaces, although algorithmic behavior can vary across runs.

---

## Derivative-Based and Derivative-Free Optimization

Optimization algorithms can also be distinguished according to whether they require derivative information.

### First-Order Methods

These methods use the gradient:

$$
\nabla f(x).
$$

Examples:

* Gradient Descent,
* Momentum,
* Nesterov Accelerated Gradient,
* Adam.

### Second-Order Methods

These methods use second-order information, typically represented by the Hessian:

$$
H(x)=\nabla^2 f(x).
$$

Examples:

* Newton's Method,
* Trust-Region Methods,
* Quasi-Newton Methods.

### Derivative-Free Methods

These methods do not require explicit gradient or Hessian information.

Examples include:

* Nelder-Mead,
* Powell's Method,
* Pattern Search,
* Evolutionary Algorithms.

Derivative-free methods can be useful when the objective function is noisy, discontinuous, expensive to differentiate, or available only through function evaluations.

---

## Standard Form of an Optimization Problem

For reference, a broad form of a constrained optimization problem is

$$
\begin{aligned}
\min_{x\in\mathbb{R}^n} \quad & f_0(x)\\
\text{subject to} \quad & f_i(x)\leq b_i, \qquad i=1,\ldots,m,\\
& h_j(x)=c_j, \qquad j=1,\ldots,p.
\end{aligned}
$$

This formulation provides a common mathematical framework for a large class of optimization problems.

Different optimization algorithms exploit different properties of this formulation. For example, Gradient Descent uses first-order information, Newton's Method uses second-order information, linear programming exploits linear structure, and constrained optimization methods explicitly account for restrictions on the feasible region.

---

## Optimization Problem Classification

The major classifications introduced in this section can be summarized as:

| Classification | Categories |
| :--- | :--- |
| **Objective** | Minimization / Maximization |
| **Constraints** | Unconstrained / Constrained |
| **Function structure** | Linear / Nonlinear |
| **Convexity** | Convex / Non-convex |
| **Variables** | Continuous / Discrete / Mixed-integer |
| **Search mechanism** | Deterministic / Stochastic |
| **Derivative information** | First-order / Second-order / Derivative-free |
| **Number of objectives** | Single-objective / Multi-objective |

Understanding these classifications is important because the structure of an optimization problem strongly influences the algorithms that can be applied to it, the guarantees that can be obtained, and the computational resources required.

---
