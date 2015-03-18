#summary Notes from FieldML meeting 20110225
#labels FieldMLmeetingNotes

# FieldML meeting 20110225 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Poul Nielsen

## Previous action items ##
"**Action item** RC: Will implement in cmgui the bases that Yubing Shi (from university of Sheffield) requires (Action items was deferred from December 2010), aiming for completion by 11 March." Status: still in progress.

"**Action item** CB: Will create an OpenCMISS example to illustrate the need for and use of scale factors.  If this is done early enough in the week, he will pass this on to the group, and then CL will create a mock-up of the FieldML representation of the input mesh and of the output mesh and solution field."

Discussions were held during the week.  CB provided a mesh of 1D elements embedded in a 2D RC coordinate system.  RB provided an updated version of the example so that the "unit scaling" example matched the "arithmetic mean" example, but setting derivative DOF values to be with respect to ξ.  CL created a FieldML 0.3 equivalent, see [revision 7bb77fe474](http://code.google.com/p/fieldml/source/detail?r=7bb77fe4745bf211cf2a4ad3c2f9f2127998cacb&repo=mockups) of the Mock-ups repository.

**New Action item** CL will update this example so that it includes the geometry field that does not use scale factors, but matches one of the scale factor approaches: arithmetic mean (i.e. just uses derivative DOF values to be with respect to ξ that are equal to multiplying the arc length derivatives by the arithmetic mean scale factors).

## Metadata ##
The members of the group attended the CellML Metadata specification presentation by Mike Cooling held just prior to the FieldML meeting.  The current plan is to use virtually the identical metadata standard for FieldML.

## Support for Hermite interpolation ##
RB: Proposed:
  1. We add Hermite interpolation to the list of standard interpolation (CubicHermite at least).
  1. This will allow for "naked" use of Hermite interpolation.
  1. To allow for use of scale factors, we use the approach already demonstrated by CL for serialising scale factor numerical values such that they are chained into the evaluation pipeline, so that the intended field evaluation works as scale factors have traditionally been interpreted.
  1. We include RDF metadata to annotate that the parameterEvaluator that contains the scale factors are just that.  We have yet to define the metadata statements that will be used to represent this.  Initially this will be a draft proposal.

Note: the need for scale factors is still under debate.  Their use seems to be so that DOFs can be provided as derivatives with respect to arc-length rather than with respect to ξ.  However, it seems possible to easily convert between arc length derivatives and derivatives with respect to ξ, but this has to be confirmed, since there must be a reason that they have been used consistently for so long at the ABI.

CB: Insists that not using scale factors will make certain problem types impractical, especially those that interface meshes.

PN: Scale factors should more appropriately be associated with the atlas.  So above approach is to be seen as an interim measure.

All agreed that above approach is to be seen as an interim measure.

## FieldML 0.3 release - remaining tasks ##
RC: Has been working on a document describing the 0.3 format, and will distribute a draft to the FieldML working group soon.



## Topics to be discussed next ##
  1. Continuation of discussion of support for Hermite interpolation
  1. Atlases
  1. Hierarchical
  1. Barycentric coordinates


## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics