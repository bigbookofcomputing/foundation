
# **Chapter 2 : Quizes**

----


!!! note "Quiz"
    **1. What is the "foundational crisis of computational physics" as described in Chapter 2?**

    - A. The difficulty in solving complex differential equations.
    - B. The conflict between the infinite, continuous nature of Real Numbers ($\mathbb{R}$) and the finite, discrete representation in a computer.
    - C. The challenge of writing bug-free code for simulations.
    - D. The high cost of supercomputing resources.

    ??? info "See Answer"
        **Correct: B**

        *(This fundamental mismatch is the source of all computational error, as computers must approximate the infinite granularity of theoretical mathematics.)*

---

!!! note "Quiz"
    **2. If the true value of a measurement is 50.0 and the computed value is 49.5, what is the relative error?**

    - A. 0.5
    - B. 0.01
    - C. 1.0
    - D. 0.05

    ??? info "See Answer"
        **Correct: B**

        *(The absolute error is $|50.0 - 49.5| = 0.5$. The relative error is the absolute error divided by the true value: $0.5 / 50.0 = 0.01$.)*

---

!!! note "Quiz"
    **3. In the IEEE 754 standard for a 64-bit float, which component primarily determines the number's **precision** (the number of significant digits)?**

    - A. The Sign bit (1 bit)
    - B. The Exponent (11 bits)
    - C. The Mantissa (52 bits)
    - D. The bias value

    ??? info "See Answer"
        **Correct: C**

        *(The 52-bit mantissa stores the significant digits of the number, defining its precision, which corresponds to about 15-16 decimal digits.)*

---

!!! note "Quiz"
    **4. The "gappy ruler" consequence of floating-point representation means that:**

    - A. All representable numbers are evenly spaced.
    - B. The absolute gap between adjacent representable numbers is constant.
    - C. The absolute gap between adjacent representable numbers grows as their magnitude increases.
    - D. Relative precision is lost for numbers of large magnitude.

    ??? info "See Answer"
        **Correct: C**

        *(Because the exponent scales the number while the mantissa's precision is fixed, the absolute spacing between numbers widens exponentially as they get larger.)*

---

!!! note "Quiz"
    **5. What is Machine Epsilon ($\epsilon_m$)?**

    - A. The smallest positive number the machine can represent.
    - B. The error introduced when a number is rounded to the nearest integer.
    - C. The smallest number that, when added to 1.0, yields a result different from 1.0.
    - D. The largest possible round-off error in any calculation.

    ??? info "See Answer"
        **Correct: C**

        *(Machine Epsilon is the fundamental unit of relative precision, representing the gap between 1.0 and the next representable floating-point number.)*

---

!!! note "Quiz"
    **6. The Ariane 5 rocket disaster was a direct result of which numerical error?**

    - A. Round-off error accumulation.
    - B. Catastrophic cancellation.
    - C. Underflow.
    - D. Overflow.

    ??? info "See Answer"        
        **Correct: D**

        *(A 64-bit float representing the rocket's velocity became too large to be stored in a 16-bit integer, causing an overflow that was misinterpreted by the guidance system.)*

---

!!! note "Quiz"
    **7. What is the fundamental difference between Round-off error and Truncation error?**

    - A. Round-off error is controllable, while truncation error is not.
    - B. Round-off error comes from hardware limits (finite precision), while truncation error comes from algorithmic approximation (e.g., cutting a Taylor series).
    - C. Round-off error only affects integers, while truncation error affects floats.
    - D. Truncation error is always larger than round-off error.

    ??? info "See Answer"
        **Correct: B**

        *(Round-off is an uncontrollable hardware limitation (the "blunt pencil"), whereas truncation is a controllable algorithmic choice (the "imperfect map").)*

---

!!! note "Quiz"
    **8. The Patriot Missile failure in 1991 was caused by the accumulation of which type of error?**

    - A. Truncation error in the guidance algorithm.
    - B. Round-off error from the binary representation of 0.1 seconds.
    - C. Catastrophic cancellation in a distance calculation.
    - D. Integer overflow in the system clock.

    ??? info "See Answer"
        **Correct: B**

        *(A tiny, inherent error in storing the decimal 0.1 in binary accumulated over 100 hours, causing a significant clock drift that made the missile miss its target.)*

---

!!! note "Quiz"
    **9. Catastrophic cancellation is most likely to occur when:**

    - A. Adding two very large numbers.
    - B. Multiplying a large number by a very small number.
    - C. Subtracting two nearly equal floating-point numbers.
    - D. Dividing a number by zero.

    ??? info "See Answer"
        **Correct: C**

        *(When two close numbers are subtracted, the leading, accurate digits cancel, leaving a result composed of the original numbers' round-off "noise," thus destroying precision.)*

---

!!! note "Quiz"
    **10. To avoid catastrophic cancellation when calculating $f(x) = 1 - \cos(x)$ for small $x$, which stable alternative formula should be used?**

    - A. $f(x) = \sin^2(x) / (1 + \cos(x))$
    - B. $f(x) = 2 \sin^2(x/2)$
    - C. $f(x) = \tan(x) \sin(x)$
    - D. There is no stable alternative.

    ??? info "See Answer"
        **Correct: B**

        *(The half-angle identity $1 - \cos(x) = 2 \sin^2(x/2)$ avoids the subtraction of nearly equal numbers and is therefore computationally stable for small x.)*

---

!!! note "Quiz"
    **11. What does a large Condition Number ($\kappa \gg 1$) indicate about a problem?**

    - A. The problem is numerically stable and robust.
    - B. The problem is "ill-conditioned," meaning small relative errors in the input will be magnified into large relative errors in the output.
    - C. The algorithm will converge quickly.
    - D. The problem can only be solved with integer arithmetic.

    ??? info "See Answer"
        **Correct: B**

        *(The condition number is a measure of a problem's inherent sensitivity to input errors. A large $\kappa$ signifies an unstable problem where errors are amplified.)*

---

!!! note "Quiz"
    **12. In an iterative simulation, an algorithm that causes the computational error to grow exponentially at each step is described as:**

    - A. Well-conditioned
    - B. Stable
    - C. Unstable
    - D. Convergent

    ??? info "See Answer"
        **Correct: C**

        *(Unstable algorithms act as error amplifiers, leading to exponential error growth that quickly overwhelms the true solution and makes the simulation results meaningless.)*

---

!!! note "Quiz"
    **13. According to the Nyquist-Shannon Sampling Criterion, to avoid aliasing, the sampling rate ($f_s$) must be:**

    - A. Equal to the maximum signal frequency ($f_s = f_{\max}$).
    - B. Less than half the maximum signal frequency ($f_s < 0.5 f_{\max}$).
    - C. At least twice the maximum signal frequency ($f_s \ge 2 f_{\max}$).
    - D. Independent of the signal frequency.

    ??? info "See Answer"
        **Correct: C**

        *(If the sampling rate is too low, high-frequency components of a signal are incorrectly recorded as lower-frequency "aliases," and the original information is lost.)*

---

!!! note "Quiz"
    **14. In digital signal processing, increasing the bit depth (e.g., from 8-bit to 16-bit) primarily reduces which type of error?**

    - A. Aliasing error
    - B. Quantization error
    - C. Truncation error
    - D. Catastrophic cancellation

    ??? info "See Answer"
        **Correct: B**

        *(Higher bit depth increases the number of discrete levels available to represent the signal's amplitude, reducing the rounding error (quantization error) at each sample.)*

---

!!! note "Quiz"
    **15. Why is floating-point addition not always associative? i.e., why can `(a + b) + c` differ from `a + (b + c)`?**

    - A. Because of integer overflow.
    - B. Because of the order of operations in the CPU.
    - C. Because adding a very small number to a very large number can cause the small number to be rounded to zero.
    - D. Because all floating-point operations are inherently random.

    ??? info "See Answer"
        **Correct: C**

        *(If `a` is very large and `b` is very small, `a + b` might just equal `a` due to rounding. But if `b` and `c` are both small, `b + c` might be large enough to be "seen" when added to `a`.)*

---

!!! note "Quiz"
    **16. In the context of computational ethics, what is the difference between "Verification" and "Validation"?**

    - A. Verification checks the physics; Validation checks the code.
    - B. Verification asks "Are we solving the equations correctly?"; Validation asks "Are we solving the correct equations?".
    - C. Verification is done by testers; Validation is done by physicists.
    - D. There is no difference; the terms are interchangeable.

    ??? info "See Answer"
        **Correct: B**

        *(Verification ensures the code accurately implements the mathematical model. Validation ensures the model accurately represents the real-world physics by comparing to experimental data.)*

---

!!! note "Quiz"
    **17. The error plot for a numerical derivative approximation often forms a "V" shape. What do the left and right sides of the "V" represent?**

    - A. Left: Overflow, Right: Underflow.
    - B. Left: Round-off error dominance, Right: Truncation error dominance.
    - C. Left: Truncation error dominance, Right: Round-off error dominance.
    - D. Left: Stable region, Right: Unstable region.

    ??? info "See Answer"
        **Correct: C**

        *(For large step sizes (left side), truncation error dominates. For very small step sizes (right side), round-off error from catastrophic cancellation dominates.)*

---

!!! note "Quiz"s
    **18. Why can't the decimal number 0.1 be represented exactly in binary floating-point?**

    - A. It is an irrational number.
    - B. It results in an infinitely repeating fraction in base-2.
    - C. It is too small for the exponent to handle.
    - D. It requires more than 52 mantissa bits.

    ??? info "See Answer"
        **Correct: B**

        *(Similar to how 1/3 is 0.333... in decimal, 1/10 is a non-terminating fraction in binary, which must be rounded, introducing representation error from the start.)*

---

!!! note "Quiz"
    **19. An "underflow" error occurs when:**

    - A. A number is too large to be represented and is set to infinity.
    - B. A non-zero calculation results in a value too small to be distinguished from zero.
    - C. A calculation results in "Not a Number" (NaN).
    - D. Two numbers cancel each other out perfectly.

    ??? info "See Answer"
        **Correct: B**

        *(Underflow happens when a result is smaller in magnitude than the smallest value the exponent can represent, often causing it to be "flushed to zero.")*

---

!!! note "Quiz"
    **20. What is the primary role of the "exponent" in an IEEE 754 floating-point number?**

    - A. To store the number's sign.
    - B. To determine the number's precision.
    - C. To set the number's scale or magnitude (its range).
    - D. To manage rounding operations.

    ??? info "See Answer"
        **Correct: C**

        *(The exponent acts like the power in scientific notation, defining the number's range and allowing the system to represent both very large and very small values.)*

---

!!! note "Quiz"
    **21. In the hands-on project simulating aliasing, why does a 10 Hz signal appear as a 5 Hz signal when sampled at 15 Hz?**

    - A. Because the sampling rate was too high.
    - B. Because the Nyquist criterion ($f_s \ge 2f_{\max}$) was violated.
    - C. Because of quantization error from a low bit depth.
    - D. Because of round-off error in the sine function.

    ??? info "See Answer"
        **Correct: B**

        *(The sampling rate of 15 Hz is less than twice the signal frequency of 10 Hz (20 Hz). The high frequency "aliases" to a lower, false frequency, which is $|f_{\max} - f_s| = |10 - 15| = 5$ Hz.)*

---

!!! note "Quiz"
    **22. What is the most reliable way to check if a numerical algorithm is sensitive to round-off error?**

    - A. Read the algorithm's documentation.
    - B. Run the simulation in both 32-bit (single) and 64-bit (double) precision and compare the results.
    - C. Check for memory leaks.
    - D. Ensure the code is well-commented.

    ??? info "See Answer"
        **Correct: B**

        *(If the 32-bit results diverge significantly or explode while the 64-bit results remain stable, it is a strong indicator that the calculation is sensitive to the smaller precision of 32-bit floats.)*

---

!!! note "Quiz"
    **23. The unstable recursive formula $y_n = (10/3) y_{n-1} - y_{n-2}$ for calculating $(1/3)^n$ fails because:**

    - A. It is mathematically incorrect.
    - B. It suffers from catastrophic cancellation.
    - C. Initial round-off error seeds a hidden, exponentially growing unstable solution ($3^n$).
    - D. It causes an immediate overflow.

    ??? info "See Answer"
        **Correct: C**

        *(The formula is mathematically sound, but numerically unstable. Tiny round-off errors in the initial values are enough to trigger a hidden unstable solution that grows exponentially and overwhelms the correct, decaying solution.)*

---

!!! note "Quiz"
    **24. When summing a long list of floating-point numbers of different magnitudes, which strategy is generally more accurate?**

    - A. Summing them in random order.
    - B. Summing them from largest to smallest.
    - C. Summing them from smallest to largest.
    - D. The order of summation does not affect the final result.

    ??? info "See Answer"
        **Correct: C**

        *(Summing from smallest to largest allows the small numbers to accumulate into a value large enough to be "seen" when added to the larger numbers, minimizing rounding errors.)*

---

!!! note "Quiz"
    **25. What is the purpose of setting a random number seed (e.g., `np.random.seed(42)`) in a scientific simulation?**

    - A. To make the simulation run faster.
    - B. To ensure the random numbers are truly unpredictable.
    - C. To make the stochastic experiment reproducible for debugging and verification.
    - D. To increase the precision of the random numbers.

    ??? info "See Answer"
        **Correct: C**

        *(Setting a seed guarantees that the same sequence of pseudo-random numbers is generated every time, which is critical for debugging, verification, and ensuring fair comparisons between different algorithm versions.)*
