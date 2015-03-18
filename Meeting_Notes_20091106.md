# FieldML meeting 20091106 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Poul Nielsen(most of meeting)


General notes:


RB: New design method being used: prototype in Java, produce corresponding UML diagrams semi-automatically; and automatically produce XML "mockups" from test code. See http://code.google.com/p/fieldml-java2/

RB: Prior to each FieldML meeting, each person of this FieldML work-group needs to commit at least 2 hours per week to understanding the latest changes to the Java/UML/Mockups.  Meet with Caton during the week and work together to get the Java/UML/XML design to represent your view point.



Discussion of current revision of design (revision 5d1faf99f9):

PN: disagrees with having separate ContinuousDomain and EnsembleDomain

RB: points out that global…. are destined for "standard library".

CB: Params for x field depend on what type of interpolation.

RB, CL, RC: FieldML XML will not be dependent on sequence in which it is read.  Bulk numerical data will be read from separate bulk numerical data files.  CB: But any implementation requires knowledge of interpolation per element before it can handle the parameter arrays for that interpolation.

CB: Field DOFs are private to that field.  Much discussion.  Resolution: Parameter sets will be allowed to be private to field.


Mating of element to shape missing.


CL: We can add a type of Map that can augment an existing Map with additional mapping: e.g Map1={ (1;2;3)-->(4.34; 32.93; 0.032)}, Map2 = Map1 + {(4;5)-->(0.0; -225.03)}


FEMField: Mapping from element to evaluator, essentially the same for x and y, and when evaluating, reusing basis function evaluations at same xi coordinates is potentially a common optimisation.  Can we combine?


CL: Idea: having one map that is the same as another map except in a few of the mappings:

e.g. Map 1: all are bilinear

Map 2: same as Map 1 except, element 77 uses biquadratic.

Note: this is different from augmenting a map.


Will probably come back to physical units in a later version of FieldML.  Currently just a stub attribute on Domain.  Won’t necessarily be an attribute of Domain though.


Action item: CL: Other "interpolation" types will be added to example: constant per element, "globally" constant, cubic-Hermite.  These will illustrate how differing param counts will be handled.