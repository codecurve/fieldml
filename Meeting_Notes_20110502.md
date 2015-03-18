#summary Notes from FieldML meeting 20110502
#labels FieldMLmeetingNotes

# FieldML meeting 20110502 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley

## Publications ##
This was discussed, agreed that we would provide information for people to contact us to request the "Concepts and Serialisation" document.

## Recent progress ##
CL: Resolved all the remaining tracker items under [tracker item 2869](https://tracker.physiomeproject.org/show_bug.cgi?id=2869).
## Data Objects tag usage discussion ##
Discussion of [triquadratic.heart.test.xml](http://code.google.com/p/fieldml/source/browse/input/triquadratic+heart+test.xml?spec=svn.testbed-scala.f1f61899458e841acc327387bd7f492fdf2df99d&repo=testbed-scala&r=f1f61899458e841acc327387bd7f492fdf2df99d) at revision f1f61899458e.

Most of discussion focussed on details of the DataObject tag, and the way other parts of FieldML refer to this tag.
For example, on lines 55-65, ranges are stored as integer data in a data object.

CB: It would be best if there are convenience functions to provide either direct access to the underlying integer data or higher level access the resulting integer list.

RC: Suggested a mock-up of an HDF5 data object.

CL: Issue with whether we support HDF5 parallel.

RC: Data object should specify whether data is integer or double.

CL: Has deferred doing this due to the complexity of implementing it and current time constraint.

## Identifiers for components of the mesh structured type ##
CL: Currently "heart.mesh.variable.xi" is implicitly declared by "heart.mesh" and "xi".  Seeking suggestions for an improved approach.

CL: currently the "Variable" tag is essentially unused, and just annotation.  For example, on [line 165](http://code.google.com/p/fieldml/source/browse/input/triquadratic+heart+test.xml?repo=testbed-scala&r=f1f61899458e841acc327387bd7f492fdf2df99d#166), the variables are meant to match the corresponding "bind" tags, but the API does not validate this.

## Discussion on representation of numerical precision within data objects ##
CL: Currently precision (e.g. 32bit float, 64 bit float) is not specified. API currently just defaults to machine default C Integer. We could use standard C types.

Discussion of whether we should use 32-bit integers or 64-bit by default.

CL: Current uses of integer: Ensemble item, Error, FieldML object handle, FieldML session.

## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics