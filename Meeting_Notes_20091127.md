# FieldML meeting 20091127 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Poul Nielsen

FieldML-java2 revision 344abbac19

RB: Tri-quad example: although element setup using coplanar along the trifid may not be of real world value, it would be of benefit, because it will illustrate a more convincing general linear map (GLM).

RB and CL will rework triquad to achieve this.

CL: Hanging node example already shows this. Nevertheless we will rework the tri-quad example.

RB: We should anticipate the use of computed fields in the way we do the GLM.

RC, PN: Refinement and hanging node.

CL: Hanging node example has redundant map.  Should just map from global to element Dofs.

CB: Prefers if Hanging Node example does not have intermediate map, since OpenCMISS implementation would find that burdensome, since it would repeatedly be using the intermediate map, and thus would cache its values, which results in a lot of extra storage.

CB: Isn't the intermediate map introducing an "extra concept".

All others: no, intermediate map is just another instance of "map concept", hence does not increase number of concepts.

CB: Lines 114 to 123: Redundant 1.0's.

RB: Use "default"

CL: No, default has to be 0, otherwise mapping isn't sparse, and is in fact wrong, i.e. values requested away from band would be 1.0.

Turns out, looking at the code, CL is right, there are two different types of mapping.

7 nodes to 8 nodes uses mapping that has index and multiplier, "ContinuousParameters class".

8 nodes to element nodes has just index mapping (lines 130-143), "EnsembleParameters class".

Discussion on connectivity:

PN: Should not mix mapping with connectivity. Info shouldn't be constrained to be at nodes.

CL: OpenCMISS does not force info to be carried at nodes, it totally depends on the interpolation type.

PN: Should not use mappings to infer connectivity.  Connectivity info needs to be explicitly expressed.

RB: Need an example:

PN: Bezier: quadratic B-spline example, each "node" affects 3 elements.

Things to do next/ in future, in this order:

  * B-spline example: params aren't from individual nodes. RB suggested this test of connectivity with dy/dt=f(t) where f is field value. CB suggested we do this first, since it addresses a key design issue.
  * CL, RB: TriQuad using GLM spanning nods.
  * Hanging nodes removing redundant map, note that this does not imply that having the intermediate map is disallowed.
  * Use BiCubicHermite in Hanging nodes example
  * Fourier basis for a signal processing example.
  * RB: Illustrate decomposition.
