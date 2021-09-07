# Week3Lec1_Khush_2020101119

## Khush Devendra Patel

**Main ideas :** 

- **Idea: Fast Fourier Transform***
- **Idea: Interpolation***

# Fast Fourier Theorem

Polynomial Multiplication : We have two d degree polynomials, say, $A(x)$ and $B(x).$

We have to get C(x) = A(x)B(x) in the quickest possible time. 

The concept of Fast Fourier Theorem emerges from the divide and conquer methodology.

$A(x)=a_0 +a_1x+···+a_dx^d$

$B(x)=b_0 +b_1x+···+b_dx^d$

$C(x) = c_0 + c_1x + · · · + c_2*_dx_2*_d$

Naive algorithm : $O(d^2)$

FFT : $O(d * log d)$

**Alternate Representation of Polynomials**

- **Coefficient Representation** : A(x) can be represented as $a_0 +a_1x+a_2x^2 +· · ·+a_dx^d$

or in a list $[a_0, a_1, · · · , a_d]$, where $a_i$ are the coefficients. 

- **Value Representation** : A(x) can also be represented as list of $({α,A(α)})$ pairs. This list should have at least d + 1 distinct pairs. (where d is the degree of A(x)).
- Conversion from Coefficient representation to Value representation is called **Evaluation**.
- Conversion from value representation to coefficient is called **Interpolation**.

### Algorithm

1.  Given A(x), evaluate it into 2d + 1 such pairs
2. Do the same for B(x)
3. Obtain $C(x_i)=A(x_i)B(x_i)$ for 1 ≤ i ≤ 2d+1
4. Therefore value representation of C(x) is known. 
5. Interpolate C(x) back to Coefficient representation.

### Evaluation by divide and conquer

Suppose we had $P(x) = x^2$, pick evaluation points.

When x = 1 and x = -1, we get same results. Similarly for x = 2 and x = -2

Assume

- $A(x) = x2 + 3x + 2$
- $B(x) = 2x^2 + 1$
- $C(x) = A(x)B(x)$ = $3x^5 +2x^4 +x^3 +7x^2 +5x+1$

Separating odd and even powers,

$C(x)=(2x^4 +7x^2 + 1)+x*(3x^4 +x^2 +5)$

or $C(x) = e(x^2) + x*o(x^2)$

$C(−x)=e(x^2)−x·o(x^2)$

There is a lot of overlap in calculations

If we have already calculated C(x) at x=1, then calculating at x=-1 isn't very expensive. We can split the big polynomial into two smaller units with degree d/2 - 1.

$T ( n ) = 2 T ( n/2 ) + O ( N )$. [O(n) for adding]

We can evaluate $e(x^2)$ and $o(x^2)$ at $n/2$  points, and this becomes a recursive algorithm.

But this trick works only for the this step of recursion.

Lets say we need $e(x^2) = 2x^4 +7x^2 +1$ at x = 1, 4, 9, 16.

But these aren’t positive/negative pairs. Recursions doesn't apply

We can solve it using complex numbers.

### Complex Numbers

Suppose we have P(x) = $x^3 + x^2 − x − 1$  and need at least 4 points.

![Untitled](Week3Lec1_Khush_2020101119%2039c28f1bbb444dbd9caafc741213db39/Untitled.png)

let them be ±x1,±x2. For the next level of recursion, x^2_2 should be equal to $−(x^2_1).$ We observe numbers bifurcate into their two square roots. Assume $x_1$ = 1, this is how nth roots of unity come into picture. Were n is an exact power of 2, and n ≥ 2d + 1

This algorithm does the evaluation step. It takes in the coefficients of a polynomial and evaluates it some special points which are the quickest to calculate.

## Algorithm :

![Untitled](Week3Lec1_Khush_2020101119%2039c28f1bbb444dbd9caafc741213db39/Untitled%201.png)

# Interpolation

After we have values for both polynomials at all n places, we can multiply each pair in linear time. It's just a matter of converting the value representation to the coefficient representation. Surprisingly, by slightly altering the formula, this may be solved in a similar way, taking advantage of the property of inverse of a DFT matrix.

![Untitled](Week3Lec1_Khush_2020101119%2039c28f1bbb444dbd9caafc741213db39/Untitled%202.png)

We put x as $ω_i$  (where ω=e^(2*i*pi/n))

![Untitled](Week3Lec1_Khush_2020101119%2039c28f1bbb444dbd9caafc741213db39/Untitled%203.png)

w in M^(-1) is 1/n*(w^(-1)) 

Now, we have the coefficients of C(x).