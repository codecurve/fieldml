#summary Notes from FieldML meeting 20110509
#labels FieldMLmeetingNotes

# FieldML meeting 20110509 #

Present: Randall Britten, Caton Little, Chris Bradley
## Recent progress ##
CL: Showed "20110506 - Data objects with shared sources and HDF5 support/ triquadratic heart.xml" at revision e861f553942a of mock-ups repository, demonstrating being able to specify data sources per "file". See this [example](http://code.google.com/p/fieldml/source/browse/20110506+-+Data+objects+with+shared+sources+and+HDF5+support/triquadratic+heart.xml?repo=mockups&r=e861f553942ae2352ae1cd745dcfc52e8ec01b52).

CL: This example also has a mock-up of how HDF5 data sources would be specified, however, HDF5 support will only be added after the end of May release.

CL: Discussed with Richard the possibility of removing "Variables" except for abstract evaluator.

CB: Queried why 

&lt;variable&gt;

 tag is never a local variable.

RB: Similar to discussion on locally bound variables in CellML, see [tracker item 2902](https://tracker.physiomeproject.org/show_bug.cgi?id=2902). (Note that on comment 0, "require that bound variables appear" should read "require that bound variables NOT appear".
## Release timing ##
CB: Will finish data objects by 13 May.  After that, will make the release of version 0.4, so that release is available by 20 May.  After that, will update OpenCMISS example that reads FieldML mesh, solves, and writes solution to FieldML.  Richard will update cmgui so that cmgui can read and render the FieldML output from OpenCMISS.

## Glossary ##
NSWSI: Not sure who said it

BND: Bulk numerical data

DOF: Degree of freedom

ROI: Region of interest

FEM: Finite element method

CFD: Computational Fluid Dynamics