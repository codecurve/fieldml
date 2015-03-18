# FieldML Requirements list - draft 20090918 #
  * Field
  * Mesh
    * Structured
    * Unstructured
  * Mesh dimension
  * Named sets, all members of set same dimension
  * Anti-requirement:
    * Mesh has faces & lines
    * Hard association between elements & nodes
  * Represent a mesh boundary
  * Serialise as XML
    * Link to Binary data e.g. HDF5, DICOM, images, vol data
  * Hierarchical
  * Reusable: i.e. can re-use meshes/functions as library components
  * Separation of basis function from element shape
  * Separation of Mesh (topology) from functions (basis) and DOF (linked to function by mapping)
  * Readability (e.g. name things in a way that is meaningful to human users)
  * Decomposition/aggregation (Distributed memory computing)
  * Physical units
  * Coordinate systems
  * Embedding
  * Later discussion: Hierarchical coordinate systems