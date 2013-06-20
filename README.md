Go L-BFGS-B
===========


Description
-----------

Go L-BFGS-B is software for solving numerical optimization problems
using the limited-memory (L) Broyden-Fletcher-Goldfarb-Shanno (BFGS)
algorithm with bounds constraints (B).  L-BFGS-B is a deterministic,
gradient-based algorithm for finding local minima of smooth, continuous
objective functions subject to bounds on each variable.  The bounds are
optional, so this software also solves unconstrained problems.  L-BFGS-B
is accurate and efficient for problems of 1000s of variables.  There is
more information about [L-BFGS-B on
Wikipedia](http://en.wikipedia.org/wiki/L-BFGS) or in your favorite
optimization textbook.

This software provides modern, intuitive interfaces to the [L-BFGS-B
Fortran
software](http://users.eecs.northwestern.edu/~nocedal/software.html) by
the authors of the algorithm, Jorge Nocedal et al.  Interfaces are
provided for Go (Golang), C, and Fortran 2003.


License
-------

Go L-BFGS-B is free, open source software.  You are permitted to copy
and use it however you wish.  It is released under the BSD 2-Clause
License.  See the file `LICENSE.txt` in your distribution (or [on
GitHub](https://github.com/afbarnard/go-lbfgsb/blob/master/LICENSE.txt))
for details.

The original Fortran code is released under the BSD 3-Clause License
(see `lbfgsb/License.txt` in your distribution or [on
GitHub](https://github.com/afbarnard/go-lbfgsb/blob/master/lbfgsb/License.txt)).
Since I have not modified the Fortran code, I have decided just to
incorporate it rather than re-license it.


Features
--------

Go L-BFGS-B is version 0.0.1.

This software is in the early development stages, but should have a
useful, stable, released package pretty quickly.

* Simple API allowing Go programs to easily do efficient, accurate
  optimization.  You only need to provide functions (or an object) that
  evaluate the objective function value and gradient.

* Bounds constraints allow typical, simple inequality (box) constraints
  on individual variables without needing a more specialized algorithm.

* Modern (Fortran 2003) API for original FORTRAN 77 optimizer.

* Incorporates recent improvements and corrections to L-BFGS-B
  algorithm.  (Uses L-BFGS-B version 3.0 from March, 2011.)


Go-Fortran Interface
--------------------

The architecture of this software has two main pieces: a library with a
C API (but written in modern Fortran), and a Go package providing the
functionality of the library as a Go API.  The library is designed to be
used from both Fortran and C, and so could work with other languages
besides Go.

I have endeavored to make this a good Go-Fortran interface example as
well as a useful package.  Accordingly, I have included my experimental
interface prototype code to be used for learning and experimenting with
Cgo and interfaces between Go and C (or Fortran).  However, let me know
about (or contribute!) possible improvements.


Requirements
------------

Building this software requires:

* Fortran 2003 compiler with support for procedure pointers, such as GCC
  4.4.6 or later (gfortran)

* Go 1.0


Build
-----

1. Download this package into a Go workspace.

2. Build the Fortran code into a library.

   ```shell
   $ make
   ```

   This builds a static library, `liblbfgsb.a`, that will be linked into
   your Go program.

3. Import the `go-lbfgsb` module.  Build your Go program normally.

   ```go
   import lbfgsb "github.com/afbarnard/go-lbfgsb"
   ```

   ```shell
   $ go build
   ```

I have not yet figured out how to use the Go build system to build
everything, so the Fortran code must be separately built into a library
before building any Go programs.  I hope to solve this issue and thus
enable `go get` and other conveniences.


Contact
-------

* [Aubrey Barnard](https://github.com/afbarnard)

Contributions of all sorts, patches, bugs, issues, etc. are welcome, but
are most welcome after due diligence.


Copyright (c) 2013 Aubrey Barnard.  This is free software.  See
LICENSE.txt for details.
