#summary Notes from FieldML meeting 20110128
#labels FieldMLmeetingNotes

# FieldML meeting 20110128 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Poul Nielsen

## Discussion of project roles and responsibility for next season ##
Discussion to clarify who is responsible for ensuring team meets EuHeart deliverable date for FieldML release version (tentatively v0.3, possibly will be called v1.0)

Conclusion: will follow same as last year, RB has overall responsibility for the EuHeart deliverable.

Work will continue on improving FieldML even after the EuHeart deliverable.  PN has a James Cook Fellowship to work on FieldML for 2 years.

## Discussion of version naming ##
RB: If we release a version of FieldML and the API in March, we will call this v0.3, and name any release after that appropriately.

## Discussion of what is included in v0.3 ##
RC: API needs to be able to parse and write to data from arbitrary streams, not just file system, e.g. data in RAM, Internet URLs.

CL: Work has been done towards, this, further work still required.

PN: Asked about HDF5 support.

CL: Still has not been worked on.

CB: Suggests support for NetCDF.

## Discussion of overlapping atlases ##
PN: Need to allow for overlapping charts.

CB: Concerned about performance costs of supporting arbitrary overlapping charts.

PN: Example use case: Radial Basis functions with finite support.

CB: Similar to mesh-free methods.

PN: Example: branching structure of 1D "elements".

RB: Why 1D?

PN: Locally 1D.

RB: Except at bifurcation.

PN: Yes! This is a main point of difference from differential geometry, where there is a flat Euclidian space that locally approximates the manifold at all points of the manifold.

PN: Example of 2 different atlases that share some of their charts.

PN: Last week there was discussion about whether:
  1. All charts have same dimension, and this is equal to the dimension of the manifold. CB: Points out again that it is common practice in FEM to mix dimensions of elements. RB: Pointed out that the current conceptual design does cater for meshes with mixed dimension of elements, but by means of interfacing between manifolds.
  1. Are properties of atlases different from properties of fields?

RC: We should consider relaxing the single value constraint of field values for handling partitioning of unity, which may help unify the concept of a field and atlas.

PN: Perhaps field objects and atlas objects will share a common super class, and we can handle the commonality in that way.

RC: Fields tend not to have finite value domains.

PN: But for example, a field that represents a substance concentration can't have negative values.

RC: Cmgui presents atlases as fields.

RB: One way to still support this would be to keep atlas separate from field (even if they share a common super class), but then just have a special purpose field that one can attach to and atlas to get the present field aspects of the atlas object.

CL: Like a "companion object".

RC: There will be a bijection between two atlases on the same manifold; it is similar to embedding a field.  This uses the exact mechanism that is used for producing field values.

RC: Bijection must be possible, but it does not have to be directly implemented, e.g. cyclical is sufficient: a->b->c->a

RB: We should use terminology that indicates that we can't always validate whether or not the mappings are bijective, and we expect already that some mappings that are not bijective will still be used commonly in practice.  E.g. collapsing nodes on a square-like element to make triangles, and then mapping to a triangular element.  Suggests we say "supposedly bijective".

PN: Collapsed nodes can be avoided.  They were only used because CMISS limitation.

CB: OpenCMISS has addressed this, but many packages out there have the same limitation.

CB: Boundary element method intentionally introduces singularities in order to cancel out singularities in the Green's functions.

After some discussion, consensus was that API would log a warning whenever mappings are encountered that cannot be validated as being bijections.

PN: Suggested that next Friday we discuss hierarchical meshes.

CB: Requested that we meet on Tuesday 1 Feb 10am to catch up on the changes CL has made to the FieldML design representation, etc.

RB: Emphasised that we will soon have to limit the range of revision of the technical design that we will allow as we approach the EuHeart delete date.  After that we can re-open the design as we continue work to improve FieldML.  This is similar to what we had to do last year.

## Sketches ##
![http://wiki.fieldml.googlecode.com/hg/images/Branching_vessels_example.jpg](http://wiki.fieldml.googlecode.com/hg/images/Branching_vessels_example.jpg)

![http://wiki.fieldml.googlecode.com/hg/images/Overlapping_atlases.jpg](http://wiki.fieldml.googlecode.com/hg/images/Overlapping_atlases.jpg)

![http://wiki.fieldml.googlecode.com/hg/images/Use_case_for_overlapping_atlases_-_aerofoil.jpg](http://wiki.fieldml.googlecode.com/hg/images/Use_case_for_overlapping_atlases_-_aerofoil.jpg)