

Everyone know factorial, if I would ask you what is the factorial of 5, so 5! you would know its 120. Its easy:

5 x 4 x 3 x 2 x 1 = 120

When we look at it we can so something fairly easily.

1! = 1
2! = 2
3! = 6
4! = 24
5! = 120

Its getting bigger exponentially, but now it will get weird.
What if I ask you this:
$$ 
\frac{3}{2} ! = ?
$$

You might say, its nonsenses because factorial only works with integers (whole numbers),  and this isn't one. Mathematicians being Mathematicians found a way to make sense of this nonsense.

## The Gamma function

$$
\Gamma(z)
$$
The basic way is pretty intuitive, we already know the points of the integers in a coordinate system, in form of a graph.  The question is, if we can draw a smooth curve between these points to understand what happens between the integers, and this is where the magic happens. The function for factorial is:

$$
n! = n \cdot (n - 1)!
$$
We want our extended function to preserve this relationship with also non-integer values. 

When we enforce this recursive property along with something called [[log convexity]], we get exactly one curve that fits . 

We want: $$ f(x) = x \cdot f(x - 1)$$ Not just for integers but for all x. Many functions in mathematics can be written via integrals, so lets try it:

$$f(x) = \int_0^\infty g(t, x)\,dt$$
Apply: $$f(x) = x\cdot f(x - 1)$$ 
If we plug this into our recursive property, we get: 

$$\int_0^\infty g(t, x)\,dt = x \cdot \int_0^\infty g(t,x - 1)\,dt$$
This means:
$$g(t, x) = x \cdo