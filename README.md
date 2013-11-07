polyCub [`@CRAN`](http://CRAN.R-project.org/package=polyCub)
============================================================

An `R` package providing methods for **cubature** (numerical integration) **over
polygonal domains**. Note that for cubature over simple hypercubes, the packages
[`cubature`](http://CRAN.R-project.org/package=cubature)
and [`R2Cuba`](http://CRAN.R-project.org/package=R2Cuba)
might be more appropriate (cf.
[`CRAN Task View: Numerical Mathematics`](http://CRAN.R-project.org/view=NumericalMathematics)).

The function `polyCub()` is the main entry point of the package. It is a
wrapper around the following specific cubature methods.

#### General-purpose cubature rules:
* Two-dimensional midpoint rule (a simple wrapper around
`spatstat::as.im.function`) 
* Product Gauss cubature as proposed by [Sommariva and Vianello (2007,
*Bit Numerical Mathematics*, **47** (2), 441-453)](http://dx.doi.org/10.1007/s10543-007-0131-2)

#### Cubature rules for specific types of functions:
* Efficient adaptive cubature for *isotropic* functions via line `integrate()`
along the polygon boundary
* Quasi-exact methods specific to the integration of the
*bivariate Gaussian density* over polygonal and circular domains


A Short History of the Package
------------------------------
For any spatio-temporal point process model, the likelihood contains an integral of the conditional intensity function over the observation region. If this is a polygon, analytical solutions are only available for trivial cases of the intensity function -- thus the need of a cubature method over polygonal domains.

My Master's Thesis (2010) on ["Spatio-Temporal Infectious Disease Epidemiology based on Point Processes"](http://epub.ub.uni-muenchen.de/11703/) is the origin of this package. Section 3.2 therein offers a more detailed description and benchmark experiment of some of the above cubature methods (and others).

The implementation then went into the [`surveillance`](http://CRAN.R-project.org/package=surveillance) package, where it is used to fit `twinstim` self-exciting two-component spatio-temporal point process models described in [Meyer et al (2012, *Biometrics*, **68** (2), 607-616)](http://dx.doi.org/10.1111/j.1541-0420.2011.01684.x).
In May 2013, I decided to move the cubature functionality into a stand-alone package, since it might be useful for other projects as well -- and here we are.
