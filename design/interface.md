# Other Interfaces
## Mathematica
The two packages that seem to do least squares fitting are `Fit` and `FindFit`.

Fit which deals with any linear combination of terms takes 3 arguments the `data`, which is
a list of points `{x1, y1, ..., f1}` and an expression `funs` with a gives a list of terms
(i.e. `{1, x, Sin[x]}`) which are used as a linear combination to be solved for to fit the
data. Finally the parameter `var` is given to describe which symbols in `funs` are to be
replaced with the data. The documentation is vague but states that `Fit` uses singular
value decomposition. Whereas `FindFit` uses `Levenberg-Margquardt` for nonlinear least
squares (and general optimization for when it is not just least squares, which I am not 
interested in)

Some examples:

    data = {{0, 1}, {1, 0}, {3, 2}, {5, 4}}
    # Fin the line that best fits the data:
    line = Fit[data, {1, x}, x]
    # Find the parabola that best fits the data
    parabola = Fit[data, {1, x, x^2}, x]
    # strange combination
    fit = Fit[data, {1, x, Sin[x]}, x]

If statistical and goodness of fit statistics are needed then the `Fit` call is wrapped in
a `LinearModelFit` which gives a whole host of information on the fit.
