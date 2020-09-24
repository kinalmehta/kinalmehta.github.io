---
title: "Basics of Maths"
excerpt: "Basics of Maths"
permalink: /classnotes/applied_optimization/math_basics
last_modified_at: 2020-09-20
---

# Linear Algebra



# Calculus

- Differentiation rules

  - Addition/subtraction
    $$
      f(x) = g(x) \pm h(x) \\
      f'(x) = \dfrac{df}{dx} = g'(x) \pm h'(x)
    $$

  - Multiplication
    $$
      f(x) = g(x) * h(x) \\
      f'(x) = \dfrac{df}{dx} = g(x)*h'(x) + h(x)*g'(x)
    $$

  - Division
    $$
      f(x) = \dfrac{g(x)}{h(x)} \\
      f'(x) = \dfrac{df}{dx} = \dfrac{h(x)g'(x)-g(x)h'(x)}{h(x)^2}
    $$


- Taylor Series

  - Taylor series can approximate any function $f(x)$ around some $x$

    $$
      f(x+h) = \sum_{i=0}^{\infin} \frac{h^i}{i!}f^{i}(x) \qquad \forall x \in  \textbf{dom } f
    $$

  - it can also be written as

    $$
      f(x+h) = f(x) + hf'(x) + \frac{h^2}{2!}f''(x) + \dots
    $$


- L'Hopital rule

  - if
    $
      \lim_{x \to a} \dfrac{f(x)}{g(x)}
    $
    is of the form $\dfrac{0}{0}$ or $\dfrac{\infin}{\infty}$, then,

    $$
        \lim_{x \to a} \dfrac{f(x)}{g(x)} = \lim_{x \to a} \dfrac{f'(x)}{g'(x)} \quad \forall a \in \R
    $$


- Basic

  $$
  \nabla f(x) \rightarrow grad of f(x)
  $$


# References
1. https://www.geogebra.org/graphing

