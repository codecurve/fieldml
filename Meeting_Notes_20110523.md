#summary Notes from FieldML meeting 20110523
#labels FieldMLmeetingNotes

# FieldML meeting 20110523 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley

## Agenda ##
Progress towards release of FieldML API 0.4

Node ordering for simplex elements

Consistency of FieldML with CellML

## Progress towards release of FieldML API 0.4 ##
CL: FieldML API v0.4 release candidate 2 (RC2) made available as source May 17.

RB: Documentation required: CL to generate Doxygen and include a zip of the Doxygen; also a Readme.txt or equivalent document that explains how to check out the source and briefly documents a simple example, with reference to the Doxygen.

RC: Will remove API description from the FieldML format concepts document (still work in progress).

## Node ordering for simplex elements ##
RB: An example is required of FieldML data interchange between OpenCMISS and cmgui of a mesh that uses 3D simplex elements in order to validate the FieldML simplex element support.

RC: The elements will need to be 3D simplex quadratic, since node numbering re-ordering needs to be validated.

CL: Showed FieldML\_Library.xml as at version 499d8d33e87b.  See line 282 URL: http://code.google.com/p/fieldml/source/browse/FieldML_Library.xml?repo=api&r=8e18b2926f12301dadaab9f29f37e71422ef9eca#282

RC: Described that he and CL have only implemented the node ordering of cmgui (since one other FEM package also uses this ordering: "GetFem").

CB: Not happy that the ordering that OpenCMISS uses has been omitted. The current node ordering in RC2 is arbitrary.

RC: Stated that his intention is that other node orderings require the application to permute/swizzle the node ordering; and that future version of FieldML will allow explicit description of node ordering so that arbitrary node ordering can be used.

Long discussion.

PN and CL: Suggested that the monomial matrix be used to specify a basis.

RB: Nevertheless, that is a solution for a future version of FieldML and we require a decision for 0.4.

All agreed that we will include the Zienkiewicz/OpenCMISS ordering.

RC: Wants to then also include VTK ordering, so that in total v0.4 has 3 orderings for triquadratic simplex elements, similarly for wedges.

CL: Does not view FieldML\_library.xml as **the** standard FieldML library, but rather as just an arbitrary FieldML library.

CB: Agrees.

**Action Item**: CL: will add VTC and Zienkiewicz/OpenCMISS node orderings to quadratic simplex elements evaluators specified in FieldML\_library.xml.

## CellML consistency ##
RB: Asked if there were any other suggestions of minor element or attribute name changes that could be done for 0.4. Two recent changes were made for this: the use of xlink for imports, and the change of the element name "Variable" to "Argument".

RB: The "import" element in FieldML is quite different from CellML's "import" element.  In CellML, "import" also has instantiation semantics. However, FieldML's use of "import" is more consistent with other computing usages, e.g. Java and Scala.

RC: Import might be useful for creating local aliases, which would mean it no longer has the common import semantics.

## Other ##
RC: Proposed removal of the EnsembleType associated with each element evaluator in the library. This change will not be made for v0.4.

**Action Item**: RC: create a tracker item proposing this for FieldML 0.5.

URL for FieldML XSD and library.xml:

Discussed, and agreed that these will be hosted on www.fieldml.org once released.

Action Item**: CB: will organise that the XSD and library.xml are hosted on www.fieldml.org.**

## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics

DSL: Domain Specific Language