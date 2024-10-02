# Relay DDE Solver

This project is dedicated to implementation of numerical methods suitable for a broad set of delay differential equations (DDEs), with the main focus on discontinuous DDEs.

The usage of this project consists of the following 4 steps:
1. In c++, define differential equations that you want to study.
2. In c++, make a code that takes parameters from json and generates desired output, like time series of one solution or values at the end of integration depending on parameters of equation or initial conditions, etc. It can be anything.
3. In python script or notebook, call that c++ code and get computed values in a form of numpy arrays.
4. In python script or notebook, draw pictures from obtained data in matplotlib or any other graphical library.

# Definition of equations

As of a state of development, the most general form of supported equations is

$$ 
\dot x = f(x, x_\tau, \dot x_\tau) = 
\begin{cases} 
  f_0(x, x_\tau, \dot x_\tau), & b(x, x_\tau, \dot x_\tau) < b_0, \\  
  f_1(x, x_\tau, \dot x_\tau), & b(x, x_\tau, \dot x_\tau) \in (b_0, b_1), \\
  \vdots \\
  f_{l}(x, x_\tau, \dot x_\tau),   & b(x, x_\tau, \dot x_\tau) \in (b_{l-1}, b_{l}), \\
  f_{l+1}(x, x_\tau, \dot x_\tau), & b(x, x_\tau, \dot x_\tau) > b_{l}
\end{cases} 
$$

where $x_\tau = (x(t - \tau_1(t)), ..., x(t - \tau_m(t)))^T$, $\dot x_\tau = (\dot x(t - \tau_1(t)), ..., \dot x(t - \tau_m(t)))^T$ and $\tau_i(t) > 0$ are a delay functions. 

With appropriate chose of $l$ --- the number of discontinuity surfaces, and $m$ --- the number of delays, this equation includes as a particular cases:
* Continuous and discontinuous ODEs (ordinary differential equations)
* Continuous and discontinuous DDEs (delay differential equations)
* Continuous and discontinuous NDDEs (neutral delay differential equations)

## class DifferentialEquation

Class `DifferentialEquation` encapsulates all information about one equation and corresponding `solution` method. Class itself has the following signature (pseudocode):

`template <size_t n, ArgSpec b_spec, ArgSpec f_spec> class DifferentialEquation`.

To be continued...


# Writing c++ code

To be continued...

# Calling c++ from python

To be continued...
