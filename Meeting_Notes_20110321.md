#summary Notes from FieldML meeting 20110321
#labels FieldMLmeetingNotes

# FieldML meeting 20110321 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley

## Previous action items ##
"**Action item** RC: Will implement in cmgui the bases that Yubing Shi (from university of Sheffield) requires (Action items was deferred from December 2010), aiming for completion by 11 March." Deferred until after Richard returns from Europe trip which is end of March.

## General ##
Due to other project pressures, this was a short meeting.  Next meeting on Wednesday 23 March.
RC: Away until Wednesday 6 April 2011.

## Follow up from last time's discussion ##
RB: Discussions were had with CL, RC and CB, and we resolved that we will find a way to avoid having to do I/O operations twice when reading or writing identical bulk numerical data (BND).  CL proposed separating the XML specification of the location of the BND, this could be called a "data resource".  This would allow for rationalisation in the case where an ensemble membership and ordering both referred to the same data resource.  Even if CL's proposal is not the approach adopted, a method that does allow for an equivalent optimisation will be adopted.


## Prioritisation ##
The group discussed which items need to be done for the May release.
  1. Need to fix the way the standard FieldML API is made available.  Currently, the "Library.XML" file needs to be available as a separate file.  It needs to be "baked in" to the (see tracker item 2856).
  1. Ranges, arbitrary ensemble members
  1. Valid ensemble identifiers start at 0
  1. Import specification
  1. Regions
  1. Fix misuse of bind\_index on piecewise
  1. Standardise names and naming schemes, e.g. 'bindings' instead of 'binds'
  1. Move to new agreed names for shapes (or bounds functions - see ref1), basis functions, point layouts.
  1. Improve continuous type especially declaration and naming of index ensembles. I.e. index ensembles are created and named within the declaration of the type.
  1. Improve piecewise serialisation which will be too verbose for large meshes.
  1. (Ref2: )Fix weak syntax for mesh type; name constituent parts explicitly in XML.
  1. (Ref1: ) Instead of ref2, go straight to structured types with generic bounds evaluators. Members of structured types will have sub-names.
  1. Import specification to remove scattered references to "library.**" etc.
  1. I/O for use by distributed memory.
  1. Concrete domains and fields
  1. Subsets of ensembles (for metadata annotation)**

The above list still needs to be prioritised, and some items will be deferred.  Items that we have already decided to defer till after end of May's release:
  1. Ability to specify an alternative foundation library, without reference to the "standard FieldML library".  This will require full mathematical descriptions, e.g. via MathML.
  1. HDF5 for BND.
  1. Review API to make it more user friendly

**Action Item**: RB: update plan in tracker so that v0.3 FieldML item can be closed, open new 0.4 item etc.

## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics