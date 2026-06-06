# AC-EXP6
# AUTOCORRLATON and PSD:

## AIM: 

Write a program for Autocorrelation and PSD of signals in SCILAB and verify Wiener-Khinchin relation.

## EQUIPMENTS NEEDED:

• Computer with i3 Processor • SCI LAB

## THEORY:

The Wiener-Khinchin theorem states that the power spectral density of a wide sense stationary random process is the Fourier transform of the corresponding autocorrelation function.

## ALGORITHM:

Load or Define the Signal: Input your time-domain signal.
Compute Autocorrelation: Calculate the autocorrelation function of the signal.
Compute Power Spectral Density (PSD): Estimate the PSD of the signal, either directly using a method like Welch’s periodogram or by using the Fourier transform of the autocorrelation.
Plot Results: Visualize the autocorrelation function and PSD.
PROCEDURE

• Refer Algorithms and write code for the experiment. • Open SCILAB in System • Type your code in New Editor • Save the file • Execute the code • If any Error, correct it in code and execute again • Verify the generated waveform using Tabulation and Model Waveform

## PROGRAM:
```
clc;
clear all;

// Signal and Autocorrelation
t = 0:0.01:2*%pi;

// Modified Signal Equation
x = 2*sin(3*t) + 0.5*cos(7*t);

subplot(3,2,1);
plot(t,x);
title("Original Signal x(t)=2sin(3t)+0.5cos(7t)");
xlabel("t");
ylabel("x(t)");

// Autocorrelation
au = xcorr(x,x);

subplot(3,2,2);
plot(au);
title("Autocorrelation");
xlabel("Samples");
ylabel("Amplitude");

// FFT of Autocorrelation
v = fft(au);

subplot(3,2,3);
plot(abs(v));
title("FFT of Autocorrelation");
xlabel("Frequency Index");
ylabel("|V|");

// FFT of Signal
fw = fft(x);

subplot(3,2,4);
plot(abs(fw));
title("FFT of Signal");
xlabel("Frequency Index");
ylabel("|FW|");

// Power Spectrum
fw2 = (abs(fw)).^2;

subplot(3,2,5);
plot(fw2);
title("Power Spectrum");
xlabel("Frequency Index");
ylabel("Power");


clc;
clear;

// Mean and Variance Calculation

function z = f(x)
    z = x.^3 .* (1 - x).^2;
endfunction

a = 0;
b = 1;

EX = intg(a,b,f);

function z = c(y)
    z = y.^3 .* (1 - y).^2;
endfunction

EY = intg(a,b,c);

disp(EX,"i) Mean of X = ");
disp(EY,"Mean of Y = ");

function z = g(x)
    z = x.^2 .* x.^3 .* (1 - x).^2;
endfunction

EX2 = intg(a,b,g);

function z = h(y)
    z = y.^2 .* y.^3 .* (1 - y).^2;
endfunction

EY2 = intg(a,b,h);

vX2 = EX2 - (EX)^2;
vY2 = EY2 - (EY)^2;

disp(vX2,"ii) Variance of X = ");
disp(vY2,"Variance of Y = ");


clc;
clear;

// Cross Correlation

x = [1 2 3 4];
y = [4 3 2 1];

// Cross correlation
r = convol(x, y($:-1:1));

// Separate graphics window
figure();

// Stem-style waveform
plot2d3(1:length(r), r);

xtitle("Cross Correlation");
xlabel("Samples");
ylabel("Amplitude");

```

## OUTPUT:

<img width="757" height="725" alt="image" src="https://github.com/user-attachments/assets/a91719d2-dde1-4650-ba07-3773f09ae33b" />


## RESULT: 

Thus the Autocorrelation and PSD are executed in Scilab and output is verified.
