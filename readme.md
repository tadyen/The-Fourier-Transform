# Complex numbers, Phasors, and The Fourier Transform

A proof by tadyen

## 0. Preface

I am **NOT SATISFIED** with conventional explanations of complex numbers and phasors, why they are treated identically to angle operations, and the proof of the Fourier Transform! Thus my own personal quest to resolve said dissatisfaction.

> Complex numbers are NOT vectors. Why are they commonly treated as identical?

> So, we convert complex numbers into the Argand-plane, and then de-convert it back? (phasor transform) How is this mathematically legal?

> Same thing with the Fourier transform (and Complex Fourier transform). So, the Complex Fourier is formed by converting the sin components of the classical Fourier into imaginary units to form the Complex Fourier Transform (via phasor transform). Sureeeee... that's  mathematically legal.

I've been taught complex numbers in highschool. 
> I've learnt that they involve plenty of trigonometry.

I've been taught complex numbers and phasors in 1st year of uni. 
> I've learnt they are useful as phasors, but left me with a huge question of *"How is it mathematically legal to perform phasor operations for angles and vectors? Aren't complex numbers and vectors completely different mathematically?"*

I've been taught the Fourier Transform in 2nd year. 
> My question from 1st year is now piled with a lack of intuition for the given proof (using orthoganality of cos and sin), and consequent usage of phasors on Fourier transforms. 

It's always either in too much detail (complicated way to learn) and with too little explanation. ***"Here is a proof you can read at your own leisure. It's one mega bundle of lecture slides choked with weird jargon and stuff"*** .My feeling towards it has always been a "Here's the formulae. Take it or leave it"

Why can we inherently treat angles as complex numbers? They are not the same thing! A gain or reduction of $ 90^\circ$ or $\frac{\pi}{2}$ radians is sometimes said to be simply multiplying or dividing by ***i*** but clearly angles and complex numbers belong to a different class (or set) of numbers or algebra! SO WHY!?!

My attempt to dispel this feeling has led me towards writing up proofs of it for myself. I am writing this as if the reader is **already familiar** with the Fourier transform and mathematics leading up to it, but might have similar struggles regarding it as the way I do. 

The following is my methodology for it.


## 1. Theorems

We require a few basics to prove the theorem.

Trigonometry

Complex Numbers

Taylor expansion

sinh, cosh and exponents

Phasors

Periodicities



### 1.1 Complex numbers and angles

#### Complex numbers are NOT angles

Complex numbers are an extension of the real numbers. We can go into talking about the [Caley-Dickson construction](https://en.wikipedia.org/wiki/Cayley%E2%80%93Dickson_construction) but that is beyond the scope of this piece. 

Complex numbers lose the property of **Order** from the Reals. They gain the property of **seperability**, ie. the imaginary part is seperable from the real part.

In the Reals ($R$), you can make statements like 

> $ a < b $ for $\{a,b\}\in{R}$

but for the Complex ($Z$) you can't. A statement like the above will not make sense. How does $(1 + i) > (2 - i)$ ??

However, angles HAVE the property of **order** to them. Algebra involving angles exist in $R$ (eg $\pm \pi$ radians). So, complex numbers **ARE NOT** angles!

A common interpretation of complex numbers are in the form of **vectors**, as having both a magnitude and direction. However, 2D vectors are really just **ordered pairs** that you can write in the form of $(x,y)$. We can also generalise vectors further into higher dimensions, or even talk about matrices, but we can't with complex numbers (or we can by invoking Caley-Dickson I suppose...) so clearly they are **NOT THE SAME**. (Quaternions, next down the list in the Caley-Dickson construction, allows for rotation in the 3D-plane). 

The loss of order can be argued in a multitude of ways, usually in the form of *"complex numbers imply vectors"*. 

However, this does not satisfy me enough. You can do the {mult, div} operations with complex numbers, but **NOT** with *'vector against another vector'*! The hack involves using rotational matrices and scalars, which isn't complex algebra anymore.


> ***Complex numbers ARE NOT vectors*** (to me at least)


#### Complex representations

Complex numbers can be represented in few ways. I assume the reader is already knowledgeable on it. Just to be on the same page regarding representations, I shall iterate the following:

let $z$ be a complex number given by:

> $ z = x + yi $ where ${x,y}\in{R}$ and $i$ is the imaginary number

> $A = \|(x,y)\|$

>$\theta = \text{atan2}(y,x)$

> Re{z} = x , Im{z} = y

then

Cartesian:

>$\text{ z = x + y}i$ 

Angular (Polar) form (sometimes known as $A \text{cis}\theta$ in *school notation*):

> $z = A(\cos(\theta)+i\sin(\theta)) =A\angle\theta$

Euler form:

> $z = Ae^{i\theta}$

It is a lot easier to work in the angular or Euler form with mult/div, since angles translate to add/sub in the angular form. I believe this is where the common treatment of Complex numbers being identical to Vectors comes from.



### 1.2 Taylor/Maclaurin series expansions:

Let a piecewice continuous function, $f(x)$ be $N$ times differentiable.

Let $P(x)$ be a polynomial that is also $N$ times differentiable:

$$
P(x) = p_0 + p_1x^1 + p_2x^2 + \ldots + p_kx^k + \ldots + p_kx^N 
$$

then

$$
{\frac{d^k}{dx^k}\left(P(x)\right)}|_{x=0} = {p_k}k!
$$

then

$$
p_k = \frac{{\frac{d^k}{dx^k}\left(P(x)\right)}|_{x=0}}{k!}
$$

If we let $P(x) = f(x)$ then we can construct the Maclaurin polynomial as:

$$
f(x) = \sum^{N}_{k=0} p_k x^k
$$

where
$$
p_k = \frac{{\frac{d^k}{dx^k}\left(f(x)\right)}|_{x=0}}{k!}
$$



#### Maclaurin series of $\cos(x)$, $\sin(x)$ and $e^x$
Proving for $\cos(x)$:

> $\frac{d^0}{dx^0} \cos(x) = \cos(x) \implies \frac{d^0}{dx^0}\cos(x)|_{x=0} = \cos(0) = 1$

> $\frac{d^1}{dx^1} \cos(x) = -\sin(x) \implies \frac{d^1}{dx^1}\cos(x)|_{x=0} = -\sin(0) = 0$

> $\frac{d^2}{dx^2} \cos(x) = -\cos(x) \implies \frac{d^2}{dx^2}\cos(x)|_{x=0} = -\cos(0) = -1$

> $\frac{d^3}{dx^3} \cos(x) = \sin(x) \implies \frac{d^3}{dx^3}\cos(x)|_{x=0} = \sin(0) = 0 \longleftarrow \text{(can use as a starting point for working out sin(x))}$ 

A repeat! 
> $\frac{d^4}{dx^4} \cos(x) = \cos(x) = \frac{d^0}{dx^0}\cos(x) \implies \mod4 \text{ cyclic}$

So, the coffecients are on even terms, and the sign simply changes. The Maclaurin for cos(x) is thus:
$$
\begin{aligned}
    \cos(x) &= \lim_{N\to\inf}\sum^{N/2}_{k=0} \frac{(-1)^kx^{2k}}{(2k)!} \\
    &= 1 + \frac{x^2}{2!} - \frac{x^4}{4!} + \frac{x^6}{6!} - \frac{x^8}{8!} + \ldots  
\end{aligned}
$$

Similarly:
$$
\begin{aligned}
    \sin(x) &= \lim_{N\to\inf}\sum^{N/2}_{k=0} \frac{(-1)^{k}x^{2k+1}}{(2k+1)!} \\
    &= x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \frac{x^9}{9!} - \ldots  
\end{aligned}
$$

Proving for $e^x$
> $\frac{d^n}{dx^n} e^x = e^x \implies \frac{d^n}{dx^n}e^x|_{x=0} = 1 \ldots\text{ for any }n\in N $

so

$$
\begin{aligned}
    e^x &= \lim_{N\to\inf}\sum^{N}_{k=0}\frac{x^k}{k!} \\
    &= 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \frac{x^4}{4!} + \ldots
\end{aligned}
$$

### 1.3 Euler's identity

If we substitute $x$ for $ix$ into the Maclaurin series for $e^x$ we get:

$$
\begin{aligned}
    e^{ix} &= \lim_{N\to\inf}\sum^{N}_{k=0}\frac{(ix)^k}{k!} \\
    &= 1 + ix + i^2\frac{x^2}{2!} + i^3\frac{x^3}{3!} + i^4\frac{x^4}{4!} + i^5\frac{x^5}{5!} + i^6\frac{x^6}{6!} + i^7\frac{x^7}{7!} + \ldots \\
    &= \left(1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \frac{x^6}{6!} \ldots\right) + i\left(x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} \ldots\right) \\
    &= \cos(x) + i\sin(x)
\end{aligned}
$$


#### cos and cosh:
cosh(x) is given by:

$$
\begin{aligned}
    \cosh(x) &= \frac{e^x+e^{-x}}{2}\\
    &= \frac{1}{2}\left( \left(1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \frac{x^4}{4!} + \frac{x^5}{5!} + \frac{x^6}{6!} + \frac{x^7}{7!} + \frac{x^8}{8!} + \ldots\right)
    +\left(1 - x + \frac{x^2}{2!} - \frac{x^3}{3!} + \frac{x^4}{4!} - \frac{x^5}{5!} + \frac{x^6}{6!} - \frac{x^7}{7!} + \frac{x^8}{8!} - \ldots\right)\right) \\
    &= 1 + \frac{x^2}{2!} + \frac{x^4}{4!} + \frac{x^6}{6!} + \frac{x^8}{8!} + \ldots  \\
\end{aligned}
$$

cos(ix) is given by:

$$
\begin{aligned}
    \cos(ix) &= \lim_{N\to\inf}\sum^{N/2}_{k=0} \frac{(-1)^k(ix)^{2k}}{(2k)!} \\
    &= \lim_{N\to\inf}\sum^{N/2}_{k=0} \frac{(-1)^k(i^2)^kx^{2k}}{(2k)!} \\
    &= \lim_{N\to\inf}\sum^{N/2}_{k=0} \frac{(-1)^k(-1)^kx^{2k}}{(2k)!} \\
    &= \lim_{N\to\inf}\sum^{N/2}_{k=0} \frac{x^{2k}}{(2k)!} \\
    &= 1 + \frac{x^2}{2!} + \frac{x^4}{4!} + \frac{x^6}{6!} + \frac{x^8}{8!} + \ldots  
\end{aligned}
$$

thus:
> $\cos(ix) = \cosh(x)$


#### sin and sinh:

sinh(x) is given by:

$$
\begin{aligned}
    \sinh(x) &= \frac{e^x-e^{-x}}{2}\\
    &= \frac{1}{2}\left( \left(1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \frac{x^4}{4!} + \frac{x^5}{5!} + \frac{x^6}{6!} + \frac{x^7}{7!} + \frac{x^8}{8!} + \ldots\right) 
    -\left(1 - x + \frac{x^2}{2!} - \frac{x^3}{3!} + \frac{x^4}{4!} - \frac{x^5}{5!} + \frac{x^6}{6!} - \frac{x^7}{7!} + \frac{x^8}{8!} - \ldots\right)\right) \\
    &= x + \frac{x^3}{3!} + \frac{x^5}{5!} + \frac{x^7}{7!} + \frac{x^9}{9!} + \ldots  \\
\end{aligned}
$$

sin(ix) is given by:

$$
\begin{aligned}
    \sin(ix) &= \lim_{N\to\inf}\sum^{N/2}_{k=0} \frac{(-1)^{k}(ix)^{2k+1}}{(2k+1)!} \\
    &= \lim_{N\to\inf}\sum^{N/2}_{k=0} \frac{(i)(-1)^{k}(i)^{2k}x^{2k+1}}{(2k+1)!} \\
    &= \lim_{N\to\inf}\sum^{N/2}_{k=0} \frac{(i)x^{2k+1}}{(2k+1)!} \\
    &=i\left( x + \frac{x^3}{3!} + \frac{x^5}{5!} + \frac{x^7}{7!} + \frac{x^9}{9!} + \ldots\right)
\end{aligned}
$$

thus:
> $\sin(ix) = i\sinh(x)$

> $\implies i\sin(ix) = -\sinh(x)$

Looking at Euler's identity again, we have:

$$
\begin{aligned}
    \cos(ix) + i\sin(ix) &= e^{i(ix)} \\
    &= e^{-x} \\
    &= \cosh(x)-\sinh(x)\\
    \cosh(x)-\sinh(x) &= \left(\frac{e^x+e^{-x}}{2}\right)-\left(\frac{e^x-e^{-x}}{2}\right) \\
    &= e^{-x} \longrightarrow\text{consistent!}
\end{aligned}
$$


```python

```
