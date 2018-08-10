# Google Summer Of Code 2018 Final Report
## Overview
The project, spanned over a period of slightly over 3 months, consisted in improving the way in SageMath checks for graph isomorphism.  
The plan was first implementing an interface to one of the fastest, if not the fastest, automorphism and isomorphism checking open-source library, Nauty, an interface that could turn useful both as a standalone isomorphism checker and as a benchmarking tool.  
Subsequently, an implementation would be made of the Weisfeiler-Lehman (WL) method: such method, described in [this 1968 paper][1], computes the coherent closure of an arbitrary (di)graph in polynomial time; in simpler terms, the method starts with an initial partition of the vertices (resp. edges) of a graph G and refines this partition through several passes, until the partition resulting by a refinement round is equal to the one the round started with; this resulting, final partition, has the property of being equal to or refined by the orbits (resp. orbitals) of the original graph's automorphism group, and we say WL recognizes a graph if the resulting partition is equal to its orbits (resp. orbitals).  
While this is called the Weisfeiler-Lehman algorithm, it's more correct to say family of algorithms, since for any positive *k* a version of WL can be defined which recognizes strictly more graphs than any other, lower order, WL[^CFI].  

As said above, scope of the project was implementing this family of algorithms, or at least part of it: in particular, the idea was implementing a generic, parametric method that could allow to run any order of Weisfeiler-Lehman if at all possible; since it was not possible to determine if such a thing could be done before enough research was done on how to actually implement WL, a fallback plan was prepared, consisting in manually implementing, separately, the first three orders of WL (the choice of restricting it to the first 3 was made due to the results presented in this paper[^planar]).

Lastly, the project provided for the implementation of an isomorphism checking method which could use k-WL to distinguish graphs in a faster way.



[^CFI]: Jin-yi Cai, Martin Fürer, and Neil Immerman. An optimal lower bound on the number of variables for graph identifications. Combinatorica, 12(4):389–410, 1992
[^planar]: S. Kiefer, I. Ponomarenko and P. Schweitzer, "The Weisfeiler-Leman dimension of planar graphs is at most 3," 2017 32nd Annual ACM/IEEE Symposium on Logic in Computer Science (LICS), Reykjavik, 2017, pp. 1-12.  
doi: 10.1109/LICS.2017.8005107