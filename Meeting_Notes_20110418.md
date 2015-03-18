#summary Notes from FieldML meeting 20110418
#labels FieldMLmeetingNotes

# FieldML meeting 20110418 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Poul Nielsen
## Publications ##
RC: Mailed "FieldML 0.3 Concepts and Serialisation\_DRAFT v2.doc" on Friday for rest of group to review.

RB: Concerned that releasing RC's document will jeopardise the intended publication of a FieldML research manuscript in the near future.  This does not mean that we withhold the document from interested parties, but rather that we only provide it on request, and subject to conditions that will not jeopardise our ability to publish it.

This was discussed, agreed that we would provide information for people to contact us to request the "Concepts and Serialisation" document.

## Recent progress ##
CL: Resolved most of the tracker items under [tracker item 2869](https://tracker.physiomeproject.org/show_bug.cgi?id=2869).

RC: Finalising workings of simplex elements and corresponding basis functions.

## Discussion of "Concepts and Serialisation" document ##
### Ensemble labels ###
CB: Document says Ensemble entries are integers, but these should just be allowed to be arbitrary string labels.

RC: What are practical real world use-cases?

RB: Gene expression data where each gene has a string label.

PN: Agrees with CB.

RC: Integers will always be required.

RB: Binary formats tend to require numerical bulk data.

CL: Examples: VTK binary and HDF5.

RB: Much of the debate arises from a tension between the FieldML concepts and the need for practical implementation.

RB: Proposed separation of conceptual design from technical design; but that this formalisation be deferred till after May release. This was accepted.

### Subsets ###
CB: Does not support the statement made in the document that says that subsets should be implemented as Boolean valued fields.

PN: Agrees with CB, that mathematical operations on sets should be directly supported, rather than indirectly via fields or evaluators.

RB: Compared the approach suggested by RC with that suggested recently by Andrew Miller for CellML 1.2 initial conditions and reset rules.  Andrew suggested that both of these could be expressed in a way that complies with the current CellML 1.1 specification using the MathML. E.g. all MathML "equations" are essentially statements that the solver must ensure hold true.  Thus, general Boolean expressions could be constructed that equate to initial conditions and reset rules, e.g. NOT (t=0) OR dy/dt=yp0 for an initial value on a derivative; infinitesimally-delayed(y)<10 OR y=0 for a reset rule.  The similarity between this approach and RC's suggestion is that it allows a wide range of concepts to be supported without introducing new language features.  While at first it seems that it is complicated to parse, a parser need only support certain cases, and thus simply needs to parse for cases that match the appropriate templates.

RB: Suggested that there may be a way to resolve the issue in the "Concepts and Serialisation" document that does not commit to a future design path.

There was much discussion about this, and individual meetings will be held during the week to attempt to resolve this.

## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics