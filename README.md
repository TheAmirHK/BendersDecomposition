This method was first introudced by Prof. Jacques F. Benders in his paper "Partitioning procedures for solving mixed-variables program- ming problems" back in 1962. 
He explains this method as a partitioning procedure as it is clear from the title to partition mixed-integer problems where we have complicating variables (often integer) that make solving the problem directly difficult.
It works by decomposing the problem into a master problem and a subproblem. The master problem typically contains the integer variables, while the subproblem contains the continuous variables.
The general formulation of a mixed-integer problem that can benefit from this method is written as follow: <br>
## General formulation

<div align="center">

$min_{x,y} \quad c^T x + d^T y$

*S.t.*<br>

$Ax + By \geq b, \quad x \in X, \quad y \in Y$
</div>

where:

- $x$ are the complicating (integer) variables (solved in the master problem).
- $y$ are the continuous variables (solved in the subproblem).
- $Ax + By \geq b$ represents coupling constraints that involve both sets of variables.

## Master Problem (Solving for \( x \))
<div align="center">

$min_{x,\theta} \quad c^T x + \theta$

*S.t*

$x \in X$


$theta \geq \text{Benders' Cuts} \quad (\text{computed iteratively from subproblem duals})$
</div>

- The variable ${\theta}$ represents an approximation of the subproblem's cost.
- Benders' cuts are added iteratively to tighten the approximation.

## Subproblem (Solving for \( y \) given \( x \))
<div align="center">

$min_{y} \quad d^T y$

*S.t.*

$By \geq b - Ax, \quad y \in Y$
</div>

- The subproblem is continuous and easier to solve than the full problem.
- The dual solution of the subproblem generates Benders' cuts, which refine the master problem.
