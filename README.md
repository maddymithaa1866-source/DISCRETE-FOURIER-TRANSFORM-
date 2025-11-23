# EXP 1 A : COMPUTATION OF DFT USING DIRECT AND FFT

# AIM: 

 To Obtain DFT and FFT of a given sequence in SCILAB. 

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
DISCRETE FOURIER TRANSFORM 
```
clc;
clear;

// Input sequence
x = [1 2 3 4];   // change your sequence here

N = length(x);

// ----------- DFT (manual) ----------
X_dft = zeros(1, N);

for k = 0:N-1
    for n = 0:N-1
        X_dft(k+1) = X_dft(k+1) + x(n+1) * exp(-%i*2*%pi*k*n/N);
    end
end

// ----------- FFT (inbuilt) ----------
X_fft = fft(x, -1);

// ----------- FIX FOR NO GRAPH PROBLEM -----------
clf();        // clears figure
scf(0);       // opens figure window

// ----------- PLOTTING -----------
subplot(2,2,1);
plot2d3(0:N-1, abs(X_dft));
title("Magnitude of DFT");

subplot(2,2,2);
plot2d3(0:N-1, imag(X_dft));
title("Imaginary Part of DFT");

subplot(2,2,3);
plot2d3(0:N-1, abs(X_fft));
title("Magnitude of FFT");

subplot(2,2,4);
plot2d3(0:N-1, imag(X_fft));
title("Imaginary Part of FFT");
```


# OUTPUT: 
<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/a4e1a6f5-bef9-4dad-8ebf-9d3855917ab0" />



# RESULT: 
