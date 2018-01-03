# GCE-Math &nbsp; [![Build Status](https://travis-ci.org/kthohr/gcem.svg?branch=master)](https://travis-ci.org/kthohr/gcem) [![Coverage Status](https://codecov.io/github/kthohr/gcem/coverage.svg?branch=master)](https://codecov.io/github/kthohr/gcem?branch=master)

## About

GCE-Math (**G**eneralized **C**onstant **E**xpression Math) is a templated C++ library for compile-time computation of mathematical functions.

* GCE-Math makes extensive use of recursive templates and ```constexpr``` functions to evaluate continued fraction and series-type expansions of special mathematical functions.
* The library is written in a concise C++11 ```constexpr``` format, and is C++11/14/17 compatible.
* The ```gcem::``` syntax is identical to the C++ standard library.
* Tested and accurate to machine precision against the C++ standard library.

## Status

The library is actively maintained, and is still being extended.

A list of features includes:

* basic standard library functions, such as:
    - ```abs```, ```exp```, ```log```, ```max```, ```min```, ```pow```, ```sqrt```
* trigonometric functions:
    - basic: ```cos```, ```sin```, ```tan```
    - inverse: ```acos```, ```asin```, ```atan```
    - hyperbolic (area) functions: ```cosh```, ```sinh```, ```tanh```, ```acosh```, ```asinh```, ```atanh```
* special functions:
    - beta and gamma functions: ```beta```, ```lbeta```, ```lgamma```, ```tgamma```
    - the Gaussian error function and inverse error function: ```erf```, ```erf_inv```
    - (regularized) incomplete beta and incomplete gamma functions: ```incomplete_beta```, ```incomplete_gamma```
    - inverse incomplete beta and incomplete gamma functions: ```incomplete_beta_inv```, ```incomplete_gamma_inv```

## Syntax

GCE-Math functions are written as C++ templates. For example, the [Gaussian error function](https://en.wikipedia.org/wiki/Error_function) (```erf```) is defined as:
```cpp
template<typename T>
constexpr
T
erf(const T x)
```
where a series of internal templated ```constexpr``` functions implement a recursive continued fraction expansion. 

For users unfamiliar with C++ template programming, note that the output type ('```T```') in this example is determined by the input type, e.g., ```float```, ```double```, ```long double```, etc. So take care when passing integral-type inputs and use recasts where appropriate.


## Installation

GCE-Math is a header-only library and does not require any additional libraries (beyond a C++11 compatible compiler). 

Simply include the gcem header files with your project.

## Example

Compute the log Gamma function at a point:

```cpp
#include "gcem.hpp"

int main()
{
    constexpr long double x = 1.5;
    constexpr long double res = gcem::lgamma(x);

    return 0;
}
```

To build the full test suite:

```bash
# clone gcem from GitHub
git clone -b master --single-branch https://github.com/kthohr/gcem ./gcem
# compile tests
cd ./gcem/tests
make
./run_tests
```

## Related libraries

For a library built on the GCEM compile-time functionality, see [StatsLib](https://github.com/kthohr/stats).

## Author

Keith O'Hara

## License

GPL (>= 2)
