# The "Teaching Concurrency" problem

In an article titled [Teaching Concurrency], Leslie Lamport wrote:

> Invariance is the key to understanding concurrent systems, but few engineers or
> computer scientists have learned to think in terms of invariants. Here is a
> simple example. Consider *N* processes numbered from 0 through *N−1* in which
> each process i executes

```
x[i] : = 1;
y[i] : = x [(i − 1) mod N ]
```

> and stops, where each *x[i]* initially equals 0. (The reads and writes of
> each *x[i]* are assumed to be atomic.) This algorithm satisfies the following
> property: after every process has stopped, *y[i]* equals 1 for at least one
> process *i*. It is easy to see that the algorithm satisfies this property; the last
> process *i* to write *y[i]* must set it to 1. But that process doesn’t set *y[i]* to 1
> because it was the last process to write *y*. What a process does depends only
> on the current state, not on what processes wrote before it. The algorithm
> satisfies this property because it maintains an inductive invariant. Do you
> know what that invariant is? If not, then you do not completely understand
> why the algorithm satisfies this property. How can a computer engineer
> design a correct concurrent system without understanding it? And how can
> she understand it if she has not learned how to understand even a simple
> concurrent algorithm?

The file [Simple.tla](Simple.tla) in this repo contains:

1. an implementation of this algorithm in [PlusCal].
1. an inductive invariant of this algorithm
* a [structured proof] of the property that uses the inductive invariant, and can be
  checked with [TLAPS].


*Note: I originally wrote this as a [Stack Overflow answer](https://stackoverflow.com/a/46108331/742)*.

[Teaching Concurrency]: https://www.microsoft.com/en-us/research/publication/teaching-concurrency/
[structured proof]: https://www.microsoft.com/en-us/research/publication/how-to-write-a-proof/
[TLAPS]: https://tla.msr-inria.inria.fr/tlaps/content/Home.html
[PlusCal]: https://lamport.azurewebsites.net/tla/pluscal.html


