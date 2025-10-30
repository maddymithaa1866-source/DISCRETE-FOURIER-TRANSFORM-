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

// Input sequence (8 samples)
x = [1 2 3 4 4 3 2 1];
N = length(x);

// -------- Input Plot --------
subplot(2,1,1);
plot2d3(0:N-1, x);
xlabel("n");
ylabel("Amplitude");
title("Input Sequence");
xgrid();

// -------- DIF FFT Computation --------
stages = log2(N);
X = x; // copy input

for s = 1:stages
    m = 2^s;
    half = m/2;
    Wm = exp(-%i * 2 * %pi / m);
    for k = 0:(N/m - 1)
        for j = 0:(half - 1)
            t = X(k*m + j + 1);
            u = X(k*m + j + half + 1);
            X(k*m + j + 1) = t + u;
            X(k*m + j + half + 1) = (t - u) * (Wm^j);
        end
    end
end

// -------- Bit reversal (manual version) --------
function y = bitrevorder_manual(N)
    bits = log2(N);
    y = zeros(1,N);
    for n = 0:(N-1)
        b = dec2bin(n,bits);
        rb = part(b, length(b):-1:1);
        y(n+1) = bin2dec(rb) + 1;
    end
endfunction

order = bitrevorder_manual(N);
X = X(order);

// -------- Display output values --------
disp("DIF FFT Output (Complex values):");
disp(X);

// -------- Output Plot --------
subplot(2,1,2);
plot2d3(0:N-1, abs(X));
xlabel("k");
ylabel("|X(k)|");
title("Magnitude Spectrum using DIF");
xgrid();



# OUTPUT: <img width="765" height="725" alt="image" src="https://github.com/user-attachments/assets/e6e00d1a-ec9d-47ef-bd14-c4df26db7119" />



# RESULT: Hence got the output for DFT and FFT of a given sequence in SCILAB.

