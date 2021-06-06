### Homework 1: Getting Started

A good software engineer strives to write programs that are fast, correct, and maintainable.

* Maintainability: comment your code, use meaningful variable names, insert whitespaces,
  and follow a consistent style.

* Code organization: break up large functions into smaller subroutines, write reusable
  helper functions, and avoid duplicate code.

* Version control: write descriptive commit messages, and commit your changes frequently,
  but dont commit anything which doesn't compile.

* Assertions: frequently make assertions within your code so that you know quickly when
  something goes wrong.

#### Preprocessing with clang
`clang -E preprocess.c`
`clang -E -DNDEBUG preprocess.c`


#### AddressSanitizer
Quick memory error checker that uses compiler instrumentation and a run-time library.
It can detect a wide variety of bugs (including memory leaks).
`make ASAN=1`

#### Valgrind
Another tool for checking memory leaks. If you want to check a program but are not
able to instrument it, Valgrind is a good option for detecting memory bugs.
`valgrind ./,atrox_multiply -p`

Valgrind only detects memory bugs that affect outputs


#### Code coverage
Add to compiler flags:
`-fprofile-arcs -ftest-coverage`

Add to linker flags:
`--coverage`

Then run program. This will create a number of .gcda and .gcno files.

Use llvm-cov utility on individual files to check their coverage:
`llvm-cov gcov testbed.c`

Hash-marks indicate that lines were never executed. Other lines have numbers that
indicate how many times the line was executed.
