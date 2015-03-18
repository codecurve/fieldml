#summary Notes from FieldML meeting 20110323
#labels FieldMLmeetingNotes

# FieldML meeting 20110323 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley
## Prioritisation ##
### Done ###
  1. Need to fix the way the standard FieldML API is made available.  Currently, the "Library.XML" file needs to be available as a separate file.  It needs to be "baked in" to the [Tracker item 2856](https://tracker.physiomeproject.org/show_bug.cgi?id=2856).
  1. Valid ensemble identifiers: allow 0
  1. "Structure description" validation
### In Scope ###
See [Tracker item 2869](https://tracker.physiomeproject.org/show_bug.cgi?id=2869)
  1. Ranges, arbitrary ensemble members [Tracker item 2853](https://tracker.physiomeproject.org/show_bug.cgi?id=2853)
  1. Import specification, including removal of scattered references to "library. ... " etc. [Tracker item 2855](https://tracker.physiomeproject.org/show_bug.cgi?id=2855)
  1. Regions as namespaces [Tracker item 2855](https://tracker.physiomeproject.org/show_bug.cgi?id=2855)
  1. Fix misuse of bind\_index on piecewise [Tracker item 2854](https://tracker.physiomeproject.org/show_bug.cgi?id=2854)
  1. Standardise names and naming schemes, e.g. 'bindings' instead of 'binds' [Tracker item 2870](https://tracker.physiomeproject.org/show_bug.cgi?id=2870)
  1. Move to new agreed names for shapes (or bounds functions - see ref1), basis functions, point layouts.  [Tracker item 2871](https://tracker.physiomeproject.org/show_bug.cgi?id=2871)
  1. Improve continuous type especially declaration and naming of index ensembles. I.e. index ensembles are created and named within the declaration of the type. [Tracker item 2872](https://tracker.physiomeproject.org/show_bug.cgi?id=2872)
  1. (Ref2: )Fix weak syntax for mesh type; name constituent parts explicitly in XML. [Tracker item 2873](https://tracker.physiomeproject.org/show_bug.cgi?id=2873)
  1. I/O for use by distributed memory API client applications.  [Tracker item 2874](https://tracker.physiomeproject.org/show_bug.cgi?id=2874)
  1. I/O for fast block reads and writes.  [Tracker item 2874](https://tracker.physiomeproject.org/show_bug.cgi?id=2874)
  1. Subsets of ensembles (for metadata annotation) [Tracker item 2875](https://tracker.physiomeproject.org/show_bug.cgi?id=2875)
  1. Ensemble sequences (i.e. facility to specify order of an ensemble). [Tracker item 2875](https://tracker.physiomeproject.org/show_bug.cgi?id=2875)
### Defer till after end of May's release: ###
  1. Comprehensive data validation (i.e. implementation of a validation procedure is deferred.  Nevertheless, the specification document will state what is deemed valid.
  1. Concrete domains and fields
  1. Element shapes for a mesh as "bounds evaluators" from a piece-wise.
  1. (Ref1: ) Instead of ref2, go straight to structured types with generic bounds evaluators. Members of structured types will have sub-names.
  1. Improve piecewise serialisation which will be too verbose for large meshes.
  1. Ability to specify an alternative foundation library, without reference to the "standard FieldML library".  This will require full mathematical descriptions, e.g. via MathML.
  1. HDF5 for BND.
  1. Regions: nesting
  1. Regions: references to regions
  1. Regions: other structured aspects of regions
  1. Review API to make it more user friendly
  1. Arbitrary ensemble labels
## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics