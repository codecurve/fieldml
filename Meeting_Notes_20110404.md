#summary Notes from FieldML meeting 20110404
#labels FieldMLmeetingNotes

# FieldML meeting 20110404 #

Present: Randall Britten, Caton Little, Poul Nielsen, Chris Bradley
## Recent progress ##
CL: As committed first implementation of "imports".  Just evaluators and types can be imported.  They are just functional declarations; hence an import does not "instantiate". The facility to "instantiate" has been deferred.

PN: Concerned that a consistent approach must be taken, so that when we do introduce instantiation.

RB: Wants to avoid the "limitation" that CellML has where "instantiation" and definition import are done with one statement.

PN: Explained the rationale for the CellML approach, but since FieldML is different, supports taking a different approach if necessary.

CL: Should "region" be rather named "namespace"?  Currently, that is all they are used for.

Much discussion

CL: Data objects: in progress.

CL: Showed mock-up that is working with head revision of FieldML-API, see http://code.google.com/p/fieldml/source/browse/FieldML%200.3%20-%20Library%20Imports/triquadratic%20heart.xml?repo=mockups (i.e. Revision 37900f7b0525 of "Mock-ups" repository).

## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics
