# Engineering Mathematics - HW1

## 1. Separable Variables

**Q4: Solve $\frac{dy}{dx} = y \ln y$**

**Solution:**

Separate variables:
$$\frac{1}{y \ln y} dy = dx$$

Integrate:
$$\int \frac{1}{y \ln y} dy = \int dx$$

Let $u = \ln y, \ du = \frac{1}{y} dy$:
$$\int \frac{1}{u} du = \int dx$$
$$\ln |u| = x + C$$
$$\ln |\ln y| = x + C$$

Exponentiate both sides:
$$|\ln y| = e^{x+C} = e^C e^x$$

Let $c_1 = \pm e^C$:
$$\ln y = c_1 e^x$$
$$y = e^{c_1 e^x} \quad $$

---
**Note:** If $y=1$, $\ln y = 0$, then $\frac{dy}{dx} = 0$. Thus, $y=1$ is also a solution (the equilibrium solution).

## 2. Cauchy-Euler Equations

**Q14: Solve $x^2 y'' + 3xy' + y = 0$**

**Solution:**

This is a Cauchy-Euler equation. Let the solution be $y = x^m$.
Then $y' = mx^{m-1}$ and $y'' = m(m-1)x^{m-2}$.

Substitute these into the ODE:
$$x^2 [m(m-1)x^{m-2}] + 3x [mx^{m-1}] + [x^m] = 0$$
$$x^m [m(m-1) + 3m + 1] = 0$$

Since $x^m \neq 0$, we solve the **Auxiliary Equation**:
$$m^2 - m + 3m + 1 = 0$$
$$m^2 + 2m + 1 = 0$$
$$(m+1)^2 = 0$$

We obtain a repeated root:
$$m_1 = m_2 = -1$$

For a repeated root $m$ in a Cauchy-Euler equation, the basis of solutions is $x^m$ and $x^m \ln x$.

**General Solution:**
$$y = c_1 x^{-1} + c_2 x^{-1} \ln x$$
$$y = \frac{c_1 + c_2 \ln x}{x} \quad ✅$$
