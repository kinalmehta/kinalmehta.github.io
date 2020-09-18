---
title: "Transformations"
permalink: /ClassNotes/transformations
excerpt: "Introduction to 3D transformations"
last_modified_at: 2020-09-18
toc: true
---

# The Transformation Matrix

## Basics of rotation
Let us consider a simple 2D case. In 2D, anti-clockwise rotation by angle $\theta$ can be performed on a vector $P$ in frame $A$ represented as $^{A}P$ to convert to frame $B$ represented as $^{B}P$ using rotation matrix $R^{A}_{B}$.

$$
^A P = {R_{B}^{A}} \:{^BP}\\

\text{where, }

\:R_{B}^{A}=\left[\begin{array}{ccc}\cos \theta & -\sin \theta & 0 \\\sin \theta & \cos \theta & 0 \\0 & 0 & 1\end{array}\right]
$$

# References
1. Introduction to Robotics: Mechanics and Control by John J Craig

