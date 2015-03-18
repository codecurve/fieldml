#summary Notes from FieldML meeting 20110218
#labels FieldMLmeetingNotes

# FieldML meeting 20110218 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Poul Nielsen

## Previous action items ##
"**Action item** CL will create a FieldML example that can be read into OpenCMISS via the FieldML API of a 1D cubic-hermite mesh with a few elements
> geometric." Done.

## Discussion of Simplex/Tetrahedral elements ##

CB: Showed a diagram from Zienkiewicz, Figure 4.18.  Explained how there is a natural node numbering, which stems from formulating basis functions
based on area coordinates.

RC, PN: Do not like area coordinates, since they are redundant, e.g. for a 2D simplex triangle, only 2 parameters are needed, but area coordinates
> provide 3 coordinates.

RB: We have all along planned to include in a future version of FieldML, the facility to specify low level descriptions of element shapes, coordinates,
> basis function definitions etc.  However, we should probably defer this till after the May deadline.

CB: Feels that low level descriptions are a high priority and should not be deferred. Feels that use of barycentric coordinates is widespread.

CL: To a large extent, many of the required features to allow for low level description are already available.  However, automatic translation between
> two different systems is a different issue.

Discussion of generalised barycentric coordinates, regarding their prevalence and the priority for FieldML support.

### Discussion of collapsed elements ###
CL: Mailed out an example to illustrate a FieldML representation of a mesh using cubic-Hermite elements.  The mail included an externalised FieldML
> library (library.xml).

RC: Regarding library.xml, Richard does not want to specify all collapsed elements and bases in library, due to combinatorial explosion.

PN: Agrees, wants to balance including features to support what users demand with keeping FieldML design clean. Collapsed elements are only collapsed
> for a particular field.

CL: The question is, where do you put the information that describes the collapse? Do you put it with the collapsed field, or with the underlying
> element shape and set of basis functions?

RC: FieldML could be strict, prohibiting users from describing collapsed charts.

General discussion, highlighting the 3 options:
  1. FieldML expresses anything the author wants.
  1. User allowed to specify "unclean" charts, basis functions sets, API can translate
  1. API does not support translation; user of API has to translate.

Discussion of "synonym problem": the expressive power of a language can result in multiple ways of using the language to represent the same thing.

CB: API must make it easier rather than harder to translate.

## Discussion of scope of FieldML ##

CL: Is FieldML for translation or serialisation?

**Action item** RC: Will implement in cmgui the bases that Yubing Shi (from university of Sheffield) requires (Action items was deferred from
December 2010), aiming for completion by 11 March.

PN: Drew a sketch showing the possible views of what the scope of FieldML is, see [sketches](#Sketches.md).

CB: Wants to include translation in set of tools provided as part of FieldML toolset.

Some discussion of how we assess what external users/potential users requirements are, and how we prioritise these.  Also, will users
"be surprised" when the next version of FieldML is released in May?

RB: We have already signalled to the FieldML community of potential users what the direction of FieldML development is, based on the fact
that we released a β version in May 2010.

RB: Suggests that we document which requirements each FieldML release meets, as well as which requirements have been identified but not
> met, and what the FieldML work-group's current prioritisation of the outstanding requirements is.

## Scale factors ##
CB: CL's cubic Hermite example is not useful for illustrating the approach used by OpenCMISS.

RB: Suggested CB create an example in OpenCMISS that we can discuss next week so that debates about how the issues that the use of scale
factors addresses can be discussed in more detail.

Discussion about the use of scale factors, and alternative approaches.

**Action item** CB: Will create an OpenCMISS example to illustrate the need for and use of scale factors.  If this is done early enough
in the week, he will pass this on to the group, and then CL will create a mock-up of the FieldML representation of the input mesh and
of the output mesh and solution field.

## Topics to be discussed next ##
  1. Support for Hermite interpolation, specifically dealing with scale factors ( continued)
  1. Atlases
  1. Hierarchical
  1. Barycentric coordinates

## Sketches ##

![http://wiki.fieldml.googlecode.com/hg/images/Scope_of_FieldML_20110218PN.jpg](http://wiki.fieldml.googlecode.com/hg/images/Scope_of_FieldML_20110218PN.jpg)


## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics