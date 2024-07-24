# Single Precision Square Root Function for the CDC 3x00

W. J. Cody wrote a paper, cited below, which describes the process to derive parameters for the double precision square root function on the CDC 3600/3800.

The parameters for the single precision square root function were derived by Hans J. Maehly. Cody describes this process in the Appendix of his paper, along with the note that the derivation was not published by Maehly. Cody's presentation comes from Maehly's notes.

## Algorithm

The square root function represents the argument $x = 2^{2m} \times x_0$ where $1/2 \leq x_0 \lt 2$. A hyperbola, fitted to the square root function in that range, is evaluated, creating

$$x_1 = {{3.0903156} - {8.5500505 \over {3.0903156 + x_0}}}$$

Then the function improves that estimate with two iterations of the Newton-Raphson approximation: $x_2 = {{(x_1 + { x  \over x_1})} \over 2}$ and $x_3 = {{(x_2 + { x  \over x_2})} \over 2}$

$y = sqrt(x)$ is approximates as $y \approx 2^m \times x_3$

## Citation

_Double-precision square root for the CDC-3600_, W. J. Cody, Communications of the ACM, Volume 7, Issue 12, Pages 715 - 718, December 1964.

## Article URLs

[ACM](https://dl.acm.org/doi/abs/10.1145/355588.365122)
[DOI](https://doi.org/10.1145/355588.365122)
