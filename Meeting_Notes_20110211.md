#summary Notes from FieldML meeting 20110211
#labels FieldMLmeetingNotes

# FieldML meeting 20110211 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Poul Nielsen

## Previous action items ##
"RC will write up the first draft of the above, and mail it to the fieldml-developers mailing list." **Done.**

## Release of v0.3 of API and spec ##
CL: This will be done today.

RB: List of element shape names and as discussed on FieldML mailing list will be used.  This serves as a first draft of the list, and may be revised in future releases.

CL: Confirmed this.

PN: Not happy with this list, but understands that it represents a first draft, and is OK for this release.

## Re-ordering ##
RC: Suggests that node ordering default is fastest in lowest ξ.

CB: Software that uses FieldML is likely to have its own node ordering.  API needs to be able to re-arrange (i.e. "swizzle") DOFs as necessary. This is an important feature.

RB: Swizzle support can be added to FieldML later.  Asked CL what current OpenCMISS example that has been implemented does regarding conflicting node ordering.

CL: Although a swizzle is used in the FieldML file, this is to re-order the data in the BND serialisation into FieldML canonical order (which currently is as RC has suggested).  OpenCMISS and cmgui are both using canonical order.

CB: Clarified: for basis functions sets formed via tensor products, OpenCMISS and cmgui use the same node ordering.  However, for simplex types, the node ordering differs.

Much discussion by all of the best way of specifying alternates for node orderings.

## Discussion of "OpenCMISS implementation of FieldML" ##
CB: Example: temperature field, varying with time, geometry field, product of the two fields, e.g. temperature varying with space and time.

RC, CB: OpenCMISS terminology "Field variable" is equivalent to FieldML terminology "field".

Some discussion about how imports will work in future versions of FieldML, and how name clashes can be avoided.  Currently, FieldML 0.2 and soon to be released FieldML 0.3, use implicit importing of the library.  Future versions will probably require explicitly importing the library.

RB: Imports simply need to follow a system similar to CellML whereby components imported are assigned a name by the import statement within the namespace of the importer.

CB: Wants API to be able to describe the basis function sets in the library in the same way that it will be able to describe user defined basis function sets, where the user definition may be "from scratch", and hence no reference needs to the definitions in the library.

Much discussion.  All agree that the API will at some future point support the above feature.  In addition, it will allow for user definition based on swizzles and other variations of the library i.e. make reference to the library.

CB: Disagrees completely that swizzles and reference to a particular implemetation the library is good or standard FieldML practice. The library is just a FieldML implementation and should not be viewed as the favoured approach. One of the big things for FieldML is to be an interchange format and thus we must resist enforcing a particular view on users. Their way is just as valid as the libraries way and that they should happily be able to have their own implementation of the libary. There should not be any need for any swizzles in FieldML.

CB: Feels that this is a very high priority. At the moment we cannot even read/write Simplex elements in native formats between OpenCMISS and cmgui.

## Hermite interpolation ##
RC: Handling of Hermite style interpolation is a high priority.

CL: Already implemented, with the caveat that there is no indication of which DOFs and their corresponding basis functions represent derivatives.

RC: Hermite bases are usable without scale factors, scale factors should be added in the parameter map.

CB: Scale factors allow DOFs to have physical meaning, rather than just being derivatives with respect to ξ.  For example, this is important when describing interface boundary conditions.

RB: Current mock-up (done about a year ago) just treated scale factors as DOFs, hence has a redundancy, e.g. in a 2D case, the scale factor of the cross-derivative is the multiple of the two scale factors of the derivatives of each of the 2 directions.  Note: scale factors are just the terms that result from the chain rule of differentiation.

RC: FieldML already supports flexible mapping including from 'physically meaningful' derivative DOFs using CMISS-style 'scale factors', we just haven't standardised our convention for doing so. [later: Our Hermite basis examples should include mapping of derivatives w.r.t. arbitrary patch coordinate systems into the element chart coordinate system; the so-called 'physically meaningful' approach is just one example, where the patch coordinate length scale equals that of the global coordinate system & axes may be aligned with arcs of the element edges.](Added.md)

RC: Two possible designs for Hermite bases, which include value and derivative DOFs:

  1. Simple linear array of DOFs, indexed by one index variable.
  1. More structured array, indexed with node number and derivative

RC: Suggests keeping both ideas alive for a while, until it is clearer which way is better.

PN: Simple linear array should be preferred for now, since it is just that: simpler.

RC: Mesh refinement: a case where scale factors change, e.g. halving element length changes scale factors by a factor of 2.

Discussion on whether it is valid to change scale factors during a simulation involving deformation.

PN: Changing scale factors changes the atlas, i.e. the same element number and ξ coordinates now refer to different material points.

RC: Points out that the new atlas has actually gained new material points and lost material points.

RC: Disagrees with CB's assertion that scale factors must be applied to make DOFs 'physically meaningful' (i.e. derivative DOFs must be w.r.t. to a coordinate system with same scales as global coordinates) in order to prescribe boundary conditions when solving. It just makes it simpler to apply when the user-prescribed boundary value is exactly given at a node and in the case of a derivative when it is in the arc direction, i.e. it is just an optimisation. When this is not the case, prescribed values can simply be transformed using the chain rule into their influence on one or more DOFs. This also goes for the general situation where values are prescribed away from nodes and/or not aligned with arc directions. Admittedly these may require other techniques to apply the B.C. to the system, such as Lagrange multipliers or penalty methods.

CB: Disagrees with the disagree! If you do not have dofs involving spatial derivatives w.r.t. a physical rather than a mathematical parameter then your boundary conditions on these DOFs change if you change your mesh. This is not something that should be considered good or desirable. The boundary conditions for a particular problem should be the same regardless of how the domain is meshed. This is not just an optimisation. In addition in coupled problems that involve DOFs from a different region then it is extremely important to ensure that you can interpret the magnitude of the DOF value in different regions the same way. If you cannot interpret the magnitudes the same then you cannot put them in the same equations without knowledge of the scaling used in the different regions. Having the same scaling in different regions and/or different parts of the mesh allows you to interpret the magnitude of the DOFs the same way without any other knowledge. I agree that other physical derivatives could be used but arc length is a simple measure that is invariant under coordinate transformation. I also agree that if you are very careful you can construct systems of equations using the combined DOF\*scale factor product. However, extreme care is needed and the numbers that come out are not useful to a physical modeller. I disagree that the use of scale factors is incompatiable with more general mappings of global derivatives to element derivatives or that they have to be aligned with the coordinate axes.

**Action item** CL will create a FieldML example that can be read into OpenCMISS via the FieldML API of a 1D cubic-hermite mesh with a few elements geometric.

## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics