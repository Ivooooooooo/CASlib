# CASlib: Computer Algebra System in Modern C++

[![C++20](https://img.shields.io/badge/C%2B%2B-20-blue.svg)](https://en.cppreference.com/)
[![Header-only](https://img.shields.io/badge/header--only-brightgreen)](https://github.com/caslib/caslib)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

CASlib is a symbolic computation library in C++20 that provides tools for algebraic manipulation, automatic differentiation, and simplification of mathematical expressions.

---

## Main Features

- **Symbolic Manipulation**: Variables, constants, and algebraic expressions.
- **Automatic Differentiation**: Calculation of symbolic derivatives.
- **Simplification**: Algebraic simplification rules.
- **Mathematical Functions**: Support for sine, cosine, exponentials, and more.
- **Extensible**: Easy addition of new operations and rules.
- **Type-safe**: Use of C++20 concepts for type safety.

---

## Usage Example
```cpp
#include "caslib.hpp"
#include <iostream>

int main() {
    using namespace caslib;

    CAS engine;

    // Create symbols
    auto x = engine.symbol("x");
    auto y = engine.symbol("y");

    // Build expression: x^2 + sin(2y)
    auto expr = engine.add(
        engine.pow(x, engine.constant(2)),
        engine.sin(engine.mul(engine.constant(2), y))
    );

    // Partial derivative with respect to x
    auto dx = engine.derivative(expr, x);

    // Simplify and display
    std::cout << "Expression: " << engine.to_string(expr) << "\n";
    std::cout << "Derivative: " << engine.to_string(dx) << "\n";
    std::cout << "Simplified: " << engine.to_string(engine.simplify(dx)) << "\n";

    return 0;
}
```
**Expected Output:**
```
Expression: (x^2.000000) + sin((2.000000 * y))
Derivative: (2.000000 * x) + cos((2.000000 * y)) * 0.000000
Simplified: 2.000000 * x
```

---

## Installation

CASlib is a header-only library. Just include `caslib.hpp` in your project.

```bash
git clone https://github.com/Ivooooooooo/caslib/caslib.git
cd caslib
```

---

## Requirements

- C++20-compatible compiler (GCC 10+, Clang 10+, MSVC 9+)

---

## Contributions

Contributions are welcome! Open an issue or submit a pull request.
