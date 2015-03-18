# FieldML meeting 20091204 #

Revision: 34ba16968c

File QuadraticBSplineExample.java

Lines 149-178:

PN: Grouped by interpolation parameter (major), then by element (minor).  Should rather be by element, than by parameter.

Discussion by all:

Could do all as one map, add another column (similar to direction ensemble/index), takes on value 1,2 or 3 for param 1,2,3.

Action item: CL will add ODE trivial example to extend this.

PN: could use computed fields/expressions for "data compression".

Note: we are still aiming to defer computed fields till FieldML v0.3, but to aim to make FieldML v0.2 easy to extend for this change.

CB: DOF (degree of freedom) parameters should belong inside of the field.  The field should own the DOFs.

Much discussion.

PN: There may be shared DOFs.

CB: To handle shared DOFs, it should be necessary to explicitly make the shareable DOFs visible.

RB: We did something similar when we had the hand coded XML mock-ups, for the analysis of adaptive mesh refinement.

CL: However, that related to denoting which nodes were visible.

CB: The description of the number of elements and the interpolation used on each element leads naturally to the information about the required number of DOFs.

CL: Current design already addresses CB's concern.

RB: Requested CB to create stand-alone code (even in Fortran) to illustrate the design he's proposing.

CB: Also, how does it know how many DOFs are needed?

RC,CL: Asserted that the field has enough info to infer the required counts and sizes of maps and DOFs.

RB: Proposes that we alter the example to illustrate that this assertion is true: Don't to the setvalue on the DOFs object, defer this till after the declaration of the PiecewiseField on line 220 -226 is done. Then add query method calls on PiecewiseField that return the required number and sizes of maps. Set the maps, then call another query method that now uses the maps to infer the number and sizes of DOF arrays required.

RB: Proposed that on line 185 we could declare DOF array as "public" or "private".  If private, then once associated with one field, it is "illegal" to associate with any more fields later.

Much other discussion by all:

Neither "public" nor "private" should be mandatory.

Regions will have concepts of visibility (public/private).

CL: Could introduce groups (within regions) for controlling visibility within region.

CL: This is a serialisation format, concepts like visibility don't really make sense.

RB: If an application that uses FieldML for its serialisation cares about visibility, we should have a facility for serialising this.

More discussion

PN: We need to work on how information hiding will be handled.

