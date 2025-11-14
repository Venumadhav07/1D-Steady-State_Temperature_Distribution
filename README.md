# 1D Steady-State Temperature Distribution (Finite Difference Method)

This project demonstrates the numerical solution of *1D steady-state heat conduction* using the *finite difference method (FDM)* in MATLAB.  
The goal is to compute the temperature distribution along a rod when the two ends are kept at fixed temperatures.

## Problem Description

We consider a rod divided into N nodes:

- *Left end (Base):* 200°C  
- *Right end (Tip):* 20°C  
- *Interior nodes:* Unknown temperatures  

Governing equation (steady state, no heat generation):

\frac{d^2 T}{dx^2} = 0

Finite difference formulation for interior nodes:

T_i = \frac{T_{i-1} + T_{i+1}}{2}

We use an *iterative relaxation method* to solve this until temperatures converge.

## Method Used

1. Divide the rod into *N = 10* nodes  
2. Apply boundary conditions:
   - \( T_1 = 200^\circ C \)
   - \( T_N = 20^\circ C \)
3. Update interior nodes iteratively:

   T_i^{new} = \frac{T_{i-1} + T_{i+1}}{2}
  
4. Repeat for a fixed number of iterations (e.g., 100)
5. Plot the final temperature distribution

This produces a *linear* temperature profile, as expected for steady-state conduction without internal heat generation.


## ALGORITH:

% Geometry
L  = 10/100;
N  = 10;
dx = L/(N-1);

% Initial and Boundary Conditions
T = zeros(1,N);      %initail condition=0
T(1) = 200;
T(N) = 20;

% Iterative Relaxation
k = 100;
for j = 1:k
    for i = 2:N-1
        T(i) = 0.5 * (T(i+1) + T(i-1));
    end
end

% Display final temperatures
for i = 1:N
    fprintf('T%d = %.2f\n', i, T(i));
end

% Plot
figure;
plot(T);
xlabel('Node Index');
ylabel('Temperature (°C)');
title('1D STEADY STATE TEMPERATURE DISTRIBUTION');
grid on;
title('1D Steady-State Temperature Distribution');
grid on;
legend('Temperature Profile', 'Location', 'eastoutside');
