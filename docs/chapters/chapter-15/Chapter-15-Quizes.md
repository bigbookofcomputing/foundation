
!!! note "Quiz"

    ---
    
    ??? question "1. What is the fundamental purpose of Fourier Analysis in the context of computational physics?"
        - a) To increase the number of data points in a signal through interpolation.
        - b) To solve systems of linear equations that arise from discretizing PDEs.
        - c) To change the basis of a signal from the time or space domain to the frequency domain, revealing its periodic components.
        - d) To calculate the total energy of a simulated physical system.
    
        ??? info "See Answer"
            - **c) To change the basis of a signal from the time or space domain to the frequency domain, revealing its periodic components.**
            - **Explanation:** Fourier analysis decomposes a complex signal into a sum of simple sinusoidal waves, which is equivalent to viewing the signal in the frequency domain.
    
    ---
    
    ??? question "2. What is the primary computational limitation of the direct implementation of the Discrete Fourier Transform (DFT) formula?"
        - a) It only works for signals with a number of points that is a power of 2.
        - b) It has a computational cost that scales as $\mathcal{O}(N^2)$, making it too slow for large datasets.
        - c) It cannot handle complex-valued signals.
        - d) It suffers from severe numerical instability due to round-off errors.
    
        ??? info "See Answer"
            - **b) It has a computational cost that scales as $\mathcal{O}(N^2)$, making it too slow for large datasets.**
            - **Explanation:** The DFT formula requires a nested loop structure, leading to a quadratic scaling in computational complexity with respect to the number of data points, $N$.
    
    ---
    
    ??? question "3. The Fast Fourier Transform (FFT) is an algorithm that computes the exact same result as the DFT but with a significantly improved computational cost of:"
        - a) $\mathcal{O}(N)$
        - b) $\mathcal{O}(\log N)$
        - c) $\mathcal{O}(N \log N)$
        - d) $\mathcal{O}(N^{1.5})$
    
        ??? info "See Answer"
            - **c) $\mathcal{O}(N \log N)$**
            - **Explanation:** The FFT uses a "Divide and Conquer" strategy to reduce the computational complexity from $\mathcal{O}(N^2)$ to the much more efficient $\mathcal{O}(N \log N)$.
    
    ---
    
    ??? question "4. In the context of the FFT, what is the common practice if the number of data points, $N$, is not a power of 2 (e.g., $N=1000$)?"
        - a) Truncate the signal to the nearest smaller power of 2.
        - b) Use the direct DFT algorithm instead, as FFT is not applicable.
        - c) Pad the data array with zeros to increase its size to the next power of 2 (e.g., 1024).
        - d) The algorithm will fail and raise an error.
    
        ??? info "See Answer"
            - **c) Pad the data array with zeros to increase its size to the next power of 2 (e.g., 1024).**
            - **Explanation:** Padding the array to a power-of-2 length allows the FFT algorithm to run at its maximum efficiency.
    
    ---
    
    ??? question "5. After computing the FFT of a real-valued signal $y_n$ to get the complex coefficients $Y_k$, how is the Power Spectrum $\mathbf{P}_k$ calculated?"
        - a) $\mathbf{P}_k = \text{Real}(Y_k)$
        - b) $\mathbf{P}_k = Y_k / N$
        - c) $\mathbf{P}_k = |Y_k|^2$
        - d) $\mathbf{P}_k = \text{Imaginary}(Y_k)$
    
        ??? info "See Answer"
            - **c) $\mathbf{P}_k = |Y_k|^2$**
            - **Explanation:** The power spectrum is the square of the magnitude of the complex FFT coefficients. It represents the signal's power at each frequency and is a real-valued quantity.
    
    ---
    
    ??? question "6. What does the Nyquist-Shannon sampling theorem state?"
        - a) The sampling rate ($f_s$) must be less than half the maximum frequency in the signal.
        - b) The sampling rate ($f_s$) must be greater than twice the maximum frequency in the signal ($f_s > 2 f_{\text{max}}$).
        - c) The total number of samples must be a power of two.
        - d) The signal must not contain any noise.
    
        ??? info "See Answer"
            - **b) The sampling rate ($f_s$) must be greater than twice the maximum frequency in the signal ($f_s > 2 f_{\text{max}}$).**
            - **Explanation:** This theorem sets the minimum sampling rate required to accurately reconstruct a signal from its discrete samples without losing information.
    
    ---
    
    ??? question "7. What is the term for the phenomenon where a high-frequency component in a signal is incorrectly interpreted as a lower frequency due to an insufficient sampling rate?"
        - a) Attenuation
        - b) Aliasing
        - c) Catastrophic cancellation
        - d) Damping
    
        ??? info "See Answer"
            - **b) Aliasing**
            - **Explanation:** Aliasing occurs when the Nyquist-Shannon criterion is not met, causing high frequencies to "fold" over the Nyquist frequency and appear as spurious low-frequency signals.
    
    ---
    
    ??? question "8. If a signal is sampled at a rate of $f_s = 500$ Hz, what is the Nyquist frequency ($f_{Nyq}$), representing the highest frequency that can be unambiguously resolved?"
        - a) 500 Hz
        - b) 1000 Hz
        - c) 250 Hz
        - d) 125 Hz
    
        ??? info "See Answer"
            - **c) 250 Hz**
            - **Explanation:** The Nyquist frequency is always half the sampling rate: $f_{Nyq} = f_s / 2$.
    
    ---
    
    ??? question "9. In the output of a DFT, what does the frequency component for $k=0$ (i.e., $Y_0$) physically represent?"
        - a) The highest frequency component in the signal.
        - b) The total power of the signal.
        - c) The average value (or DC offset) of the signal.
        - d) The phase of the fundamental frequency.
    
        ??? info "See Answer"
            - **c) The average value (or DC offset) of the signal.**
            - **Explanation:** For $k=0$, the DFT formula simplifies to $Y_0 = \sum y_n$, which is the sum of all data points, proportional to the signal's average value.
    
    ---
    
    ??? question "10. Describe the three main steps of performing spectral filtering to remove high-frequency noise from a signal."
        - a) 1. Compute IFFT, 2. Add a filter, 3. Compute FFT.
        - b) 1. Compute FFT, 2. Zero out unwanted frequency coefficients, 3. Compute IFFT.
        - c) 1. Apply a smoothing kernel, 2. Compute FFT, 3. Normalize the data.
        - d) 1. Pad the signal, 2. Differentiate the signal, 3. Integrate the signal.
    
        ??? info "See Answer"
            - **b) 1. Compute FFT, 2. Zero out unwanted frequency coefficients, 3. Compute IFFT.**
            - **Explanation:** The process involves transforming to the frequency domain (FFT), manipulating the spectrum (filtering), and transforming back to the time domain (IFFT).
    
    ---
    
    ??? question "11. When analyzing the power spectrum of a plucked string simulation, what does the first and largest peak ($f_1$) represent?"
        - a) The amplitude of the pluck.
        - b) The timbre of the sound.
        - c) The fundamental frequency of the note.
        - d) The amount of noise in the simulation.
    
        ??? info "See Answer"
            - **c) The fundamental frequency of the note.**
            - **Explanation:** The fundamental frequency is the lowest frequency and typically the most powerful component, defining the pitch of the musical note.
    
    ---
    
    ??? question "12. The 'timbre' or 'quality' of a musical sound from a simulated instrument is determined by what feature of its power spectrum?"
        - a) The value of the Nyquist frequency.
        - b) The position of the fundamental frequency peak.
        - c) The relative heights and number of the harmonic peaks ($2f_1, 3f_1, \dots$).
        - d) The total area under the power spectrum curve.
    
        ??? info "See Answer"
            - **c) The relative heights and number of the harmonic peaks ($2f_1, 3f_1, \dots$).**
            - **Explanation:** The unique mixture of harmonics (overtones) above the fundamental frequency is what gives an instrument its characteristic sound.
    
    ---
    
    ??? question "13. The Cooley-Tukey FFT algorithm achieves its efficiency by recursively breaking an N-point DFT into:"
        - a) N one-point DFTs.
        - b) Two N/2-point DFTs (for even and odd indexed points).
        - c) A series of matrix-vector multiplications.
        - d) A polynomial interpolation problem.
    
        ??? info "See Answer"
            - **b) Two N/2-point DFTs (for even and odd indexed points).**
            - **Explanation:** This "Divide and Conquer" approach exploits symmetries in the DFT calculation to avoid redundant computations.
    
    ---
    
    ??? question "14. In Python, which `scipy.fft` function is used to get the physical frequencies corresponding to the FFT output array?"
        - a) `fft()`
        - b) `ifft()`
        - c) `fftfreq()`
        - d) `fftshift()`
    
        ??? info "See Answer"
            - **c) `fftfreq()`**
            - **Explanation:** `fftfreq(N, d)` returns the frequency bins, where N is the number of points and d is the sample spacing (1/sampling_rate).
    
    ---
    
    ??? question "15. A low-pass filter is designed to do what?"
        - a) Remove the DC component of a signal.
        - b) Allow only high frequencies to pass through, removing low frequencies.
        - c) Allow only low frequencies to pass through, removing high frequencies.
        - d) Amplify all frequencies equally.
    
        ??? info "See Answer"
            - **c) Allow only low frequencies to pass through, removing high frequencies.**
            - **Explanation:** This is useful for removing high-frequency noise from a signal that is known to have a lower frequency.
    
    ---
    
    ??? question "16. An engineer samples a signal at 20 kHz and sees a sharp peak in the FFT at 12 kHz. Why is this result suspicious?"
        - a) The peak is too sharp to be real.
        - b) The frequency is too low for a 20 kHz sampling rate.
        - c) The detected frequency (12 kHz) is above the Nyquist frequency (10 kHz) and is therefore an alias.
        - d) The power spectrum cannot have peaks at even-numbered frequencies.
    
        ??? info "See Answer"
            - **c) The detected frequency (12 kHz) is above the Nyquist frequency (10 kHz) and is therefore an alias.**
            - **Explanation:** With a 20 kHz sampling rate, the maximum resolvable frequency is 10 kHz. Any peak above this is a result of aliasing from a higher, unknown frequency.
    
    ---
    
    ??? question "17. The output of the `fft` function is an array of complex numbers. What information do the magnitude and phase of each complex number $Y_k$ encode?"
        - a) Magnitude encodes frequency; phase encodes power.
        - b) Magnitude encodes amplitude; phase encodes the time-shift of the frequency component.
        - c) Magnitude encodes power; phase encodes the sampling rate.
        - d) Magnitude encodes the signal-to-noise ratio; phase is irrelevant.
    
        ??? info "See Answer"
            - **b) Magnitude encodes amplitude; phase encodes the time-shift of the frequency component.**
            - **Explanation:** The complex result of the FFT contains information about both the strength (amplitude) and timing (phase) of each sinusoidal component.
    
    ---
    
    ??? question "18. What is the inverse operation of the Fast Fourier Transform (FFT)?"
        - a) The Discrete Cosine Transform (DCT).
        - b) The Inverse Fast Fourier Transform (IFFT).
        - c) The Power Spectrum calculation.
        - d) There is no inverse operation; the transform is irreversible.
    
        ??? info "See Answer"
            - **b) The Inverse Fast Fourier Transform (IFFT).**
            - **Explanation:** The IFFT transforms data from the frequency domain back to the time/space domain. The process is perfectly reversible (FFT -> IFFT).
    
    ---
    
    ??? question "19. If the power spectrum of a plucked string shows that all even harmonics ($2f_1, 4f_1, 6f_1, \dots$) are missing, what is the most likely physical reason?"
        - a) The string was plucked with very little force.
        - b) The simulation used a timestep that was too large.
        - c) The string was plucked exactly at its center ($L/2$).
        - d) The string material has very high damping.
    
        ??? info "See Answer"
            - **c) The string was plucked exactly at its center ($L/2$).**
            - **Explanation:** Plucking at the center places a node for all even harmonics, meaning they are not excited and will not appear in the spectrum.
    
    ---
    
    ??? question "20. The core principle of Fourier analysis, a change of basis to reveal underlying components, is a conceptual bridge to which other data analysis technique?"
        - a) Monte Carlo Integration (Chapter 11)
        - b) Root Finding Methods (Chapter 6)
        - c) Principal Component Analysis (PCA) (Chapter 16)
        - d) Ordinary Differential Equation Solvers (Chapter 7)
    
        ??? info "See Answer"
            - **c) Principal Component Analysis (PCA) (Chapter 16)**
            - **Explanation:** Both FFT and PCA are techniques that perform a change of basis to find a more informative representation of the data. FFT uses a fixed sinusoidal basis, while PCA finds a data-driven basis.
    
    ---
    
    ??? question "21. In the Python code `Y = fft(signal_noisy)`, what is the data type of the returned variable `Y`?"
        - a) An array of integers.
        - b) An array of floating-point numbers.
        - c) An array of complex numbers.
        - d) A single floating-point number.
    
        ??? info "See Answer"
            - **c) An array of complex numbers.**
            - **Explanation:** The FFT coefficients are complex, encoding both amplitude and phase information for each frequency.
    
    ---
    
    ??? question "22. When using the IFFT to reconstruct a signal after filtering, why is it common to take the real part of the result (e.g., `np.real(ifft(Y_filtered))`?"
        - a) The imaginary part contains only noise.
        - b) For a real-valued input signal, the reconstructed signal should also be real, and small imaginary components are typically due to floating-point inaccuracies.
        - c) The `ifft` function requires its output to be explicitly cast to real.
        - d) The real part represents power, which is the desired quantity.
    
        ??? info "See Answer"
            - **b) For a real-valued input signal, the reconstructed signal should also be real, and small imaginary components are typically due to floating-point inaccuracies.**
            - **Explanation:** Due to the symmetry of the FFT for real inputs, the IFFT of a symmetrically filtered spectrum should be real. Any residual imaginary part is usually negligible numerical error.
    
    ---
    
    ??? question "23. The duality between the time domain and the frequency domain implies that a signal that is very localized in time (like a sharp spike) will be:"
        - a) Very localized in frequency.
        - b) Very spread out in frequency (broadband).
        - c) Non-existent in the frequency domain.
        - d) Represented by a single frequency peak.
    
        ??? info "See Answer"
            - **b) Very spread out in frequency (broadband).**
            - **Explanation:** This is a manifestation of the uncertainty principle in signal processing. A signal cannot be arbitrarily localized in both time and frequency simultaneously. A sharp spike requires a wide range of frequencies to construct.
    
    ---
    
    ??? question "24. In the provided codebook example for spectral filtering, how is the filter applied to the frequency-domain data `Y`?"
        - a) By adding a masking array to `Y`.
        - b) By performing element-wise multiplication of `Y` with a boolean masking array (`Y * filter_mask`).
        - c) By using a `for` loop to iterate and set values to zero.
        - d) By calling a dedicated `filter` function from `scipy`.
    
        ??? info "See Answer"
            - **b) By performing element-wise multiplication of `Y` with a boolean masking array (`Y * filter_mask`).**
            - **Explanation:** This is a highly efficient, vectorized way to set the unwanted frequency coefficients to zero. The boolean mask is `True` (or 1) for frequencies to keep and `False` (or 0) for frequencies to discard.
    
    ---
    
    ??? question "25. If you increase the `T_DURATION` of a signal while keeping the sampling rate `FS` constant, what is the effect on the frequency resolution of the resulting FFT?"
        - a) The frequency resolution decreases (peaks become wider).
        - b) The frequency resolution increases (the space between frequency bins gets smaller).
        - c) The frequency resolution is unchanged.
        - d) The Nyquist frequency increases.
    
        ??? info "See Answer"
            - **b) The frequency resolution increases (the space between frequency bins gets smaller).**
            - **Explanation:** The frequency resolution is $\Delta f = f_s / N$. Increasing the duration `T_DURATION` increases the total number of points `N = FS * T_DURATION`, which decreases $\Delta f$, leading to a finer-grained frequency spectrum.
    
    ---
    
    