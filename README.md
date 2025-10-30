# EXP 1 A : COMPUTATION OF DFT USING DIRECT AND FFT

# AIM: 

# To Obtain DFT and FFT of a given sequence in SCILAB. 

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
// DISCRETE FOURIER TRANSFORM 
clc;
clear;
close;

// Input sequence
xn = [1 2 3 4 4 3 2 1];
n = 0:length(xn)-1;

// Plot input sequence
subplot(2,2,1);
plot2d3(n, xn);
xlabel("Time (n)");
ylabel("Amplitude");
title("Input Sequence");

// Compute DFT using FFT
Xk = fft(xn, -1);  // Forward FFT (DFT)

// Magnitude spectrum
magX = abs(Xk);
k = 0:length(Xk)-1;
subplot(2,2,2);
plot2d3(k, magX);
xlabel("Frequency index (k)");
ylabel("Magnitude");
title("Magnitude Spectrum");

// Phase spectrum
phaseX = atan(imag(Xk), real(Xk));
subplot(2,2,3);
plot2d3(k, phaseX);
xlabel("Frequency index (k)");
ylabel("Phase (radians)");
title("Phase Spectrum");

// Compute Inverse FFT (IDFT)
y = fft(Xk, 1);  // Inverse FFT

// Plot the reconstructed signal
n2 = 0:length(y)-1;
subplot(2,2,4);
plot2d3(n2, real(y));  // Take real part to avoid tiny imaginary errors
xlabel("Time (n)");
ylabel("Amplitude");
title("Reconstructed Signal using IFFT");


# OUTPUT: <img width="765" height="725" alt="image" src="https://github.com/user-attachments/assets/eb512640-20cb-4fac-a77e-1ee00018e5db" />



# RESULT: Hence got the output for DFT and FFT of a given sequence in SCILAB. 

