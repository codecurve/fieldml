#summary Notes from FieldML meeting 20110204
#labels FieldMLmeetingNotes

# FieldML meeting 20110204 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Poul Nielsen

## Discussion of GIMIAS team questions re FieldML API ##

CL: Aiming to release FieldML API v0.3 β on or before 11 Feb.

Differences:

  * Underlying FieldML spec changed to v0.3 - Support for this is done.

  * Support for semi dense data: Done

  * Support for a wider range of element types: still todo.

Deferred:

  * Support for data (XML and BND) from sources other than local disk, e.g. URL.

  * HDF5 support. CB wants this, especially for HDF5.

The above 2 deferred items will be addressed for the release that follows v0.3.

Also, see [sketches](#Sketches.md).

## Discussion of version numbering ##

Current releases are spec version 0.2 and API version 0.1.

Upcoming release: spec version 0.3, API v0.3, i.e. version numbers kept in sync.

Version numbers for release after that will be discussed at the nearer to the time, but will aim to somehow indicate the correspondence of format spec version and API version, notwithstanding backwards compatibility.

CL: No attempt has been made to make API v0.3 backwards compatible, and so it will not be able to process FieldML format v0.2 documents.

RB: v0.3 will still be a β status.

## Discussion of proposed HDF5 support ##

CL: Does not want to have to wrap the HDF5 API in order to support all the many and varied ways that HDF5 can be structured. Currently the preferred mode is that application that used FieldML API to directly read and write the BND that the FieldML describes.

After some discussion, it was agreed that basic support for directly accessing BND using FieldML API will be the goal for the release that follows after v0.3.

## Discussion of inter-conversion, FieldML to/from other formats ##

RB: It seems that GIMIAS will be converting between the formats that it currently handles and FieldML.   Perhaps this conversion will be done in memory.

CB: Suggested that if the GIMIAS developers are developing conversion functionality, this be made available as a stand-alone tool set, since it will be valuable for many users interested in using FieldML.

## Discussion about element shapes that will be included in v0.3 ##

RB: Suggested that we discuss and agree on the list of element shapes.

RC: Suggested: library.shape.**, where** is

  * line
  * square
  * triangle
  * cube
  * tetrahedron
  * wedge12
  * wedge13
  * wedge23
  * pyramid ?

RB: Suggested that these be formally made part of the specification that is released when versions of FieldML specification get released, e.g. included in the XSD if possible, otherwise in an associated human readable document that augments the specification.  All agreed. A document will be needed to discuss the bounds, e.g. triangle has ξ\_1 from 0 to 1, ξ\_2 from 0 to 1, ξ\_1 + ξ\_2 < 1.

PN: What about future proofing these names to some degree, e.g. not all line elements will range from 0 to 1, e.g. from -1 to 1.

CB: Suggested including the range info in the name, e.g. "line(0,1)"

Much discussion of this.

RC: Suggested: library.shape.unit.line, library.shape.unit.**, unit meaning 0 to 1.**

PN: Suggested:
  * library.shape.unit.1D.line
  * library.shape.unit.2D.square

> All agreed.



## Discussion about basis functions that will be included in v0.3 ##

RC and RB: Suggested that basis function / interpolation names to be supported should also be discussed.

RC: We need to have a list of standard names, and a way of constructing basis functions using tensor product of pre-defined basis functions.

PN: Suggested we just define 1D starting set, and then a mechanism for constructing from there.

RC: But there will be a delay before agreement can be reached on how tensor product construction is specified.

After much discussion, the following was proposed: library.basis.#d.unit.**, where # is the dimension (i.e. #d = 1d, 2d or 3d, not planning higher dimensions yet), and** is one of the following:
  * linear\_lagrange or lagrange1
  * quadratic\_lagrange or lagrange2
  * cubic\_lagrange or lagrange3

RB: The order of the basis functions that are part of the named set needs to be specified.

RC: This should just be in the "natural order" that comes from "fastest in ξ\_1".

RB: This does then just require specifying the order for the 1D basis function sets.

RC: Pre-packaged tensor product proposal:
  * bilinear\_lagrange or lagrange1\_lagrange1
  * lagrange1\_lagrange3

PN: Or just library.basis.2d.lagrange implies bilinear

CB: Prefers bilinear\_lagrange

CL: Suggested that synonyms/redundancy i.e. having both is fine.

PN: library.basis.2d.simplex1 : uses linear bases.  library.basis.2d.simplex2 uses quadratic bases, homogenously.

RC: For wedges, need to specify which pair of ξ's are the simplex plane, and the third is then the direction.

PN: Suggested: 13Simplex2\_2Lagrange1 means quadratic simplex in ξ\_1, ξ\_3 plane, linear lagrange in ξ\_2 direction.

**Action item** RC will write up the first draft of the above, and mail it to the fieldml-developers mailing list.

## Sketches ##

![http://wiki.fieldml.googlecode.com/hg/images/GIMIAS_and_FieldML_and_cmgui_-_schematic.jpg](http://wiki.fieldml.googlecode.com/hg/images/GIMIAS_and_FieldML_and_cmgui_-_schematic.jpg)

## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics