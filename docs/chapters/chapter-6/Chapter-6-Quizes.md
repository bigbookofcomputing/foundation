
# **Chapter-6: Quizes**

---

!!! note "Quiz"
    **1. What is the fundamental physical concept that numerical integration, or quadrature, aims to compute?**

    - A. The instantaneous rate of change.
    - B. The total accumulation of a quantity over a domain.
    - C. The optimal step size to balance truncation and round-off error.
    - D. The roots of a complex polynomial.

    ??? info "See Answer"
        **Correct: B**

        *(Numerical integration is the computational equivalent of the integral ($\int f(x) dx$), which calculates global, accumulated properties like total work done, total probability, or the center of mass.)*

---

!!! note "Quiz"
    **2. The Trapezoidal Rule approximates the area under a curve by tiling it with which geometric shape?**

    - A. Rectangles with height equal to the midpoint value.
    - B. Parabolas connecting three adjacent points.
    - C. Trapezoids formed by connecting adjacent data points with a straight line.
    - D. Triangles formed by the x-axis and two data points.

    ??? info "See Answer"
        **Correct: C**

        *(The Trapezoidal Rule uses linear interpolation between points, forming a trapezoid. Its area is the interval width times the average height of the two sides.)*

---

!!! note "Quiz"
    **3. If you double the number of intervals ($N$) used in the Trapezoidal Rule, by what factor does the total truncation error decrease?**

    - A. 2
    - B. 4
    - C. 8
    - D. 16

    ??? info "See Answer"
        **Correct: B**

        *(The Trapezoidal Rule is a second-order accurate method, meaning its error scales as $O(h^2)$. Halving the step size $h$ (by doubling $N$) reduces the error by a factor of $2^2 = 4$.)*

---

!!! note "Quiz"
    **4. What is the primary advantage of Simpson's Rule over the Trapezoidal Rule?**

    - A. It is simpler to implement.
    - B. It does not require a uniform grid.
    - C. It has a much higher order of accuracy ($O(h^4)$ vs. $O(h^2)$).
    - D. It can handle infinite integration limits directly.

    ??? info "See Answer"
        **Correct: C**

        *(Simpson's Rule uses parabolic tiles that match the function's curvature, leading to fourth-order accuracy. This means its error decreases by a factor of 16 when the step size is halved, converging much faster than the Trapezoidal Rule.)*

---

!!! note "Quiz"
    **5. What is the characteristic weighting pattern for the Extended Simpson's Rule?**

    - A. `1/2, 1, 1, ..., 1, 1/2`
    - B. `1, 2, 2, ..., 2, 1`
    - C. `1, 4, 2, 4, ..., 4, 1`
    - D. `1, 3, 3, 1`

    ??? info "See Answer"
        **Correct: C**

        *(The Extended Simpson's Rule formula is $I \approx \frac{h}{3} [y_0 + 4y_1 + 2y_2 + \dots + 4y_{N-1} + y_N]$. This famous pattern arises from summing the areas of overlapping parabolic tiles.)*

---

!!! note "Quiz"
    **6. A critical requirement for applying the standard Extended Simpson's Rule is that:**

    - A. The function must be linear.
    - B. The number of data points must be even.
    - C. The number of intervals ($N$) must be even.
    - D. The step size $h$ must be greater than 1.

    ??? info "See Answer"
        **Correct: C**

        *(Because Simpson's Rule uses a three-point parabolic tile that spans two intervals, the total number of intervals must be even to tile the entire domain without leaving a single interval leftover.)*

---

!!! note "Quiz"
    **7. What is the "Aha! Moment" or key principle behind Gaussian Quadrature?**

    - A. It uses random sampling points to estimate the integral.
    - B. It achieves maximum accuracy by optimally choosing both the sample points ($x_i$) and their weights ($w_i$).
    - C. It fits a high-degree polynomial to the entire dataset at once.
    - D. It is an adaptive version of Simpson's Rule.

    ??? info "See Answer"
        **Correct: B**

        *(Unlike grid methods with fixed points, Gaussian Quadrature treats the sample locations and weights as free parameters, choosing them to perfectly integrate polynomials of the highest possible degree for a given number of points.)*

---

!!! note "Quiz"
    **8. An $N$-point Gaussian Quadrature rule can perfectly integrate any polynomial up to what degree?**

    - A. $N$
    - B. $N-1$
    - C. $2N$
    - D. $2N-1$

    ??? info "See Answer"
        **Correct: D**

        *(With $N$ points, we have $2N$ degrees of freedom ($N$ positions and $N$ weights). This allows the method to be exact for any polynomial of degree up to $2N-1$. For example, a 2-point rule is exact for cubics.)*

---

!!! note "Quiz"
    **9. You have a pre-existing, fixed grid of experimental data in a NumPy array. Which Python function is most appropriate for integrating it?**

    - A. `scipy.integrate.quad`
    - B. `scipy.integrate.simpson` or `scipy.integrate.trapezoid`
    - C. A manual implementation of Monte Carlo integration.
    - D. `numpy.fft.fft`

    ??? info "See Answer"
        **Correct: B**

        *(`quad` is for callable functions, as it needs to evaluate the function at its own optimal points. For data on a fixed grid, you must use a grid-based method like `simpson` or `trapezoid` which work directly with the provided `x` and `y` arrays.)*

---

!!! note "Quiz"
    **10. How can an integral with an infinite limit, such as $\int_0^\infty f(x) dx$, be "tamed" for numerical evaluation?**

    - A. By integrating to a very large number like $10^{10}$.
    - B. By using a change of variables (e.g., $t = 1/(1+x)$) to map the infinite domain to a finite one.
    - C. By using the Trapezoidal rule, which handles infinity automatically.
    - D. This type of integral cannot be solved numerically.

    ??? info "See Answer"
        **Correct: B**

        *(The rigorous method is to use a substitution that "compactifies" the infinite interval into a finite one, like $[0, 1]$. This transforms the problem into a standard form that any quadrature method can handle without guesswork.)*

---

!!! note "Quiz"
    **11. The integral for the exact period of a nonlinear pendulum, $T \propto \int_0^{\theta_0} \frac{d\theta}{\sqrt{\cos\theta - \cos\theta_0}}$, presents what specific numerical challenge?**

    - A. An infinite integration limit.
    - B. An endpoint singularity where the integrand goes to infinity.
    - C. The function is too noisy for grid methods.
    - D. The integral is high-dimensional.

    ??? info "See Answer"
        **Correct: B**

        *(At the upper limit $\theta = \theta_0$, the denominator becomes $\sqrt{0}$, causing the integrand to diverge. A naive grid-based method would fail with a division-by-zero error.)*

---

!!! note "Quiz"
    **12. Why is `scipy.integrate.quad` the ideal tool for solving the nonlinear pendulum integral?**

    - A. It is the fastest implementation of the Trapezoidal rule.
    - B. It uses Monte Carlo sampling, which is robust to singularities.
    - C. It is an adaptive Gaussian quadrature method with built-in handling for endpoint singularities.
    - D. It converts the integral into a differential equation.

    ??? info "See Answer"
        **Correct: C**

        *(`quad` automatically detects the singularity, concentrates its evaluation points away from the problematic endpoint, and uses specialized techniques to calculate the integral accurately without failing.)*

---

!!! note "Quiz"
    **13. What is the "Curse of Dimensionality" in the context of numerical integration?**

    - A. The fact that all methods become less accurate for functions of complex variables.
    - B. The exponential increase in the number of grid points ($N^D$) required by grid-based methods as dimension ($D$) increases.
    - C. The slow $O(1/\sqrt{N})$ convergence of Monte Carlo methods.
    - D. The requirement that $N$ must be even for Simpson's rule.

    ??? info "See Answer"
        **Correct: B**

        *(A grid with just 10 points per dimension requires $10^2=100$ points in 2D, but an impossible $10^{10}$ points in 10D. This exponential scaling makes grid methods completely infeasible for high-dimensional problems.)*

---

!!! note "Quiz"
    **14. What is the "magic" property of Monte Carlo integration's error that allows it to defeat the Curse of Dimensionality?**

    - A. The error is always zero.
    - B. The error scales as $O(1/N^4)$, which is very fast.
    - C. The error scaling, $O(1/\sqrt{N})$, is independent of the dimension $D$.
    - D. It uses random numbers, which are not cursed.

    ??? info "See Answer"
        **Correct: C**

        *(The error of a Monte Carlo estimate is $\sigma/\sqrt{N}$, where $\sigma$ is the function's standard deviation. This formula has no dependence on dimension $D$. Therefore, the number of samples needed to achieve a certain accuracy is the same in 3D, 10D, or 1000D.)*

---

!!! note "Quiz"
    **15. In which of the following scenarios would Monte Carlo integration be the *only* feasible method?**

    - A. Calculating $\int_0^1 \sin(x) dx$ to high precision.
    - B. Finding the area under a curve from 50 experimental data points.
    - C. Calculating a partition function by integrating over the positions of 1000 particles in a box (a 3000-dimensional integral).
    - D. Integrating a function with a single, known singularity.

    ??? info "See Answer"
        **Correct: C**

        *(For low-dimensional problems, grid methods are far more accurate. But for the massive dimensionality of a many-body system in statistical mechanics, grid methods are impossible. Monte Carlo is the only viable approach.)*

---

!!! note "Quiz"
    **16. To numerically calculate the center of mass of a non-uniform rod, $\bar{x} = \frac{\int x \lambda(x) dx}{\int \lambda(x) dx}$, what must you do?**

    - A. Solve only one integral, as the other is always 1.
    - B. Numerically evaluate two separate integrals: one for the numerator and one for the denominator (total mass).
    - C. Differentiate the density function $\lambda(x)$.
    - D. Use a Monte Carlo method, as this is a high-dimensional problem.

    ??? info "See Answer"
        **Correct: B**

        *(The center of mass is a ratio of two accumulated quantities. You must compute the integral for the total mass ($M = \int \lambda(x) dx$) and the integral for the first moment of mass ($\int x \lambda(x) dx$) and then divide the results.)*

---

!!! note "Quiz"
    **17. A log-log plot of error vs. step size ($h$) is created for an integration method. The plot is a straight line with a slope of -4. What method was likely used?**

    - A. Trapezoidal Rule
    - B. Simpson's Rule
    - C. Monte Carlo Integration
    - D. Euler's Method

    ??? info "See Answer"
        **Correct: B**

        *(An error that scales as $O(h^4)$ appears as a line with slope -4 on a log-log plot of error vs. $h$. This is the signature of Simpson's Rule. The Trapezoidal Rule would have a slope of -2.)*

---

!!! note "Quiz"
    **18. To tame a singularity in an integral like $\int_0^1 \frac{1}{\sqrt{x}} dx$, a good change of variables would be:**

    - A. $x = t + 1$
    - B. $x = 1/t$
    - C. $x = t^2$
    - D. $x = \sin(t)$

    ??? info "See Answer"
        **Correct: C**

        *(With $x = t^2$, we have $dx = 2t \, dt$. The integral becomes $\int_0^1 \frac{1}{\sqrt{t^2}} (2t \, dt) = \int_0^1 \frac{1}{t} (2t \, dt) = \int_0^1 2 \, dt$. The singularity is perfectly cancelled, leaving a trivial integral.)*

---

!!! note "Quiz"
    **19. For a 1D integral of a smooth function, why is Simpson's rule generally preferred over Monte Carlo integration?**

    - A. Simpson's rule is easier to code.
    - B. Simpson's rule has a much faster convergence rate ($O(N^{-4})$ vs. $O(N^{-0.5})$).
    - C. Monte Carlo methods cannot be used in 1D.
    - D. Simpson's rule gives a less noisy result.

    ??? info "See Answer"
        **Correct: B**

        *(In low dimensions, the superior convergence rate of grid methods is dominant. To get an error of $10^{-8}$, Simpson's might need ~100 points, while Monte Carlo would need an astronomical $\sim 10^{16}$ samples. The trade-off for dimension-independence is very slow convergence.)*

---

!!! note "Quiz"
    **20. The optimal sample points ($x_i$) used in Gaussian Quadrature are the roots of which family of polynomials?**

    - A. Taylor Polynomials
    - B. Chebyshev Polynomials
    - C. Fourier Series
    - D. Legendre Polynomials

    ??? info "See Answer"
        **Correct: D**

        *(The non-uniformly spaced, optimal sample points for standard Gaussian Quadrature on the interval [-1, 1] are precisely the roots of the Legendre Polynomials.)*

---

!!! note "Quiz"
    **21. How does the true period of a pendulum change as its initial swing angle $\theta_0$ increases significantly?**

    - A. It decreases.
    - B. It remains constant, as predicted by the small-angle approximation.
    - C. It increases.
    - D. It oscillates randomly.

    ??? info "See Answer"
        **Correct: C**

        *(For large amplitudes, the restoring force is weaker than the linear approximation suggests, so the pendulum spends more time at the extremes of its swing. This makes the period longer than the constant $T \approx 2\pi\sqrt{L/g}$.)*

---

!!! note "Quiz"
    **22. In the extended trapezoidal rule formula $I \approx h \left[ \frac{1}{2}y_0 + y_1 + \dots + y_{N-1} + \frac{1}{2}y_N \right]$, why are the endpoints weighted by 1/2?**

    - A. To make the formula more symmetric.
    - B. Because endpoints are less important than interior points.
    - C. Because each interior point is counted twice (by the trapezoid on its left and right), while endpoints are only counted once.
    - D. It is an arbitrary choice that gives better results.

    ??? info "See Answer"
        **Correct: C**

        *(When summing the areas $h(y_i+y_{i+1})/2$, every interior point $y_k$ appears in two terms, for a total contribution of $h \cdot y_k$. The endpoints $y_0$ and $y_N$ appear in only one term each, giving them a contribution of $h/2 \cdot y_k$.)*

---

!!! note "Quiz"
    **23. You are given a callable Python function `f(x)` and asked to find $\int_0^\infty f(x) dx$. What is the most direct and professional approach?**

    - A. Manually implement Simpson's rule up to a large number.
    - B. Call `scipy.integrate.quad(f, 0, np.inf)`.
    - C. Manually perform a change of variables and then use `quad`.
    - D. Use `numpy.sum(f(x))` where x is a large array.

    ??? info "See Answer"
        **Correct: B**

        *(The `scipy.integrate.quad` function is designed to handle infinite limits directly and robustly by applying appropriate transformations internally. This is the most reliable and straightforward method.)*

---

!!! note "Quiz"
    **24. The error of Simpson's rule is proportional to which derivative of the function?**

    - A. The second derivative, $f''(x)$.
    - B. The third derivative, $f'''(x)$.
    - C. The fourth derivative, $f^{(4)}(x)$.
    - D. The fifth derivative, $f^{(5)}(x)$.

    ??? info "See Answer"
        **Correct: C**

        *(The local error for Simpson's rule is $-\frac{h^5}{90} f^{(4)}(\xi)$. The method is exact for cubic polynomials (whose fourth derivatives are zero), which is why it achieves the surprisingly high $O(h^4)$ global accuracy.)*

---

!!! note "Quiz"
    **25. When comparing Monte Carlo to Simpson's rule on a 1D integral, the log-log error plot for Monte Carlo will be:**

    - A. A steep, smooth line with a slope of -4.
    - B. A shallow, noisy line with an average slope of -0.5.
    - C. A flat horizontal line.
    - D. A steep, noisy line with an average slope of -2.

    ??? info "See Answer"
        **Correct: B**

        *(The error for Monte Carlo scales as $O(N^{-0.5})$, which corresponds to a slope of -0.5 on a log-log plot of error vs. N. The line is noisy because of the stochastic (random) nature of the sampling.)*
