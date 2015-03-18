# FieldML meeting 20091123 #

Present: Randall Britten, Caton Little, Richard Christie, Chris Bradley, Poul Nielsen

We now have a way of visualising 2D surface meshes: via Collada export, and then import to Blender (see image at end of this page).

The focus was on the "tri-quad example", coded in BicubicHermiteTriquadTest.java.

The initial approach taken by Caton so far essentially equates to having something akin to versions at the centre node.  This is required in some cases.  However, the purpose of Poul's "tri-quad challenge" was to address derivative continuity at the centre node. Thus, there are fewer degrees of freedom, than if values are made available at the centre node via versions in such a way that it is essentially equivalent to each element having its own independent parameters for derivatives.

We agreed to look into ways of coupling derivative degrees of freedom at the centre node.  We also agreed that the approach that we would take to do this would be via Poul's "general linear map" method.

![http://wiki.fieldml.googlecode.com/hg/images/Attempte%20at%20Example%20mesh%20ThreeXiDirectionsIn2D.png](http://wiki.fieldml.googlecode.com/hg/images/Attempte%20at%20Example%20mesh%20ThreeXiDirectionsIn2D.png)