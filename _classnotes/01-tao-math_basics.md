---
title: "Basics of Maths"
excerpt: "Basics of Maths"
permalink: /classnotes/applied_optimization/math_basics
last_modified_at: 2020-09-20
---

# Linear Algebra



# Calculus

<details><summary>Differentiation rules</summary>

<p>

- Addition/subtraction<br>
  $
    f(x) = g(x) \pm h(x) \\
    f'(x) = \dfrac{df}{dx} = g'(x) \pm h'(x)
  $

- Multiplication<br>
  $
    f(x) = g(x) * h(x) \\
    f'(x) = \dfrac{df}{dx} = g(x)*h'(x) + h(x)*g'(x)
  $

- Division<br>
  $
    f(x) = \dfrac{g(x)}{h(x)} \\
    f'(x) = \dfrac{df}{dx} = \dfrac{h(x)g'(x)-g(x)h'(x)}{h(x)^2}
  $
</p></details>


<details><summary>Taylor Series</summary>

<p>

- Taylor series can approximate any function $f(x)$ around some $x$

  $$
    f(x+h) = \sum_{i=0}^{\infin} \frac{h^i}{i!}f^{i}(x) \qquad \forall x \in  \textbf{dom } f
  $$

- it can also be written as

  $$
    f(x+h) = f(x) + hf'(x) + \frac{h^2}{2!}f''(x) + \dots
  $$
</p></details>


<details><summary>L'Hopital rule</summary>

<p>

- if
  $
    \lim_{x \to a} \dfrac{f(x)}{g(x)}
  $
  is of the form $\dfrac{0}{0}$ or $\dfrac{\infin}{\infty}$, then,

  $$
      \lim_{x \to a} \dfrac{f(x)}{g(x)} = \lim_{x \to a} \dfrac{f'(x)}{g'(x)} \quad \forall a \in \R
  $$
</p></details>



- Basic

  $$
  \nabla f(x) \rightarrow grad of f(x)
  $$


# References
1. https://www.geogebra.org/graphing

