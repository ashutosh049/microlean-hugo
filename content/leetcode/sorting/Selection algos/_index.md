---
bookCollapseSection: true
weight: 2
---

# Selection Algorithms

{{< hint info >}}
{{< fontawesome "brands/wikipedia-w" >}}
https://en.wikipedia.org/wiki/Selection_algorithm
{{< /hint >}}


---
{{< fontawesome "brands/wikipedia-w" >}}
{{< hint info >}}
## Quick Select
In computer science, [quickselect](https://en.wikipedia.org/wiki/Quickselect) is a [selection algorithm](https://en.wikipedia.org/wiki/Selection_algorithm) to find the kth smallest element in an
unordered list. It is related to the quicksort sorting algorithm. Like quicksort, it was developed
by Tony Hoare, and thus is also known as Hoare's selection algorithm.[1] Like quicksort, it is
efficient in practice and has good average-case performance, but has poor worst-case performance.
Quickselect and its variants are the selection algorithms most often used in efficient real-world
implementations.

Quickselect uses the same overall approach as quicksort, choosing one element as a pivot and
partitioning the data in two based on the pivot, accordingly as less than or greater than the pivot.
However, instead of recursing into both sides, as in quicksort, quickselect only recurses into one
side – the side with the element it is searching for. This reduces the average complexity from
{\displaystyle \Theta (n\log n)}\Theta (n\log n) to {\displaystyle \Theta (n)}\Theta (n), with a
worst case of {\displaystyle O(n^{2})}O(n^{2}).

As with quicksort, quickselect is generally implemented as an in-place algorithm, and beyond
selecting the kth element, it also partially sorts the data. See selection algorithm for further
discussion of the connection with sorting.

{{< /hint >}}