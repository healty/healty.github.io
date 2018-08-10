---
layout: default
title: Checking graph isomorphism using the Weisfeiler-Lehman algorithm
---
# Google Summer Of Code 2018 Final Report
## Overview
The project, spanned over a period of slightly over 3 months, consisted in improving the way in SageMath checks for graph isomorphism.  
The plan was first implementing an interface to one of the fastest, if not the fastest, automorphism and isomorphism checking open-source library, Nauty, an interface that could turn useful both as a standalone isomorphism checker and as a benchmarking tool.  
Subsequently, an implementation would be made of the Weisfeiler-Lehman (WL) method: such method, described in [this 1968 paper][1], computes the coherent closure of an arbitrary (di)graph in polynomial time; in simpler terms, the method starts with an initial partition of the vertices (resp. edges) of a graph G and refines this partition through several passes, until the partition resulting by a refinement round is equal to the one the round started with; this resulting, final partition, has the property of being equal to or refined by the orbits (resp. orbitals) of the original graph's automorphism group, and we say WL recognizes a graph if the resulting partition is equal to its orbits (resp. orbitals).  
While this is called the Weisfeiler-Lehman algorithm, it's more correct to say family of algorithms, since for any positive *k* a version of WL can be defined which recognizes strictly more graphs than any other lower order WL[^1]


[^1] Jin-yi Cai, Martin Fürer, and Neil Immerman. An optimal lower bound on the number of variables for graph identifications. Combinatorica, 12(4):389–410, 1992
