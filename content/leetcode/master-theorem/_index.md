---
bookFlatSection: true
weight: 2
bookToc: true
title: Analysis Of Algorithm
bookHidden: false
---
# Analysis Of Algorithm

There are many ways to analyze recurrence relations like
- Master Theorem
- Substitution Method
- Recurrence tree method

## Master Theorem

Master Theorem presents a framework and formula using which solutions to many recurrence
relations can be obtained very easily. 

Almost all recurrences of type {{< katex >}}T(n) = aT(n/b) + f(n){{< /katex >}} can
be solved easily by doing a simple check and identifying one of the three cases provided by the theorem. 

By comparing {{< katex >}} n ^{\log_b a}  {{< /katex >}} (the number of leaves) with {{< katex >}}f(n){{< /katex >}}, one can decide upon
the time complexity of the algorithm.

The [master theorem](https://en.wikipedia.org/wiki/Master_theorem_(analysis_of_algorithms)) provides
a solution to [recurrence function](https://en.wikipedia.org/wiki/Recursive_algorithm) of the form


Let {{< katex >}}T(n){{< /katex >}} be a monotonically increasing function that satisfies:
<br>
<br>
{{< katex >}}T(n) = a T(n/b) + f(n){{< /katex >}}
<br>
{{< katex >}}T(1) = c{{< /katex >}}
<br>
<br>
where {{< katex >}}a \ge 1, b \ge 2, c>0{{< /katex >}}.
<br>
<br>
If {{< katex >}}f(n){{< /katex >}} is {{< katex >}}\Theta(n^d){{< /katex >}} where {{< katex >}}d \ge 0{{< /katex >}}
<br>
then
<br>
<br>
{{< katex >}}
x = \begin{cases}
a &\text{if } b \\
c &\text{if } d
\end{cases}
{{< /katex >}}


{{< hint info >}}
Continued....
{{< /hint >}}