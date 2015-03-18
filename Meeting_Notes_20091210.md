# FieldML meeting 20091210 #

Poul Nielsen, Richard Christie, Caton Little, Chris Bradley, Randall Britten, Steve Niederer

Notes taken by Randall Britten

RB: David Nordsletten's example: discontinuous field, mentioned at this morning's OpenCMISS telecon.  RB pointed out at that time that current FieldML design seems to address David's requirement.  CB queried this.  Discussed by all, and agreed that current FieldML design does already address this via its use of fairly general mapping system. CB sees these as essentially just using versions.

CB, RC: Suggested the need for labelling DOFs in DOF lists, e.g. so that validation is possible, e.g. if a particular interpolation scheme requires certain DOFs for derivatives as one of its parameters, one can ensure that DOFs intended for values aren't erroneously used for that parameter.

PN: Suggests that this should rather be implemented by means of mapping from all-purpose list to the special purpose lists.

RC: Concerned that this adds an extra layer.

CB: Implementation would be free to use a different internal representation.

CL: Current work on decoupling DOFs from Field. Example: different parameters for the same field, e.g. at different points in time.

RB: Another example: Cardiac Atlas: Same "Field Template" (CL's term for this), but different DOFs each time a patient specific model is created.

CB, PN: When a solver returns a list of numbers. May need to reverse the mapping.

RB: Concerned that applications that read and write FieldML will be forced to always rearrange ordering and grouping of DOF lists in internal physical memory representation vs physical representation in serialisation format.

PN: However, current designs use of general map allows a wide range of physical layouts.

PN: Separation of scale factors are different from DOFs.

RB: Current design reflects separation.

CB: OpenCMISS and similar applications will need to "concatenate/merge" DOFs and scale factors to construct the matrices it uses for solvers.

RB: This indicates again that there will be a burden for this type of application, rearranging physical ordering.

SN: Old CMISS has everything in one array, sub parts of the array have different meaning, this makes it very different to debug. Having everything rearranged compared to how they were represented in FieldML serialisation creates this difficulty.

PN: However, many different applications will have own preferred internal ordering, and so re-arrangement is inevitable.

CB: One way to alleviate this is to provide helper methods that make it easier to interrogate what a particular item in an array represents.

SN: Data file reading, if slow, can be costly: massive data set size being read into HPC where usage time cost is relatively high.

Also discussed: handling distributed memory.

RC: Queried whether global DOF numbering is possible in distributed memory implementations.

CB, SN: Yes, this is already implemented in OpenCMISS.

CB: A description of DOF ordering is necessary, so that applications can re-order if necessary.

RB: Is the sparse array that represents the mapping sufficient, or do we need more semantic information in the Field Template?

Discussed by all: conclusion, we will include more semantic information in FieldTemplate.  FieldTemplate is a bit like a "header", however, it is per field, rather than per file.

Different DOF list structuring, by these options: Nodes, Constant, Element, Grid, GaussPoint.

Todo: CL, modify java code so that EnsembleDomain entries can be strings.


Discussion about API (after main meeting)

Richard Christie, Caton Little, Chris Bradley, Randall Britten

RB: 2 Options for API:

Option 1:

  * Includes implementation
  * Allows for evaluation
  * Stands alone, can be used from client apps, e.g. : OpenCMISS, cmgui, GIMIAS
  * Issue: complicated: requires change notification.

Option 2:
  * Serialisation only (i.e. input from serialised form, output to serialised form)

Planned implementation sequence: first do Option 2.  Later, work on Option 1.

See sketch:
http://wiki.fieldml.googlecode.com/hg/images/API%20options%20discussion%2020091210.jpg?r=2f3a8fb08ef6e73508708a14babda048e107665f




