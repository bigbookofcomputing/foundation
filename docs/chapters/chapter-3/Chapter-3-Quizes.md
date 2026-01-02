# **Chapter-3: Quizes**

---

!!! note "Quiz"
    **1. In the context of physics, what does finding a "root" of a function $f(x)=0$ often represent?**

    - A. The maximum value of the function.
    - B. A point of physical equilibrium, a stable state, or a quantized energy level.
    - C. The rate of change of the function.
    - D. A point of computational instability.

    ??? info "See Answer"
        **Correct: B**

        *(A root signifies a state of balance or a special condition, such as zero net force in equilibrium, a stable Lagrange point in orbit, or an allowed energy level in a quantum well.)*

---

!!! note "Quiz"
    **2. What is the core guarantee provided by the Intermediate Value Theorem for the Bisection Method?**

    - A. It guarantees that the root is found in a single step.
    - B. It guarantees that if a continuous function changes sign in an interval $[a, b]$, a root must exist within that interval.
    - C. It guarantees that the Bisection Method is the fastest algorithm.
    - D. It guarantees that the function has no derivative.

    ??? info "See Answer"
        **Correct: B**

        *(The Bisection Method's reliability is built on this theorem, which ensures a root is present as long as it is bracketed by points with opposite signs.)*

---

!!! note "Quiz"
    **3. What is the primary advantage of the Bisection Method?**

    - A. It has quadratic convergence.
    - B. It is extremely reliable and guaranteed to converge if the root is bracketed.
    - C. It does not require any initial guesses.
    - D. It works best for functions with many discontinuities.

    ??? info "See Answer"
        **Correct: B**

        *(Its main strength is its robustness. While slow (linear convergence), it is a fail-safe method for finding a root within a known bracket.)*

---

!!! note "Quiz"
    **4. The Newton-Raphson method uses which piece of information to find the root faster than Bisection?**

    - A. The function's value at three different points.
    - B. The function's second derivative.
    - C. The function's integral.
    - D. The function's first derivative (the slope of the tangent line).

    ??? info "See Answer"
        **Correct: D**

        *(Newton's method follows the tangent line at the current guess to find the x-intercept, using the derivative to guide its path directly toward the root.)*

---

!!! note "Quiz"
    **5. What is the convergence rate of the Newton-Raphson method?**

    - A. Linear
    - B. Superlinear
    - C. Quadratic
    - D. Logarithmic

    ??? info "See Answer"
        **Correct: C**

        *(When close to the root, the number of correct significant figures roughly doubles with each iteration, making it exceptionally fast.)*

---

!!! note "Quiz"
    **6. Under which condition is the Newton-Raphson method most likely to fail catastrophically?**

    - A. When the function is very steep.
    - B. When the initial guess is very close to the root.
    - C. When the derivative at the current guess is close to zero ($f'(x_n) \approx 0$).
    - D. When the function is perfectly linear.

    ??? info "See Answer"
        **Correct: C**

        *(If the tangent line is nearly horizontal, its x-intercept will be extremely far away, causing the next guess to "shoot off" and the method to diverge.)*

---

!!! note "Quiz"
    **7. How does the Secant Method approximate the derivative used in Newton's method?**

    - A. It uses a pre-computed table of derivatives.
    - B. It uses the slope of the line connecting the two most recent iterative guesses.
    - C. It assumes the derivative is always 1.
    - D. It uses the second derivative of the function.

    ??? info "See Answer"
        **Correct: B**

        *(The Secant Method replaces the analytical derivative with a finite difference approximation based on the last two points, making it a "derivative-free" Newton variant.)*

---

!!! note "Quiz"
    **8. The convergence rate of the Secant Method is approximately 1.618, which is known as:**

    - A. Linear convergence
    - B. Quadratic convergence
    - C. Superlinear convergence
    - D. Cubic convergence

    ??? info "See Answer"
        **Correct: C**

        *(Its speed is faster than linear (Bisection) but slightly slower than quadratic (Newton), making it a very practical and efficient compromise.)*

---

!!! note "Quiz"
    **9. Why is checking for `f(x) == 0` a poor stopping criterion for a root-finding algorithm?**

    - A. Because it is computationally too expensive.
    - B. Because due to floating-point precision, the algorithm might step over the exact root without ever landing on it, causing an infinite loop.
    - C. Because it only works for the Bisection method.
    - D. Because the function might be flat near the root.

    ??? info "See Answer"
        **Correct: B**

        *(The discrete nature of floating-point numbers means the true root may lie in a "gap" between representable numbers, so an exact zero might never be found.)*

---

!!! note "Quiz"
    **10. What is the "flat function trap" when using `abs(f(x)) < tol` as a stopping criterion?**

    - A. The algorithm stops because the function becomes perfectly horizontal.
    - B. If a function is very flat near a root, `f(x)` can be very small even when `x` is still far from the true root, causing premature convergence.
    - C. The algorithm will enter an infinite loop.
    - D. This criterion only works for steep functions.

    ??? info "See Answer"
        **Correct: B**

        *(A small function value does not guarantee a small error in x, especially when the function's slope is close to zero.)*

---

!!! note "Quiz"
    **11. What is the most robust stopping criterion for a professional root-finding solver?**

    - A. Stop when the function value is exactly zero.
    - B. Stop after a fixed number of iterations.
    - C. Stop when the change in the root estimate, $|x_n - x_{n-1}|$, is smaller than a combined absolute and relative tolerance.
    - D. Stop when the derivative of the function becomes negative.

    ??? info "See Answer"
        **Correct: C**

        *(This criterion, $|x_n - x_{n-1}| \le tol_{abs} + tol_{rel} \cdot |x_n|$, directly measures the refinement of the root and is robust for roots of any magnitude.)*

---

!!! note "Quiz"
    **12. In the context of the finite square well problem, what does a "transcendental equation" refer to?**

    - A. An equation that can be solved with simple algebra.
    - B. An equation that mixes algebraic terms (like $k$) with non-algebraic terms (like $\tan(k)$).
    - C. An equation that has no real roots.
    - D. An equation that only appears in classical mechanics.

    ??? info "See Answer"
        **Correct: B**

        *(These equations cannot be solved analytically and require numerical root-finding methods to determine the allowed energy levels.)*

---

!!! note "Quiz"
    **13. What is the first and most critical step in developing a computational strategy for the finite square well problem?**

    - A. Immediately implementing the Newton-Raphson method.
    - B. Plotting the function to visualize the roots and identify potential hazards like asymptotes.
    - C. Calculating the derivative of the transcendental equation.
    - D. Using the Bisection method with a very large initial bracket.

    ??? info "See Answer"
        **Correct: B**

        *(Plotting reveals the approximate locations of the roots and, more importantly, the dangerous regions (asymptotes) that could cause fast but unstable methods to fail.)*

---

!!! note "Quiz"
    **14. Why is a "hybrid" root-finding strategy often the best approach for the finite square well problem?**

    - A. It is the only method that works for transcendental equations.
    - B. It combines the safety of the Bisection method to find a safe bracket with the speed of the Secant or Brent's method to converge quickly.
    - C. It uses both the even and odd state equations simultaneously.
    - D. It requires fewer initial guesses than other methods.

    ??? info "See Answer"
        **Correct: B**

        *(The hybrid approach starts slow and safe (Bisection) to avoid instabilities and then switches to a fast method (Secant/Brent) for efficient convergence, giving the best of both worlds.)*

---

!!! note "Quiz"
    **15. Which of the three main root-finding methods requires two initial guesses that must bracket the root?**

    - A. Newton-Raphson Method
    - B. Secant Method
    - C. Bisection Method
    - D. All of the above.

    ??? info "See Answer"
        **Correct: C**

        *(The Bisection Method is the only one that strictly requires the initial guesses $a$ and $b$ to have $f(a) \cdot f(b) < 0$, which guarantees convergence.)*

---

!!! note "Quiz"
    **16. The Secant method requires two initial guesses, but unlike Bisection, they do not need to:**

    - A. Be floating-point numbers.
    - B. Be different from each other.
    - C. Bracket the root (have opposite signs of $f(x)$).
    - D. Be close to the actual root.

    ??? info "See Answer"
        **Correct: C**

        *(The Secant method uses the two points to compute an initial slope, but there is no requirement that the root must lie between them.)*

---

!!! note "Quiz"
    **17. If a root-finding algorithm is exhibiting "linear convergence," what does this mean?**

    - A. The number of correct digits doubles with each iteration.
    - B. The error is reduced by a constant factor at each step.
    - C. The algorithm is guaranteed to find the root in a single step.
    - D. The algorithm is unstable and will diverge.

    ??? info "See Answer"
        **Correct: B**

        *(Linear convergence, characteristic of the Bisection Method, means the error decreases at a steady, predictable, but relatively slow rate. For Bisection, this factor is 0.5.)*

---

!!! note "Quiz"
    **18. A key disadvantage of the Newton-Raphson method, besides its potential for instability, is that it:**

    - A. Is slower than the Bisection method.
    - B. Requires the analytical derivative $f'(x)$ to be known and implemented, which can be complex or error-prone.
    - C. Only works for polynomial functions.
    - D. Cannot find roots of transcendental equations.

    ??? info "See Answer"
        **Correct: B**

        *(The need to manually derive and code the derivative is a significant practical drawback, which the Secant method is designed to overcome.)*

---

!!! note "Quiz"
    **19. What physical quantity is found by solving the transcendental equation for the finite potential well?**

    - A. The position of the particle.
    - B. The velocity of the particle.
    - C. The allowed, discrete energy levels of the particle.
    - D. The depth of the potential well.

    ??? info "See Answer"
        **Correct: C**

        *(The roots of the transcendental equation correspond to the quantized wave numbers (k), which in turn give the discrete energy eigenvalues (E) for the bound states.)*

---

!!! note "Quiz"
    **20. If you are solving for a root near x=0, which type of tolerance is most important in your stopping criterion?**

    - A. Relative tolerance ($tol_{rel}$)
    - B. Absolute tolerance ($tol_{abs}$)
    - C. Neither, you should check if $f(x)$ is small.
    - D. Both are equally important in all cases.

    ??? info "See Answer"
        **Correct: B**

        *(For roots near zero, the relative tolerance term $tol_{rel} \cdot |x_n|$ becomes very small, so the absolute tolerance provides a fixed floor for the step size, ensuring the loop terminates correctly.)*

---

!!! note "Quiz"
    **21. The iterative formula for the Newton-Raphson method is:**

    - A. $x_{n+1} = x_n + \frac{f(x_n)}{f'(x_n)}$
    - B. $x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}$
    - C. $x_{n+1} = \frac{a+b}{2}$
    - D. $x_{n+1} = x_n - f(x_n) \left[ \frac{x_n - x_{n-1}}{f(x_n) - f(x_{n-1})} \right]$

    ??? info "See Answer"
        **Correct: B**

        *(This formula defines the next guess as the x-intercept of the tangent line at the current guess.)*

---

!!! note "Quiz"
    **22. The iterative formula for the Secant method is:**

    - A. $x_{n+1} = x_n + \frac{f(x_n)}{f'(x_n)}$
    - B. $x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}$
    - C. $x_{n+1} = \frac{a+b}{2}$
    - D. $x_{n+1} = x_n - f(x_n) \left[ \frac{x_n - x_{n-1}}{f(x_n) - f(x_{n-1})} \right]$

    ??? info "See Answer"
        **Correct: D**

        *(This is the Newton formula with the derivative $f'(x_n)$ replaced by its finite-difference approximation.)*

---

!!! note "Quiz"
    **23. Which method is considered a "derivative-free" alternative to Newton-Raphson?**

    - A. Bisection Method
    - B. Secant Method
    - C. Brent's Method
    - D. Both B and C

    ??? info "See Answer"
        **Correct: D**

        *(The Secant method is the direct derivative-free analogue. Brent's method is a more complex hybrid that also avoids derivatives by combining Bisection, Secant, and inverse quadratic interpolation.)*

---

!!! note "Quiz"
    **24. In the Lagrange point visualization project, what is the purpose of plotting the force function $F(r)$?**

    - A. To calculate the exact value of the root.
    - B. To visually identify and bracket the location where the net force is zero.
    - C. To determine the mass of the Sun.
    - D. To test the convergence rate of the Secant method.

    ??? info "See Answer"
        **Correct: B**

        *(The plot provides a "map" of the problem, showing where the root lies and providing a safe starting bracket for a numerical solver, which is a critical first step.)*

---

!!! note "Quiz"
    **25. A "hybrid" root-finding algorithm like Brent's method is popular in professional libraries because it:**

    - A. Is simpler to implement than the Bisection method.
    - B. Always converges quadratically, making it the fastest option.
    - C. Combines the guaranteed convergence of a bracketing method (like Bisection) with the speed of a faster method (like Secant).
    - D. Requires only one initial guess.

    ??? info "See Answer"
        **Correct: C**

        *(Hybrid methods offer the best of both worlds: the reliability of bracketing and the speed of open methods, making them robust and efficient for general-purpose use.)*


