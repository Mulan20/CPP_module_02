# CPP_module_02

CPP Module 02 — 42 Bangkok
Ad-hoc polymorphism, operator overloading, and the Orthodox Canonical Class Form.

About
This repository contains my CPP Module 02 exercises completed at 42 Bangkok. This module introduces fixed-point numbers, operator overloading, and the Orthodox Canonical Form (OCCF) — a standard class design pattern required from Module 02 onwards .

All code compiles with the C++98 standard and -Wall -Wextra -Werror .

Project Structure
text
.
├── ex00/
│   ├── Makefile
│   ├── Fixed.hpp
│   ├── Fixed.cpp
│   └── main.cpp
├── ex01/
│   ├── Makefile
│   ├── Fixed.hpp
│   ├── Fixed.cpp
│   └── main.cpp
├── ex02/
│   ├── Makefile
│   ├── Fixed.hpp
│   ├── Fixed.cpp
│   └── main.cpp
├── ex03/
│   ├── Makefile
│   ├── Fixed.hpp
│   ├── Fixed.cpp
│   ├── Point.hpp
│   ├── Point.cpp
│   ├── bsp.cpp
│   └── main.cpp
└── README.md
Environment & Compilation
Requirements:

Unix-like system (Linux / macOS)

c++ (or g++) with C++98 support

make

Compile each exercise:

bash
cd ex00 && make
cd ex01 && make
cd ex02 && make
cd ex03 && make
Clean:

bash
make clean    # remove object files
make fclean   # remove object files and the executable
make re       # fclean + all
Exercises
ex00 — My First Class in Orthodox Canonical Form
Goal: Create a Fixed class representing a fixed-point number using the Orthodox Canonical Form .

Requirements:

Private integer _fp_value to store the raw fixed-point value.

Static constant integer _fract_bits set to 8.

Default constructor (initializes value to 0).

Copy constructor.

Copy assignment operator overload.

Destructor.

int getRawBits(void) const; — returns the raw value.

void setRawBits(int const raw); — sets the raw value.

Concepts: OCCF, static members, const member functions.

ex01 — Towards a More Useful Fixed-Point Class
Goal: Expand the Fixed class to convert between integers, floats, and fixed-point values .

New Requirements:

Constructor taking a const int — converts to fixed-point.

Constructor taking a const float — converts to fixed-point.

float toFloat(void) const; — converts to float.

int toInt(void) const; — converts to integer.

Overload of the insertion operator (<<) to print the float representation.

Allowed function: roundf .

Concepts: Constructor overloading, conversion, stream operator overloading.

ex02 — Now We're Talking
Goal: Implement full operator overloading for the Fixed class .

New Requirements:

Comparison operators: >, <, >=, <=, ==, !=

Arithmetic operators: +, -, *, /

Increment/Decrement operators: pre-++, post-++, pre---, post--- (increments by the smallest representable ε, such as 1 + ε > 1) 

Static member functions: min and max (taking two references and returning a reference)

Concepts: Operator overloading, static member functions, const correctness.

ex03 — BSP (Binary Space Partitioning)
Goal: Apply the Fixed class to a geometric problem: determine whether a point lies inside a triangle .

New Requirements:

Point class using Fixed for x and y coordinates (OCCF).

bool bsp(Point const a, Point const b, Point const c, Point const point);

Returns true if point is strictly inside triangle abc, false otherwise.

Concepts: Composition, practical application of fixed-point arithmetic, geometric algorithms.

What I Learned
Orthodox Canonical Form: Every class from Module 02 onwards must have a default constructor, copy constructor, copy assignment operator, and destructor .

Fixed-point representation: Storing fractional values as integers with a fixed number of fractional bits (8 bits here).

Operator overloading: Making custom types behave like built-in types while respecting the natural meaning of operators .

Stream insertion: Overloading << to integrate with std::cout.

Static members: Class-level constants and utility functions shared across instances.

C++98 compliance: No auto, no nullptr, no range-based for loops.

Testing
Each exercise includes a main.cpp that demonstrates the required functionality. Run the compiled executable and verify the output matches the expected behavior described in the subject.

Common checks:

ex00: Copy construction and assignment do not share state.

ex01: toFloat() and toInt() return correct values for positive and negative inputs.

ex02: All comparison, arithmetic, and increment/decrement operators behave as expected.

ex03: bsp returns true for interior points, false for exterior points and points on edges.

Notes
This project is a personal learning record. It is not guaranteed to pass the Moulinette. If you are also at 42 Bangkok, try implementing it yourself first.

References
42 Bangkok official CPP Module 02 subject (Intra)

Fixed-Point Numbers — Berkeley CS61C 

C++ Operator Overloading — cppreference 

Orthodox Canonical Class Form — 42 Norm documentation
