#summary Notes from FieldML meeting 20110314
#labels FieldMLmeetingNotes

# FieldML meeting 20110314 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Peter Hunter, Poul Nielsen

## Previous action items ##
"**Action item** RC: Will implement in cmgui the bases that Yubing Shi (from university of Sheffield) requires (Action items was deferred from December 2010), aiming for completion by 11 March." Deferred until after Richard returns from Europe trip which is end of March.

RC: The required element shapes are supported, and point layout for simplex elements corresponds to Zienkiewicz.  Still has to work out scheme for standardising interpolation function ordering, e.g. in case where shape is product of simplex with Cartesian.    Cmgui approach: From lowest to highest ξ, but if higher ξ's are in the same simplex as lower ξ, they "jump the queue", e.g. Simplex 2D in ξ\_1 and ξ\_3, tensor product with ξ\_2 line-element: first, the basis functions over ξ\_1 and ξ\_3, then ξ\_2.

"**Action item** CL will update this example so that it includes the geometry field that does not use scale factors, but matches one of the scale factor approaches: arithmetic mean (i.e. just uses derivative DOF values to be with respect to ξ that are equal to multiplying the arc length derivatives by the arithmetic mean scale factors)." Done

"CL: Proposal 2 - Alternative: just add a special evaluator to the library.  I.e. Cubic-Hermite with scale factors. **Action Item** CL will implement proposal 2 by the next meeting, but only as mock-up.  This group will review the mock-up, and subject to the review, CL will implement this the following week.".  Done.  See Library0.3.xml (although note that this is not version 0.3, but a later version, version number still to be decided upon."

## Consensus process ##
Discussion of how we handle cases where consensus is difficult.

RB: We are now in the phase where only incremental changes can be made.  Where there is contention on fundamentals, these will be noted in the associated documentation, mainly in a separate section.

RC: Draft of FieldML documentation follows the above format.

## Discussion of possible numbering of Ensemble members ##
This was discussed in an informal meeting Friday, with CL, RC and CB.

RC: Proposes that ensembles which consist of a set of integers have the canonical ordering of the integers as the default order.

CB: Enforcing default ordering conflicts with support for parallel I/O. Parallel output might result in integer ensembles being written in a different order, e.g. "4,5,6,1,2,3"

RC: Points out that there is a way for an alternative order to be specified.

CL: Current API only allows for contiguous description of ensembles that are labelled using integer identifiers.

RB: Suggested that ordering is simply always specified, whether it be user supplied, or based on canonical integer ordering.

CL: Summarised the debate: the question is whether the API's constructor of an ensemble allows the arbitrary orders to be specified in the same call, or whether a separate call is required.

RC: Concerned about premature optimisation.

RB: Suggested as an alternative, that the API allows for construction of unordered sets or of ordered sets as a subclass of unordered sets.  Likewise, serialisation allows for using the membership serialisation as the ordering serialisation.  This allows CB's parallelisation case to be supported.

Much further discussion.
## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics