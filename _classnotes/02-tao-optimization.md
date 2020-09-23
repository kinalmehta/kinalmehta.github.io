---
title: "Optimization"
excerpt: "Optimization"
permalink: /classnotes/applied_optimization/optimization
last_modified_at: 2020-09-20
---

# Optimization Problem

## Problem Defination
A problem of the form
$$
\min f(x) \\
\text{subject to } x \in C
$$
- \\(f(x)\\) is the objective function
- C is called the constrained set
- find \\(x\\) s.t. \\(f(x)\\) is minimized

## Problem Formulation

- Model the problem as optimization (Modelling)
  - objective function
  - constraints
- Solve using optimization (Solver)
  - Problem class
    - linear/non-linear
    - smooth/non-smooth
    - convex/non-convex
  - use suitable solver based on problem class


# Convexity

- Indication function relates convex functions and convex sets
- Epi-graph of \\(f\\) is a set of all points above the function.
  - if a fucntion is convex, then its epi-graph is convex and vice-versa
  
## Convex sets



