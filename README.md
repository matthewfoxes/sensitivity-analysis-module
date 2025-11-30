# sensitivity-analysis-module
Sensitivity Analysis Module for Monte Carlo Data in Fortran

This Fortran module provides a local sensitivity analysis tool for functions evaluated via Monte Carlo simulations. It allows you to estimate the gradient and Hessian at a reference point x0 and to predict the function value at nearby points using a second-order Taylor expansion.

Features

Gradient estimation: Optional calculation of the local gradient of the output with respect to each input variable.

Hessian estimation: Optional calculation of the local Hessian, capturing second-order interactions between input variables.

Prediction at new points: Computes the predicted output at any nearby point xp using the local Taylor expansion.

Standalone implementation: Uses native Fortran operations without requiring external libraries like LAPACK.

Monte Carlo-based: Works with any dataset of function evaluations near x0, providing a data-driven local approximation.

Subroutine

subroutine sensitivity_analysis(n, r, X, Y, x0, xp, yp, grad, H)

Inputs

n – Number of input variables

r – Number of Monte Carlo runs

X(r,n) – Matrix of input samples

Y(r) – Vector of function outputs corresponding to X

x0(n) – Reference point for local sensitivity analysis

xp(n) – Point at which to predict the function value

Outputs

yp – Predicted value of the function at xp

grad(n) (optional) – Estimated gradient at x0

H(n,n) (optional) – Estimated Hessian at x0

How It Works

Centers the Monte Carlo data around x0.

Builds a design matrix with constant, linear, and quadratic terms.

Performs a least-squares regression to estimate gradient and Hessian coefficients.

Uses these coefficients to predict the function value at xp using a second-order Taylor expansion.

This module is ideal for local sensitivity analysis, uncertainty quantification, and data-driven modeling when analytical derivatives are not available.
