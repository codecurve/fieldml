#summary Notes from FieldML meeting 20110304
#labels FieldMLmeetingNotes

# FieldML meeting 20110304 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Poul Nielsen

## Meeting time ##
RB: Proposed new meeting time: Monday 10am-12pm, depending on room availability and whether some clashing meetings can be moved to a different time slot.  Will aim to start on Monday 14 March.

## Previous action items ##
"**Action item** RC: Will implement in cmgui the bases that Yubing Shi (from university of Sheffield) requires (Action items was deferred from December 2010), aiming for completion by 11 March." Status: no progress since last time, still will work on this.

RC: Still working through node ordering for reference ordering, aiming to base this on the approach in Zienkiewicz as suggested by CB.  (Note: other orderings will be possible, simply by providing the required permutation of the reference ordering.)

CL: Does not want a reference ordering, since that will have the effect of promoting that.

RC: In future versions of FieldML (probably post May 2011), other orderings will be possible to define.

"**Action item** CL will update this example so that it includes the geometry field that does not use scale factors, but matches one of the scale factor approaches: arithmetic mean (i.e. just uses derivative DOF values to be with respect to ξ that are equal to multiplying the arc length derivatives by the arithmetic mean scale factors)." CL will do this today.

## Documentation of FieldML 0.3 release ##
RC: In progress.  RC Asked CL to update cube.xml example to use new standard names.

## Cubic Hermite support ##
CL: As mentioned last time, CL has an example that uses cubic hermite and scale factors.  However, it uses "evaluator="library.math.scale\_vector\_4" ", which is a "temporary hack".  This takes a scalar and a 4 vector and scales the 4 vector by the scalar.  Looking for a more general way of doing this, such that a library component such as "library.math.scale\_vector" could be declared that allows for arbitrary length vectors. (See FieldML 0.3 - Evaluator pipelines/ CubicHermite1D.xml, revision [7bb77fe474](http://code.google.com/p/fieldml/source/detail?r=7bb77fe4745bf211cf2a4ad3c2f9f2127998cacb&repo=mockups) .)

CB understands that none of the other library evaluators declare the length of the parameter vector on which they operate, and questions why this operator is an exception.

PN: MathML allows for declaration of vector lengths that operators accept. For example, number literal types, something like:
  1. Complex (Cartesian or Polar)
  1. Real
  1. Rational
  1. Integer
  1. Whole
  1. Natural
And vector like things:
# Bag
  1. Set
  1. List
  1. Vector
  1. Matrix
Also, separately, the type "Logical" i.e. Boolean.
MathML has constructors, so it may be that for example, complex can be constructed using the literal constructor in either polar or Cartesian form.

Discussion of whether ensembles are ordered.  Discussion of how ensembles are essentially enumerations, as in say C or Java.

CB: Ensembles should not need to be ordered.

RC: If sets/ensembles/enumerations in FieldML are always ordered, it is more efficient.  Also, these things are always serialised in some order.

CL: Dense parameters can be indexed by an ensemble, e.g. 1..20000.  Serialising parameters in sequence is more efficient that serialising each parameter with its index.

PN, CB, RB: Of the view that ensembles are not ordered by definition.

CB: If Ensembles are always restricted to be ordered sets, then it will hinder parallelisation.

CL: We should avoid saying "is a" for Ensemble.  Preferable: Ensemble "has a" set.  Ensemble can "have a" default ordering.

RB: See [UML diagrams](#Sketches.md).
  1. "Is a" concept that we will avoid.
  1. "has a" concept that is preferred.

There was much further discussion of this topic.

RB: Is there a way of avoiding implementing the above details, and find an approach that will suffice for the next FieldML version.

CL: Proposal  1 - Dynamic validation: Evaluators in the library have a flag indicating that there use in the evaluation pipeline can only be evaluated after the pipeline assembly by the library is complete. The use of this flag would be restricted for now to just evaluators in the standard FieldML library.

CL: Proposal 2 - Alternative: just add a special evaluator to the library.  I.e. Cubic-Hermite with scale factors.

CL: Even though we have decided to defer the implementation of general maths operators, we need to think now about how these will fit in to FieldML.

**Action Item** CL will implement proposal 2 by the next meeting, but only as mock-up.  This group will review the mock-up, and subject to the review, CL will implement this the following week.

## Next FieldML release ##
RC: Pointed out that while trying to document FieldML 0.3, some of the names used are not consistent with what was discussed prior to the release.

CL: Wants to make another FieldML soon, nominally "FieldML 0.3.2", in order to address this and other issues (e.g. availability now of externalised XML representation of standard FieldML library).

RB: We need to improve how we review the FieldML API before making releases.

## Topics to be discussed next ##
  1. Continuation of discussion of support for Hermite interpolation
  1. Atlases
  1. Hierarchical
  1. Barycentric coordinates

## Sketches ##
Preferred:


![http://wiki.fieldml.googlecode.com/hg/images/FieldML_-_Preferred_ensemble_has-a.jpg](http://wiki.fieldml.googlecode.com/hg/images/FieldML_-_Preferred_ensemble_has-a.jpg)




To be avoided:


![http://wiki.fieldml.googlecode.com/hg/images/FieldML_-_Avoid_ensemble_is-a.jpg](http://wiki.fieldml.googlecode.com/hg/images/FieldML_-_Avoid_ensemble_is-a.jpg)

## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics