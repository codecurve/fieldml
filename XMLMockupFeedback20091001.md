# Details #

  * Exposed points from imported child meshes need not be on the boundary. 'boundary\_nodes' to be renamed as 'visible\_nodes'

  * Parent meshes should be able to declare new points on child meshes (cf. quadrature points, data points). This will require some way to devolve parent element-xi valuesdown to child element-xi values.

  * Having general linear maps to provide interpolation parameters from field dof vectors is highly desirable. However, there is often redundancy between element connectivity information, and element dof mapping, particularly when using n-linear interpolation. Moreover, OpenCMISS leverages that redundancy by explicitly associating field dof values with mesh connectivity points for most types of element evaluation scheme. There should be a way to reduce/eliminate such redundancy, allowing OpenCMISS (_et al._) to parse FieldML much more 'naturally' (from their own perspective).