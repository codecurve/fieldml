# FieldML meeting 20091113 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Poul Nielsen

Started looking at latest version of FieldmlTest.xml

All agreed: BilinearQuadEvaluator tag is not what we want, what we want is a generic Evaluator tag with an attribute that points at the relevant library

CB: Need coordinate system.

CL, RB: Why are coordinates needed at an early stage?

CL: Forgot to produce UML diagram

CL: Briefly presented latest version of FieldmlTest.xml

Critiques:

RC: Need to specify basis functions, and RC wants basis functions to be fields as well.

RB: What is next?

CL: Coordinate fields.

RC: test\_mesh.coordinates.xy could have been defined as the set-product of test\_mesh.coordinates.x and test\_mesh.coordinates.y.

See also notes on revision e5b76cb612 on fieldml-java2

Discussion regarding how to associate physical units with coordinate systems.

CL: Physical units should be associated with field value definition.

RB: Last week we said that the next thing would be to add Bi-quadradic-lagrange and Bi-cubic-hermite interpolation.  Only Bi-quadradic-lagrange was done, so suggestion is to have a Bi-cubic-hermite be the next thing that is worked on.

RB: Suggested that we work on Bi-cubic-hermite for next week and spend rest of meeting discussing the design that will be done for Bi-cubic-hermite, all agreed.

PN: Suggested this example as the example that we should work on (see picture of whiteboard).
![http://wiki.fieldml.googlecode.com/hg/images/Example%20mesh%20ThreeXiDirectionsIn2D.jpg](http://wiki.fieldml.googlecode.com/hg/images/Example%20mesh%20ThreeXiDirectionsIn2D.jpg)

RC: How are physical units associated with parameters? Lead to some discussion.

Discussion of Poul’s design from some months ago, see [Poul's diagram](http://fieldml-java2.googlecode.com/hg/trunk/doc/2009-08-20%203%20Element%20Hanging%202D%20Hermite3.pdf)

