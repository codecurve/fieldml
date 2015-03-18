#summary Notes from FieldML meeting 20110530
#labels FieldMLmeetingNotes

# FieldML meeting 20110530 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Poul Nielsen
## Agenda ##
Progress towards release of FieldML API 0.4

## Follow up of previous action items ##
**Previous action item**: CL: will add VTC and Zienkiewicz/OpenCMISS node orderings to quadratic simplex elements evaluators specified in FieldML\_library.xml.

CL: Done. Added only triquadratic simplex elements.

CB: Wanted to have tri-cubic simplex elements added as well.

This was discussed, and the conclusion was that we will add this in the near future to a possible 0.4.1 version.

There was discussion about where two different conventions end up using the same ordering for certain cases, and whether it is better to add both.

RC: Does not want to add what are essentially duplicates.

CB: Is not happy with omitting some of the orderings, since they are currently just string names for evaluators, and future versions of FieldML will allow arbitrary evaluators and orderings, which mean that different names for equivalent definitions will certainly be created.

CL: But we may want to distinguiush between cases where the duplication is incidental versus intentional.

**Previous action item**: RC: create a tracker item proposing this for FieldML 0.5.

Still to be done.

**Previous action item**: CB: will organise that the XSD and library.xml are hosted on www.fieldml.org.

There was a misunderstanding on how this would be done.  This was discussed, and all agreed that by the end of 30 May, NZST, this will either have been arranged by CB, or we will take the interim approach of hosting XSD and library on Google code for v0.4's release.  CB does not expect that there will be any problems and thinks that it is unlikely that we will need to host XSD and library on Google code.  All prefer hosting on www.fieldml.org.

RB: Had a long discussion with Peter Hunter earlier regarding plans to consolidate the infrastructure that hosts sites for FieldML, CellML, and then in future, OpenCMISS, cmgui, OpenCell, PMR2 project info (not to be confused with Physiome PMR2 instance which is separately hosted on models.physiomeproject.org), etc.

Discussion about what the future plans are for hosting the FieldML library XML.

CL: Currently API has a hard-coded "cache" of the contents of the FieldML library XML file, but this is the only special treatment of "the FieldML library".

## Progress towards release of FieldML API 0.4 ##
RC: Will make DRAFT 1 of the "FieldML v0.4 Concepts and Serialisation" document available before the end of today.

All agreed that the document will initially be available only to the FieldML group for internal review, to be completed by the end of this week (i.e. by the end of 3 June, NZST).  After this, it will be mailed to selected interested persons, with the request to keep confidential, since we will publish a paper that is largely based on its contents.  We will now commence work to create a manuscript for journal publication.

CL: Ready to make release.  Release will consist of a zip file of the source code for the API being made available on the SourceForge file download area; as well as the generated Doxygen for the API, to be hosted on fieldml.sourceforge.org.

RC: The API source and Doxygen are not sufficient on their own for a user to make use of the FieldML API.  The "FieldML v0.4 Concepts and Serialisation" document is essential.

RB: This is why the internal embargo is only until 3 June.

Known issues:

CL: Full data exchange from OpenCMISS to cmgu using FieldML v0.4 not demonstrated yet.  Still working on OpenCMISS example that writes FieldML. Not expecting any problems.

RB: If any problems are discovered, we will fix these, and make a follow up release.

RC: Has completed work to so that head revision of cmgui no reads FieldML using the v0.4 API, for some examples.  Will make a developer pre-release binary of cmgui available publicly. Current issue is that libxml clean-up approach is not consistent current cmgui/FieldML style.  Expecting that this will be resolved, by the end of this week, and that the developer release can be made available.

RB: Thanked RC for his effort in providing some review of the FieldML API.  Thanked CL for his hard work in getting this ready for the release date.

## Brief discussion of roadmap for FieldML 0.5 (i.e. next "major" version) ##
  1. Domains and Fields
  1. Streaming I/O
  1. Full HDF5 support
  1. Dependency evaluation

This will be discussed in more depth.


## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics

DSL: Domain Specific Language