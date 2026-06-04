# Homework2

## Problem (4)
Find the inverse Laplace transform of the following function:
$$\mathcal{L}^{-1} \{ \frac{s+3}{(s+1)^2(s+2)} \}$$

---

## Detailed Step-by-Step Solution

### Step 1: Partial Fraction Expansion
Since the denominator contains a repeated factor $(s+1)^2$ (repeated roots), we must include terms for every power from 1 up to the highest power when setting up the partial fractions.

Let's assume:
$$\frac{s+3}{(s+1)^2(s+2)} = \frac{A}{s+1} + \frac{B}{(s+1)^2} + \frac{C}{s+2}$$

Our goal is to find the constants $A$, $B$, and $C$.

### Step 2: Solve for Constants $B$ and $C$ (Heaviside Cover-up Method)
Using the cover-up method, we can quickly determine the coefficient for the highest power of the repeated root ($B$) and the distinct root ($C$):

* **To find $B$ (set $s = -1$):**
    Multiply both sides by $(s+1)^2$ and evaluate at $s = -1$:
    $$B = \left. \frac{s+3}{s+2} \right|_{s=-1} = \frac{-1+3}{-1+2} = \frac{2}{1} = 2$$

* **To find $C$ (set $s = -2$):**
    Multiply both sides by $(s+2)$ and evaluate at $s = -2$:
    $$C = \left. \frac{s+3}{(s+1)^2} \right|_{s=-2} = \frac{-2+3}{(-2+1)^2} = \frac{1}{(-1)^2} = 1$$

### Step 3: Solve for Constant $A$
Since $A$ is not the highest-power term of the repeated root, we cannot use the cover-up method directly. Instead, we plug the known values $B=2$ and $C=1$ back into our assumption and substitute a simple value for $s$ (such as $s=0$) to solve for $A$:

Substitute $s=0, B=2, C=1$:
$$\frac{0+3}{(0+1)^2(0+2)} = \frac{A}{0+1} + \frac{2}{(0+1)^2} + \frac{1}{0+2}$$
$$\frac{3}{2} = A + 2 + \frac{1}{2}$$

Subtract $\frac{1}{2}$ from both sides:
$$1 = A + 2 \implies A = -1$$

Thus, the partial fraction expansion is:
$$\frac{s+3}{(s+1)^2(s+2)} = -\frac{1}{s+1} + \frac{2}{(s+1)^2} + \frac{1}{s+2}$$

---

### Step 4: Find the Inverse Laplace Transform of Each Term (Table Lookup)
According to the standard Laplace transform pairs:

1. $$\mathcal{L}^{-1} \{ \frac{1}{s+a} \} = e^{-at}$$
2. $$\mathcal{L}^{-1} \{ \frac{1}{(s+a)^2} \} = t \cdot e^{-at}$$ (First Shifting Theorem)

Applying these formulas to each of our three terms gives:

* $$\mathcal{L}^{-1} \{ -\frac{1}{s+1} \} = -e^{-t}$$
* $$\mathcal{L}^{-1} \{ \frac{2}{(s+1)^2} \} = 2te^{-t}$$
* $$\mathcal{L}^{-1} \{ \frac{1}{s+2} \} = e^{-2t}$$

---

## Final Answer

Combining all the terms yields the time-domain function $f(t)$:

$$f(t) = -e^{-t} + 2te^{-t} + e^{-2t} \quad (t \ge 0)$$

Alternatively, factoring out the common base $e^{-t}$ gives the simplified form:
$$f(t) = (2t - 1)e^{-t} + e^{-2t} \quad (t \ge 0)$$

## Problem (6)
Find the Fourier transform of the function $f(t) = te^{-5t}$ for $t \ge 0$.

---

### Detailed Step-by-Step Solution

#### Method 1: Using Fourier Transform Properties (Recommended)

1. **Base Transform Pair:**
   From the standard Fourier transform pairs, the transform of a causal exponential decay function is:
   $$\mathcal{F} \{ e^{-at}u(t) \} = \frac{1}{a + j\omega}$$
   Setting $a = 5$ gives:
   $$\mathcal{X}(\omega) = \mathcal{F} \{ e^{-5t}u(t) \} = \frac{1}{5 + j\omega} = (5 + j\omega)^{-1}$$

2. **Multiplication by $t$ Property (Frequency Differentiation):**
   The property states that multiplying a time-domain function by $t$ corresponds to differentiation in the frequency domain multiplied by $j$:
   $$\mathcal{F} \{ t \cdot x(t) \} = j \cdot \frac{d}{d\omega}\mathcal{X}(\omega)$$

3. **Differentiation:**
   Differentiating $\mathcal{X}(\omega)$ with respect to $\omega$ using the chain rule:
   $$\frac{d}{d\omega} (5 + j\omega)^{-1} = -1 \cdot (5 + j\omega)^{-2} \cdot \frac{d}{d\omega}(5+j\omega) = \frac{-j}{(5 + j\omega)^2}$$

4. **Final Combination:**
   Multiply the derivative by the factor of $j$:
   $$F(\omega) = j \cdot [ \frac{-j}{(5 + j\omega)^2} ] = \frac{-j^2}{(5 + j\omega)^2}$$
   Since $j^2 = -1$, we have $-j^2 = 1$:
   $$F(\omega) = \frac{1}{(5 + j\omega)^2}$$

---

#### Method 2: Direct Integration by Definition

By definition, the Fourier transform is:
$$F(\omega) = \int_{0}^{\infty} te^{-5t}e^{-j\omega t} dt = \int_{0}^{\infty} t e^{-(5 + j\omega)t} dt$$

Let $K = 5 + j\omega$. We evaluate the integral using integration by parts ($\int u dv = uv - \int v du$):
* Let $u = t \implies du = dt$
* Let $dv = e^{-Kt}dt \implies v = -\frac{1}{K}e^{-Kt}$

$$\int_{0}^{\infty} t e^{-Kt} dt = [ -\frac{t}{K}e^{-Kt} ]_{0}^{\infty} - \int_{0}^{\infty} (-\frac{1}{K}e^{-Kt}) dt$$

Evaluating the limits:
* The first term $[ -\frac{t}{K}e^{-Kt} ]_{0}^{\infty} = 0$ because $e^{-5t}$ dominates $t$ as $t \to \infty$.
* The remaining integral becomes:
  $$\frac{1}{K} \int_{0}^{\infty} e^{-Kt} dt = \frac{1}{K} [ -\frac{1}{K}e^{-Kt} ]_{0}^{\infty} = \frac{1}{K^2}$$

Substituting $K = 5 + j\omega$ back into the equation yields the final result:
$$F(\omega) = \frac{1}{(5 + j\omega)^2}$$
