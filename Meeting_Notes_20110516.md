#summary Notes from FieldML meeting 20110516
#labels FieldMLmeetingNotes

# FieldML meeting 20110516 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley
## Agenda ##
Node ordering
Consistency of FieldML with CellML
Variables

## Node ordering ##
Previously, CB suggested the Zienkiewicz node ordering.

RC: Finds Zienkiewicz difficult to document.  Cmgui and GetFem use "fastest in lowest ξ".

RB: Had a conversation with CB.  CB doesn't mind which node ordering we use for version 0.4, since he views the "library.xml" as just one of the libraries that will be used with FieldML.  RB views this as **the** standard library with respect to which all other orderings will have to be specified.  However, nothing in version 0.4 makes either of these views set in stone, so this can be revised after the end of May release.

RC: Will look at VTK's node orderings.

Discussion of whether using alternative libraries to express alternative node orderings etc.

RB: Similar issue to ModML, where main model is expressed in a DSL (Domain Specific Language). Libraries are used to transform the model into core ModML.  However, if transformation library changes, then meaning of DSL changes.  Likewise, in FieldML, if main model is relative to a non-standard library, then meaning of model is sensitive to changes in the library.

RC: This is why it is important to house models using version control repositories such as PMR2.

CB is of the understanding that in future versions, FieldML will allow for node ordering to be described using more fundamental concepts, rather than relying on interpretations being hard coded in the FieldML API.

All agreed.

CB: Automated conversion from version 0.4 to next version is required.

All agreed. In other words, use of version 0.4 should be encouraged, even though further fundamental changes to the format are planned, since migration tools will be provided by the FieldML group.

RC: This is one of the reasons why attempting to find the best suitable names for element shapes and interpolation bases is important.

## Variable element ##
CL: Updated XSD to specify which attributes are mandatory and which are optional.

## Release timing ##
CL: Still needs to add simplex and removed "library." Will make a release candidate at the end of   today (zip file of API source with FieldML library and XSD).

RC: will perform main review while implementing v0.4 in cmgui.

RC: Some initial comments: more Doxygen required.

CL: Obvious parts of API do not have Doxygen, non-obvious parts do have Doxygen.

RC: Suggested CL add more Doxygen, rechecking which cases might be non-obvious.

RC: Is string free provided.

CL: Yes.

RC: Should another version of the document for v0.3 be made? Perhaps we should just focus on documenting 0.4 now.

All agreed to just move forward with the v0.4 document.

## Consistency of FieldML with CellML ##
RB: Recently we changed imports and data sources to use xlink to refer to external resources. Other possible tag and attribute names that could be made consistent or renamed if not consistent: e.g. Variables. Obviously, if tag names are similar but semantics are not, but there is nevertheless good justification for the name then it should be retained.

Discussion also of other tag names.

Discussion, all agreed: ParametersEvaluator to be renamed to ParameterEvaluator.

Alternatives for Variable: Place holder, slot, argument

CL: ArgumentEvaluator means Variables becomes Arguments.

CL: will do this after making RC1 available.

RB: Can FieldML API be made "internal" to OpenCMISS API as CL suggests, prior to end of May?

This was discussed; we opted not to do this until after the release of v0.4.


## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics

DSL: Domain Specific Language