

## 3.1 The Physics of “Zero” {.heading-with-pill}
> **Concept:** Root-Finding as the Foundation of Physical Modeling • **Difficulty:** ★★☆☆☆

> **Summary:** This chapter introduces numerical root-finding—Bisection, Newton-Raphson, and Secant methods—emphasizing visualization, bracketing, convergence criteria, and hybrid strategies that balance reliability and efficiency.

---

### Theoretical Background

Having constructed our **digital lab** (Chapter 1) and explored the **limits of floating-point arithmetic** (Chapter 2), we are now ready to confront the first truly intelligent algorithmic problem: finding where a function equals zero.  

In physics, this deceptively simple question—**when does $f(x)=0$?**—appears everywhere.

* **Classical Mechanics (Equilibrium):**  
  An object is in equilibrium when the **net force** acting on it is zero:  

$$
  F(x)=0.
$$

  Solving for equilibrium positions therefore means finding the **roots** of $F(x)$.

* **Orbital Dynamics (Lagrange Points):**  
  At special points between two massive bodies, the gravitational and centrifugal forces cancel perfectly. The equilibrium position satisfies 

$$
  F_{\text{total}}(r)=0.
$$

* **Quantum Mechanics (Bound States):**  
  The discrete energy levels $E_n$ of an electron in a potential well satisfy transcendental equations—nonlinear mixtures of algebraic and trigonometric terms—such as  

$$
  f(E)=\tan(E)-\sqrt{\frac{\alpha^2}{E^2}-1}=0.
$$

In each case, there is no closed-form algebraic solution. The equations are **nonlinear** and **transcendental**, requiring **numerical hunting** rather than symbolic solving. The unknown value $x$ that satisfies $f(x)=0$ is called the **root** of the function.

---

### The Numerical Challenge

Unlike algebraic manipulation, root finding is **iterative exploration**. We begin with one or more *guesses* or *brackets* and refine them through successive evaluations of $f(x)$ until we locate where the function crosses zero.  

This chapter presents three foundational algorithms:

1. **Bisection Method** — slow but absolutely reliable.  
2. **Newton–Raphson Method** — fast but can diverge catastrophically.  
3. **Secant Method** — a pragmatic compromise using only function evaluations.  

Each method trades reliability for speed in a delicate balance that every computational physicist must master.

---

### Comprehension Check

!!! note "Quiz"
    **1. Why is root finding considered a fundamental operation in physics?**

    - A. Because physical laws are mostly linear.  
    - B. Because $f(x)=2x-4$ is easy to solve.  
    - C. Because many physical phenomena—equilibria, energy levels, orbital balances—reduce to solving $f(x)=0$.  
    - D. Because Fourier analysis requires it.  

    ??? info "See Answer"
        **Correct: C**  
        Root finding unifies diverse physical problems under a single numerical framework.

---

!!! note "Quiz"
    **2. What do we call an equation combining algebraic and non-algebraic functions (e.g., $\tan x$, $\sin x$)?**

    - A. Polynomial equation  
    - B. Quadratic equation  
    - C. Linear equation  
    - D. Transcendental equation  

    ??? info "See Answer"
        **Correct: D**  
        Transcendental equations cannot be solved exactly with algebraic manipulation and demand numerical methods.

---

!!! abstract "Interview-Style Question"

    **Q:** Define a *root-finding problem* in your own words. Provide two distinct physical examples from the text where such methods are essential.

    ???+ info "Answer Strategy"
        A root-finding problem seeks the value of $x$ for which $f(x)=0$ when the equation cannot be solved analytically.  
        **Examples:**
        1. **Equilibrium condition:** solving $F(x)=0$ in mechanics to find where forces cancel.  
        2. **Quantum bound states:** solving $f(E)=0$ for allowed energies in a finite potential well.

---

### <i class="fa-solid fa-flask"></i> Hands-On Project

#### **Project:** Visualizing the Lagrange-Point Root

---

#### **Project Blueprint**

| **Section**              | **Description**                                                                                                                                                                                                                 |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Objective**            | To visualize and roughly bracket the root corresponding to the $L_1$ Lagrange point in the Sun–Earth system.                                                                                                                    |
| **Mathematical Concept** | The location where the gravitational and centrifugal forces cancel satisfies $F(r)=0$. Numerical algorithms can then refine this bracket to high precision.                                                                    |
| **Experiment Setup**     | Define $F(r)$ as the net force on a test mass along the line joining Earth and Sun. Use known constants: gravitational constant $G$, masses $M_{\odot}$ and $M_{\oplus}$, and orbital angular velocity $\omega$.                 |
| **Process Steps**        | 1. Implement $F(r)$ in Python. <br> 2. Plot $F(r)$ from Earth’s surface outward toward the Sun. <br> 3. Observe where the curve crosses zero. <br> 4. Record the approximate bracket $[a,b]$ around this crossing.                |
| **Expected Behavior**    | The plot should show one clear zero crossing between Earth and the Sun. This visually identifies a reliable bracket for subsequent algorithms (e.g., Bisection or Secant).                                                     |
| **Tracking Variables**   | - $r$: distance from Earth <br> - $F(r)$: net force per unit mass <br> - $a,b$: lower and upper bracket boundaries <br> - graphical zero crossing point                                   |
| **Verification Goal**    | Confirm visually that $F(r)$ changes sign within $[a,b]$. This ensures a guaranteed root by the Intermediate Value Theorem.                                                              |
| **Output**               | A Matplotlib plot showing $F(r)$ vs. $r$ with the zero crossing highlighted, plus printed approximate bracket coordinates.                                                                |

---

#### **Pseudocode Implementation**

```pseudo-code

BEGIN

// 1. Import libraries
IMPORT numpy AS np
IMPORT matplotlib.pyplot AS plt

// 2. Define constants (example values)
SET G = 6.674e-11
SET M_sun = 1.989e30
SET M_earth = 5.972e24
SET d = 1.496e11      // distance between Sun and Earth
SET omega = np.sqrt(G*(M_sun + M_earth) / d**3)

// 3. Define force function along line between bodies
DEFINE F(r):
RETURN G*M_sun/(r**2) - G*M_earth/((d - r)**2) - omega**2 * r

// 4. Create array of r values between Earth and Sun
r_values = np.linspace(1e9, d - 1e9, 1000)
F_values = F(r_values)

// 5. Plot and identify bracket
PLOT r_values, F_values
DRAW horizontal line at y=0
LABEL axes ("r (m)", "F(r) [m/s^2]")
SHOW plot

// 6. Observe approximate bracket [a, b]
PRINT "Approximate sign change interval:", a, b

END

```

---

#### **Outcome and Interpretation**

* The plot will display $F(r)$ crossing zero once between Earth and Sun.  
* This **graphical bracketing** step is the first and most critical phase of any root-finding procedure—without it, even advanced algorithms can fail.  
* Establishing a valid bracket transforms an unknown numerical hunt into a guaranteed, convergent search.  
* With this groundwork, the next section develops the **Bisection Method**, our first robust root-solving algorithm.



<div class="section-divider"></div>

## 3.3 The “Calculus” Method: Newton–Raphson {.heading-with-pill}
> **Concept:** Tangent-Based Iterative Root Refinement • **Difficulty:** ★★★☆☆

> **Summary:** The Newton–Raphson method leverages the function’s derivative to trace tangent lines toward the root, achieving **quadratic convergence**. However, it requires an analytic derivative and can fail dramatically when the initial guess is poor or the derivative approaches zero.

---

### Theoretical Background

The **Bisection Method** was simple but blind—it ignored how the function curves. The **Newton–Raphson Method** (or simply *Newton’s Method*) introduces intelligence through **calculus**, using the slope of the function itself to guide each step directly toward the root.

Imagine an expert skier descending a curved slope toward the valley floor at $f(x)=0$:

1. Starts at a current position $x_n$.  
2. Observes the local slope, given by the **derivative** $f'(x_n)$.  
3. Follows the tangent line defined by that slope until it intersects the x-axis.  
4. Lands on the next guess, $x_{n+1}$, closer to the root.

This geometric interpretation turns calculus into an efficient navigation tool for zero-finding.

---

### The Algorithm (Derivation)

The Newton–Raphson iteration arises directly from the equation of the tangent line at $x_n$:

$$
  y = f'(x_n)(x - x_n) + f(x_n)
$$

To locate where this tangent crosses the x-axis, set $y = 0$ and solve for $x$:

$$
  0 = f'(x_n)(x_{n+1} - x_n) + f(x_n)
$$

Rearranging yields the iterative update formula:

$$
  \mathbf{x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}}
$$

This formula expresses each new approximation as the previous guess minus a correction term proportional to the function value and inversely proportional to its slope.

---

### Performance: Quadratic Convergence

Newton’s method is renowned for its **quadratic convergence**—once close to the root, the number of correct digits roughly **doubles with each iteration**.  

This exponential speed makes it the go-to method in scientific computing, provided the derivative is known and the initial guess is reasonable.

| | Pros | Cons |
| :--- | :--- | :--- |
| **Newton–Raphson** | **Extremely Fast:** Quadratic convergence. **Elegant:** Exploits local slope for direction. | **Unstable:** Diverges if $f'(x_n) \approx 0$ or the guess is far off. **Requires $f'(x)$:** The analytic derivative must be available and implemented correctly. |

---

### Comprehension Check

!!! note "Quiz"
    **1. What is the main advantage of the Newton–Raphson method over the Bisection method?**

    - A. It is guaranteed to find a root, regardless of the initial guess.  
    - B. It has *quadratic convergence*, meaning the number of correct digits roughly doubles with each iteration.  
    - C. It does not require derivative information.  
    - D. It performs best for discontinuous functions.  

    ??? info "See Answer"
        **Correct: B**  
        Near the root, each iteration rapidly improves accuracy, making Newton–Raphson much faster than Bisection.

---

!!! note "Quiz"
    **2. The essential operational requirement for the Newton–Raphson method is:**

    - A. Two initial guesses that bracket the root.  
    - B. A polynomial form of the function.  
    - C. An analytic expression for the derivative $f'(x)$.  
    - D. A damping factor to stabilize the updates.  

    ??? info "See Answer"
        **Correct: C**  
        Without $f'(x)$, the tangent cannot be computed, and the method’s core mechanism breaks down.

---

!!! abstract "Interview-Style Question"

    **Q:** Describe two distinct scenarios where the Newton–Raphson method can fail catastrophically, and explain the mathematical cause of each.

    ???+ info "Answer Strategy"
        1. **Flat Slope Divergence:**  
           If the current guess lies near a local extremum (where $f'(x_n) \approx 0$), the tangent line becomes nearly horizontal.  
           The correction term  
           $$
             -\frac{f(x_n)}{f'(x_n)}
           $$  
           becomes enormous, sending $x_{n+1}$ far from the root and causing **divergence**.

        2. **Poor Initial Guess:**  
           Starting too far from the root can cause the tangent to cross the x-axis in the wrong region or jump into oscillation between distant points, preventing convergence.

---

### <i class="fa-solid fa-flask"></i> Hands-On Project

#### **Project:** Visualizing and Comparing Convergence Rates

---

#### **Project Blueprint**

| **Section**              | **Description**                                                                                                                                                                                                                  |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Objective**            | To implement and compare the convergence behavior of the **Bisection Method** and **Newton–Raphson Method** for the same function.                                                                                              |
| **Mathematical Concept** | Quadratic convergence in Newton–Raphson vs. linear convergence in Bisection. The difference in slope on a $\log_{10}(\text{Error})$ vs. iteration plot directly visualizes convergence order.                                   |
| **Function Chosen**      | $f(x) = x^2 - 2$, with true root $x = \sqrt{2} \approx 1.41421356237$.                                                                                                                    |
| **Experiment Setup**     | Implement both solvers with tolerance $\varepsilon = 10^{-10}$. For each iteration $n$, record the absolute error $|x_n - \sqrt{2}|$.                                                     |
| **Process Steps**        | 1. Implement both algorithms. <br> 2. Run both using initial guesses $x_0=1$ (Newton) and $[1,2]$ (Bisection). <br> 3. Store iteration count and error. <br> 4. Plot $\log_{10}(\text{Error})$ vs. $n$.                          |
| **Expected Behavior**    | The Bisection line decreases linearly with $n$; Newton–Raphson drops exponentially once near the root, showing quadratic convergence.                                                      |
| **Tracking Variables**   | - $x_n$: current estimate <br> - $f(x_n)$, $f'(x_n)$ <br> - $\text{error}_n = |x_n - \sqrt{2}|$ <br> - iteration count                                                                  |
| **Verification Goal**    | Confirm that Newton–Raphson reaches machine precision in far fewer steps than Bisection, illustrating convergence rate differences.                                                       |
| **Output**               | Plot of $\log_{10}(\text{Error})$ vs. iteration count comparing both methods, printed final errors, and iteration totals.                                                                 |

---

#### **Pseudocode Implementation**

```pseudo-code
BEGIN

// Define function and derivative
DEFINE f(x):
    RETURN x**2 - 2

DEFINE f_prime(x):
    RETURN 2*x

// 1. Newton-Raphson Method
SET x = 1.0
SET tol = 1e-10
SET n = 0

PRINT "Iteration | x_n | f(x_n) | Error"

WHILE ABS(f(x)) > tol DO
    n = n + 1
    x_new = x - f(x)/f_prime(x)
    error = ABS(x_new - sqrt(2))
    PRINT n, x, f(x), error
    x = x_new
END WHILE

PRINT "Final Root (Newton):", x
PRINT "Iterations:", n

// 2. Bisection Method (for comparison)
SET a = 1.0
SET b = 2.0
SET n_bis = 0

WHILE (b - a) > tol DO
    n_bis = n_bis + 1
    c = (a + b) / 2
    IF f(a) * f(c) < 0 THEN
        b = c
    ELSE
        a = c
    END IF
END WHILE

PRINT "Final Root (Bisection):", (a + b)/2
PRINT "Iterations:", n_bis

// 3. Plot log10(Error) vs Iteration for both methods
PLOT error_curves

END
```

---

#### **Outcome and Interpretation**

* The **Bisection Method** converges linearly—each step halves the error.
* The **Newton–Raphson Method** converges quadratically—error magnitude squares with each iteration.
* The plot of $\log_{10}(\text{Error})$ vs. iteration clearly shows the Newton curve dropping far faster.
* This experiment illustrates the dramatic efficiency of calculus-based convergence—**speed at the cost of stability**.



<div class="section-divider"></div>



## 3.4 The “Practical” Method: The Secant Method {.heading-with-pill}
> **Concept:** Derivative-Free Tangent Approximation for Root Finding • **Difficulty:** ★★★☆☆

> **Summary:** The Secant Method is a **practical, derivative-free** root-finding algorithm that replaces the analytical derivative with a finite-difference slope between two recent iterates, achieving **superlinear convergence** as a compromise between Newton’s speed and Bisection’s robustness.

---

### **Theoretical Background**

The **Secant Method** stands as a bridge between **Newton–Raphson** and **Bisection**, combining Newton’s speed with the simplicity of Bisection’s derivative-free operation. It trades analytical elegance for **practical reliability**, relying on function values rather than symbolic differentiation.

Unlike Newton’s method, which demands the explicit derivative $f'(x)$, the Secant method constructs an **approximate slope** from the last two function evaluations—forming what’s known as a **secant line**.

---

### **The Theory: Approximating the Slope**

Instead of evaluating the true derivative, the Secant Method approximates it using two successive points, $x_{n-1}$ and $x_n$:

$$
    f'(x_n) \approx \frac{f(x_n) - f(x_{n-1})}{x_n - x_{n-1}}
$$

This simple substitution turns the calculus-based Newton iteration into a purely numerical one. The tangent becomes an interpolated line segment, capturing the local slope trend.

!!! tip "Intuition Boost"
    The Secant line “remembers” the last step’s direction—like using two footprints to guess the trail’s slope—allowing progress without formal differentiation.

---

### **The Algorithm (Derivation)**

Starting from Newton’s update rule,

$$
    x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}
$$

we replace $f'(x_n)$ with its finite-difference approximation. Simplifying yields the **Secant iteration formula**:

$$
    \mathbf{x_{n+1} = x_n - f(x_n) \left[ \frac{x_n - x_{n-1}}{f(x_n) - f(x_{n-1})} \right]}
$$

This requires **two initial guesses**, $x_0$ and $x_1$, to compute the first secant line.

---

### **Performance: Superlinear Convergence**

The Secant method achieves **superlinear convergence**, faster than linear (Bisection) but slightly slower than Newton’s quadratic rate. The effective rate is approximately:

$$
    \phi \approx 1.618
$$

—coincidentally, the **Golden Ratio**, symbolizing the method’s elegant balance between stability and speed.

| | Pros | Cons |
| :--- | :--- | :--- |
| **Secant Method** | **Practical:** Requires no analytical derivative $f'(x)$. **Efficient:** Converges superlinearly (rate $\approx 1.618$). | **Unstable:** May diverge or oscillate if initial guesses are poor. **Two Guesses Needed:** Needs $x_0$ and $x_1$ to start. |

---

### **Comprehension Check**

!!! note "Quiz"
    **1. How does the Secant Method avoid calculating the analytical derivative $f'(x)$?**

    - A. By checking for sign changes between iterations.  
    - B. By approximating the slope using two recent points ($x_{n-1}$, $x_n$).  
    - C. By requiring manual derivative input.  
    - D. By assuming $f'(x)=1$ near the root.  

    ??? info "See Answer"
        **Correct: B**  
        The method estimates $f'(x)$ using a finite-difference slope, forming a secant line between consecutive iterates.

-----

!!! note "Quiz"
    **2. The convergence rate of the Secant method (≈1.618) is classified as:**

    - A. Linear  
    - B. Quadratic  
    - C. Superlinear  
    - D. Logarithmic  

    ??? info "See Answer"
        **Correct: C**  
        Its convergence lies between linear and quadratic—superlinear with an order near the Golden Ratio.

-----

!!! abstract "Interview-Style Question"

    **Q:** Why is the Secant method often preferred over Newton–Raphson in real-world engineering applications, despite Newton’s superior speed?

    ???+ info "Answer Strategy"
        **Practicality dominates precision.**  
        - Newton’s method requires deriving and coding $f'(x)$, which can be error-prone for complex functions.  
        - The Secant method eliminates that risk by numerically estimating the slope from previous points.  
        - This makes it **safer, easier to implement**, and less susceptible to human error in large-scale simulations.

---

### <i class="fa-solid fa-flask"></i> Hands-On Project

#### **Project:** Comparing Function Call Efficiency — Secant vs. Newton

---

#### **Project Blueprint**

| **Section**              | **Description**                                                                                                                                                                                                                     |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Objective**            | To compare the efficiency (in terms of function evaluations) between the Newton–Raphson and Secant methods for the same function.                                                                                                  |
| **Mathematical Concept** | Both methods approximate the root by following local slope information, but Secant replaces the analytical derivative $f'(x)$ with a finite-difference estimate between successive points.                                          |
| **Experiment Setup**     | Test function: $f(x) = e^x - 2$. Implement both algorithms with the same convergence tolerance ($\varepsilon = 10^{-8}$). Add counters to track total $f(x)$ evaluations.                                                          |
| **Process Steps**        | 1. Implement both methods. <br> 2. Initialize $x_0=0$, $x_1=1$ for Secant, and $x_0=1$ for Newton. <br> 3. Run until $|f(x_n)|<\varepsilon$. <br> 4. Record total $f(x)$ calls for each method.                                    |
| **Expected Behavior**    | Newton converges in fewer iterations, but the Secant’s derivative-free approach may require similar or fewer total $f(x)$ calls when the derivative is computationally expensive.                                                   |
| **Tracking Variables**   | - $x_n$, $x_{n-1}$ (iteration values) <br> - $f(x_n)$, $f(x_{n-1})$ <br> - $f$-call counters <br> - iteration count                                                                          |
| **Verification Goal**    | Quantify efficiency by comparing function-call counts while verifying identical root accuracy ($x \approx \ln 2$).                                                                           |
| **Output**               | Final root estimates for both methods, number of iterations, and total $f(x)$ calls printed in a formatted summary table.                                                                   |

---

#### **Pseudocode Implementation**

```pseudo-code
BEGIN

// Define function
DEFINE f(x):
    RETURN exp(x) - 2

// Initialize Secant Method
SET x0 = 0
SET x1 = 1
SET tol = 1e-8
SET f_calls = 0
SET iter = 0

PRINT "Iter | x_n | f(x_n)"

WHILE ABS(f(x1)) > tol DO
    iter = iter + 1
    f_calls = f_calls + 1
    x2 = x1 - f(x1)*(x1 - x0)/(f(x1) - f(x0))
    PRINT iter, x1, f(x1)
    x0 = x1
    x1 = x2
END WHILE

PRINT "Secant Root:", x1
PRINT "Total f(x) calls:", f_calls

END
```

---

#### **Outcome and Interpretation**

* The **Secant Method** typically converges in 5–7 iterations for $f(x) = e^x - 2$, close to the Newton–Raphson method.
* Function-call counting reveals that although Newton uses fewer steps, it also calls both $f(x)$ and $f'(x)$ per iteration—doubling computation in complex models.
* The Secant method’s ability to approximate derivatives numerically makes it **the practical choice** for large-scale systems or symbolic-derivative-resistant problems.

---

!!! example "Historical Note: Early Numerical Astronomy"
    Astronomers used secant-style interpolation long before digital computing—tracing planetary orbits with line-based slope approximations centuries before Newton formalized calculus.




<div class="section-divider"></div>



## 3.5 The “Safety Manual”: When Are We “Done”? {.heading-with-pill}
> **Concept:** Defining Reliable Stopping Criteria for Iterative Solvers • **Difficulty:** ★★★☆☆

> **Summary:** A robust solver halts when the **step size** between consecutive iterations satisfies  
> $|x_n - x_{n-1}| \le tol_{\text{abs}} + tol_{\text{rel}} \cdot |x_n|$, ensuring scale-aware, stable convergence for all magnitudes of roots.

---

### **Theoretical Background**

Having mastered the Newton–Raphson and Secant methods, we now face the subtle but vital question: **when should we stop iterating?**  
This is not a trivial detail—it determines whether our algorithm produces a **trustworthy result** or silently diverges.

We now possess two high-speed iterative algorithms generating a sequence of approximations:


$$
    x_0, x_1, x_2, \dots
$$

### **The Problem with $f(x) = 0$ (Chapter 2 Connection)**

Your first instinct might be to stop when $f(x)$ equals zero.  
That’s a **critical mistake**.

Due to the **gappy ruler** of floating-point arithmetic (recall Chapter 2), the true root may lie between representable numbers. The sequence can “step over” it—jumping from slightly positive to slightly negative—without ever hitting an exact zero.  
If we wait for a literal $f(x) = 0$, the algorithm could **loop forever**.

!!! example "Floating-Point Gap Trap"
    Suppose the true root is between $1.00000000000001$ and $1.00000000000002$.  
    The computer cannot represent either exactly. Your solver might leap across this micro-gap infinitely, never landing exactly on zero.

---

### **The Problem with Checking $f(x)$ (The “Flat Function” Trap)**

A seemingly safer choice is to stop when $|f(x_n)|$ is very small, e.g. `abs(f(x_n)) < 1e-10`.  
This too can fail when the function is **flat** near its root.

If $f'(x)$ is small, even large deviations in $x$ might yield minuscule values of $f(x)$.  
Your solver would stop early—believing it’s converged—when it’s actually still far from the true root.

!!! tip "Intuition Boost"
    Small $f(x)$ does *not* always mean small error in $x$.  
    Flat regions can fool your solver into **false convergence**.

---

### **The “Gold Standard”: Checking the Step Size ($\Delta x$)**

A reliable algorithm measures **how much its guesses are improving**.  
The fundamental idea: when the change between successive estimates becomes insignificantly small, the root has effectively stabilized.

Define this change as:

$$
    \Delta x = |x_n - x_{n-1}|
$$

A solver that monitors $\Delta x$ directly evaluates the **refinement** of its solution—not the shape of $f(x)$.

To make this check robust across all scales of $x$, we use two tolerances:

| **Criterion** | **Formula** | **Purpose** |
| :--- | :--- | :--- |
| **Absolute Tolerance ($tol_{\text{abs}}$)** | $|x_n - x_{n-1}| \le tol_{\text{abs}}$ | Ensures convergence for roots near $x=0$. |
| **Relative Tolerance ($tol_{\text{rel}}$)** | $|x_n - x_{n-1}| \le tol_{\text{rel}} \cdot |x_n|$ | Ensures scale-aware convergence for large roots. |

Combining both ensures accuracy across all magnitudes.

---

### **The “Pro” Criterion**

Professionals use a combined stopping condition that adapts automatically to both small and large roots:

$$
    \text{Stop when } |x_{n} - x_{n-1}| \le tol_{\text{abs}} + tol_{\text{rel}} \cdot |x_n|
$$

This condition scales naturally with $|x_n|$ while guaranteeing an absolute lower bound on improvement.  
It is the **industry-standard convergence test** for iterative solvers.

!!! question "Why combine two tolerances?"
    Because real roots come in all sizes.  
    A fixed absolute tolerance works only near zero; a relative tolerance alone fails for small roots.  
    The combination adapts dynamically.

---

### **Comprehension Check**

!!! note "Quiz"
    **1. Why is using `if f(x) == 0.0` a disastrous way to stop a solver?**

    - A. Because of truncation error.  
    - B. Because flat regions may produce small $f(x)$ even far from the root.  
    - C. Because of floating-point round-off gaps, the solver may “step over” the true zero.  
    - D. Because the solver will always stop prematurely.  

    ??? info "See Answer"
        **Correct: C**  
        Floating-point gaps mean the true zero may not be representable, causing endless iteration.

-----

!!! note "Quiz"
    **2. A convergence check using a *relative tolerance* is most useful when:**  

    - A. The root is near zero.  
    - B. The root is very large (e.g., $10^{15}$).  
    - C. The derivative is exactly zero.  
    - D. The method is Bisection.  

    ??? info "See Answer"
        **Correct: B**  
        Relative tolerance scales the step to the root’s magnitude, preserving precision at large $x$.

-----

!!! abstract "Interview-Style Question"

    **Q:** Your intern used `while abs(f(x)) < 1e-10` as a stopping rule. The true root is $x = 5000$. Explain why a small absolute change in $x$ is more meaningful than a small $f(x)$.

    ???+ info "Answer Strategy"
        The size of $f(x)$ does not measure how accurate $x$ is—especially if the function is flat.  
        For $x=5000$, an absolute tolerance of $10^{-10}$ means absurd precision relative to the scale.  
        Instead, a **relative tolerance** compares $\Delta x$ to $x$ itself, ensuring a fixed number of significant digits, independent of magnitude.  
        The relative step check reflects *actual root accuracy*, while $|f(x)|$ merely indicates proximity on the y-axis.

---

### <i class="fa-solid fa-flask"></i> Hands-On Project

#### **Project:** Comparing Bad vs. Good Convergence Criteria

---

#### **Project Blueprint**

| **Section** | **Description** |
|--------------|----------------|
| **Objective** | Demonstrate the difference between naive and professional convergence checks by applying both to the same root-finding task. |
| **Mathematical Concept** | Iterative convergence is best measured through changes in $x$, not the absolute magnitude of $f(x)$. |
| **Experiment Setup** | Function: $f(x) = 10^{-6}x - 1.0$ (true root $x_{\text{true}} = 10^6$). Implement a Secant solver with two stopping rules. |
| **Criterion A (Bad)** | Stop when `abs(f(x_n)) < 1e-10`. |
| **Criterion B (Good)** | Stop when $|x_n - x_{n-1}| < 10^{-8} \cdot |x_n|$. |
| **Process Steps** | 1. Run both solvers.<br>2. Compare number of iterations.<br>3. Record the final estimate and its deviation from the true root. |
| **Expected Behavior** | Criterion A will stop quickly but yield a wrong root (large $x$-error). Criterion B will take slightly longer but produce an accurate result. |
| **Tracking Variables** | $x_n$, $x_{n-1}$, $\Delta x$, $f(x_n)$, iteration count. |
| **Verification Goal** | Show that convergence checks based on $\Delta x$ yield consistent, precision-controlled roots. |
| **Output** | A table comparing iteration count, final root, and error for both criteria. |

---

#### **Pseudocode Implementation**

```pseudo-code
BEGIN

// Define test function
DEFINE f(x):
    RETURN 1e-6 * x - 1.0

// Initialize variables
SET x0 = 0
SET x1 = 2e6
SET tol_rel = 1e-8
SET tol_abs = 1e-12
SET iter = 0

// Criterion B: Step-based stopping
WHILE ABS(x1 - x0) > (tol_abs + tol_rel * ABS(x1)) DO
    iter = iter + 1
    x2 = x1 - f(x1)*(x1 - x0)/(f(x1) - f(x0))
    x0 = x1
    x1 = x2
END WHILE

PRINT "Converged Root:", x1
PRINT "Iterations:", iter

END
```

---

#### **Outcome and Interpretation**

* Under **Criterion A (Bad)**, the solver may terminate in a handful of steps but return a wildly inaccurate root (e.g., $x=9.99\times10^5$).
* Under **Criterion B (Good)**, the solver takes a few more steps but returns $x=1.0000000\times10^6$, satisfying both absolute and relative tolerance conditions.
* The experiment confirms that **step-based convergence criteria** yield stable, precision-controlled results regardless of scale.

---

!!! tip "Professional Habit"
    Always log the final values of $x_n$, $f(x_n)$, and $\Delta x$.
    They provide essential diagnostics for solver reliability before declaring convergence.



<div class="section-divider"></div>



## 3.6 Core Application: Energy Levels in a Finite Square Well {.heading-with-pill}
> **Concept:** Hybrid Numerical Root-Finding for Quantum Bound States • **Difficulty:** ★★★★☆

> **Summary:** Plot to **bracket** the transcendental equations, use **Bisection** to safely narrow each root interval, then switch to a **fast solver** (Secant or Brent) to compute the discrete quantum energy levels of a finite potential well.

---

### **Theoretical Background**

This classic quantum mechanics problem is the **perfect demonstration** of why numerical root-finding is indispensable.  
In a **finite square potential well**, the allowed (bound) energy levels of a particle are *not arbitrary*. They arise from the **boundary conditions** of the time-independent Schrödinger equation, leading to transcendental equations that **cannot be solved algebraically**.

---

### **The Physics: Transcendental Equations**

When a particle of mass $m$ is confined in a well of finite depth $V_0$, the stationary Schrödinger equation yields two transcendental equations that govern the permitted energy eigenvalues. Defining a dimensionless wave number:

$$
    k = \frac{\sqrt{2mE}}{\hbar},
$$

and a constant $\alpha = \frac{\sqrt{2mV_0}}{\hbar}$ (related to well depth), the conditions become:

* **Even (symmetric) states:**

$$
    \tan(k) = \sqrt{\frac{\alpha^2}{k^2} - 1}
$$

* **Odd (antisymmetric) states:**

$$
    -\cot(k) = \sqrt{\frac{\alpha^2}{k^2} - 1}
$$

The right-hand side stems from the evanescent wave behavior outside the well.  
The challenge: find all $k$ that satisfy these equations.

!!! tip "Key Insight"
    The *transcendental* nature (involving both algebraic and trigonometric terms) means that symbolic solutions are impossible — numerical root-finding is the **only path** to the allowed quantum energies.

---

### **The Computational Task**

For the even states, define a single root function:

$$
    f_{\text{even}}(k) = \tan(k) - \sqrt{\frac{\alpha^2}{k^2} - 1} = 0
$$

Our goal: find the discrete values of $k$ that make $f_{\text{even}}(k) = 0$.

---

### **The Computational Strategy**

#### **1. Never “Code Blind” — Plot First**

Before solving numerically, visualize the problem.  
Plot both sides ($y=\tan(k)$ and $y=\sqrt{(\alpha^2/k^2)-1}$) to understand where intersections (roots) occur.

* The $\tan(k)$ function exhibits **vertical asymptotes** at $k = \pi/2, 3\pi/2, 5\pi/2, \dots$
* The square-root term decays smoothly with increasing $k$.

!!! example "Visual Diagnostic"
    These plots immediately reveal dangerous regions where $f'(k)$ explodes near the asymptotes.  
    Such regions can **destroy** Newton–Raphson or Secant iterations that rely on derivative behavior.

---

#### **2. Choose the Safest Tool: Bisection**

Since $f(k)$ changes sign across zero-crossings and is continuous between asymptotes, the **Bisection Method** is the only safe starting algorithm.

We can identify bracketing intervals directly from the plot:

| **State** | **Bracket $[a,b]$** | **Comment** |
|------------|--------------------|--------------|
| Ground (Even 1) | $[0, \pi/2]$ | Root near $k \approx 1.4$ |
| First Excited (Even 2) | $[\pi, 3\pi/2]$ | Root near $k \approx 4.5$ |

The Bisection method guarantees the existence of a root if $f(a)\cdot f(b) < 0$.

---

#### **3. The “Pro” Way — Hybrid Approach**

Professional solvers use a **hybrid** strategy that marries safety with speed:

* **Phase 1 — Safety:**  
  Apply **Bisection** until the interval $[a,b]$ is sufficiently small and $f(k)$ behaves smoothly.  
  Example: shrink $[0, \pi/2]$ down to $[1.0, 1.4]$.

* **Phase 2 — Speed:**  
  Switch to a **fast method** (e.g., Secant, Newton, or Brent’s method) initialized inside the safe bracket.  
  The Secant or Brent algorithms then converge rapidly without risking divergence from steep slopes.

!!! tip "Hybrid Algorithm Philosophy"
    Start **slow but safe**, then **finish fast and precise**.  
    This principle generalizes beyond quantum wells — it’s the foundation of all professional numerical solvers.

---

### **Physical Interpretation**

Each converged $k$ value corresponds to a **quantized energy level**:

$$
    E_n = \frac{\hbar^2 k_n^2}{2m}
$$

The discrete sequence of $E_n$ represents the **bound states** of the particle in the finite well.  
Higher $n$ correspond to states that oscillate more rapidly within the well and penetrate further into the barriers.

---

### **Comprehension Check**

!!! note "Quiz"
    **1. Why does the presence of $\tan(k)$ and $\cot(k)$ make the Newton–Raphson method dangerous here?**

    - A. The derivative of $\tan(k)$ is impossible to compute.  
    - B. The function is nearly linear near the roots.  
    - C. The asymptotes cause $f'(k)$ to blow up, leading to catastrophic divergence.  
    - D. Newton’s method needs two initial guesses.  

    ??? info "See Answer"
        **Correct: C**  
        Near vertical asymptotes, the derivative of $\tan(k)$ diverges.  
        Newton’s method can “jump” into an adjacent interval and diverge completely.

-----

!!! note "Quiz"
    **2. What defines the “hybrid” root-finding strategy in this context?**

    - A. Use Newton first, then switch to Bisection.  
    - B. Use Bisection to bracket safely, then switch to a fast method like Secant or Brent.  
    - C. Alternate between $\tan(k)$ and $\cot(k)$ evaluations.  
    - D. Use a tolerance that combines both absolute and relative errors.  

    ??? info "See Answer"
        **Correct: B**  
        The hybrid method uses Bisection to safely isolate the root and then applies a rapid converging solver for efficiency.

-----

!!! abstract "Interview-Style Question"

    **Q:** You’re solving $F(x)=0$ for a system where $F'(x)$ is nearly zero near the root. Why might Newton–Raphson fail, and what alternative ensures convergence?

    ???+ info "Answer Strategy"
        When $F'(x) \approx 0$, the Newton update step  
        $x_{n+1} = x_n - F(x_n)/F'(x_n)$  
        becomes unstable due to division by a near-zero value, producing large, erratic jumps.  
        The **Bisection method**, by relying solely on sign changes, remains stable and convergent regardless of derivative behavior.  
        Therefore, a **hybrid** approach starting with Bisection is the professional solution.

---

### <i class="fa-solid fa-flask"></i> Hands-On Project

#### **Project:** Finding Odd-State Energy Levels via Hybrid Root Finding

---

#### **Project Blueprint**

| **Section** | **Description** |
|--------------|----------------|
| **Objective** | Compute the odd-parity quantum energy levels in a finite square well using hybrid root-finding. |
| **Mathematical Concept** | The transcendental equation $f_{\text{odd}}(k)=\cot(k)+\sqrt{\frac{\alpha^2}{k^2}-1}=0$ defines the allowed $k$ for antisymmetric bound states. |
| **Experiment Setup** | Constants: $\hbar=1$, $m=1$, $\alpha=5$. Use `scipy.optimize.brentq` to find roots of $f_{\text{odd}}(k)$. |
| **Brackets for Roots** | $[\pi/2, \pi]$ for the first odd state, and $[3\pi/2, 2\pi]$ for the second. |
| **Process Steps** | 1. Define $f_{\text{odd}}(k)$ in Python.<br>2. Plot the function to confirm sign changes.<br>3. Apply `brentq` within each safe bracket.<br>4. Compute $E_n = \frac{1}{2}k_n^2$ (since $\hbar=m=1$). |
| **Expected Behavior** | The algorithm finds distinct $k_1$ and $k_2$ values for the first two odd states. Their corresponding energies $E_1$ and $E_2$ are positive and discrete. |
| **Tracking Variables** | $k_n$, $E_n$, iteration count, and bracket intervals. |
| **Verification Goal** | Ensure $f_{\text{odd}}(k_n)$ is near zero and $E_2 > E_1$, confirming correct state ordering. |
| **Output** | A printed summary table of $k_n$ and $E_n$, plus a plot marking the computed root positions. |

---

#### **Pseudocode Implementation**

```pseudo-code
BEGIN

IMPORT numpy AS np
FROM scipy.optimize IMPORT brentq

// Constants
SET hbar = 1
SET m = 1
SET alpha = 5

// Define odd-state function
DEFINE f_odd(k):
    RETURN np.cot(k) + np.sqrt((alpha**2 / k**2) - 1)

// Define safe brackets
SET brackets = [(np.pi/2, np.pi), (3*np.pi/2, 2*np.pi)]

// Initialize storage
SET results = []

FOR each (a,b) IN brackets DO
    k_root = brentq(f_odd, a, b)
    E = 0.5 * (hbar**2 * k_root**2 / m)
    APPEND (k_root, E) TO results
END FOR

PRINT "Odd State Roots and Energies:"
FOR each (k, E) IN results DO
    PRINT "k =", k, "   E =", E
END FOR

END
```

---

#### **Outcome and Interpretation**

* The **Brent hybrid solver** converges reliably for each interval, avoiding the $\tan(k)$ and $\cot(k)$ singularities.
* The resulting $k_1$ and $k_2$ yield **distinct quantized energies** $E_1$ and $E_2$, representing the first two odd bound states.
* As $V_0$ (and thus $\alpha$) increases, more allowed energy levels appear, approaching the **infinite well limit**.
* This project solidifies the real-world necessity of **hybrid numerical strategies** in solving transcendental quantum problems.

---

!!! tip "Physical Connection"
    The number of allowed states increases with well depth ($V_0$).
    In the infinite limit, $\tan(k)$ and $\cot(k)$ roots align with the analytic standing-wave conditions of the infinite square well.



