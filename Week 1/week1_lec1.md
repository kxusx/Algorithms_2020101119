# week1_lec1

**Main Ideas**

1. Computer problems can be posed as a membership query problem
2. Axioms of Computations

**Computational Problems as Membership Query Problems**

A set can be created from all of the potential outputs that are the solution.

 As a result, the solution to the supplied input will simply be to verify whether it is part of the solution set.

Examples

1. Sorting [2,4,5,1,3] is basically checking if a permutation is part of the set [1,2,3,4,5] 
2. 3 part of prime no.s? → check if 3 is part of the set of prime numbers.

Hence language is subset of set of all possible inputs

Set can be {0,1}*

If the output has n bits then problems can be posed as n decision problems.

### Axioms of Computation

- It takes non-zero time to retrieve data from far off locations:   Basically, Random access memory is possible but only in small sizes. Information travels at a finite speed.
- Only finite information can be stored/retrieved from finite volume. Due to data storage requiring space. Space is limited in this world

Space and Time are key resources and parameters on which algorithm performance should be measured.

Different method to measure : 

- Asymptotic Analysis
- Worst Case Analysis
- Time / Space consumed