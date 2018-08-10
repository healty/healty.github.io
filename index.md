# Overview
The project, spanned over a period of slightly over 3 months, consisted in improving the way in SageMath checks for graph isomorphism.  
The plan was first implementing an interface to one of the fastest, if not the fastest, automorphism and isomorphism checking open-source library, Nauty, an interface that could turn useful both as a standalone isomorphism checker and as a benchmarking tool.  
Subsequently, an implementation would be made of the Weisfeiler-Lehman (WL) method: such method, described in [this 1968 paper][1], computes the coherent closure of an arbitrary (di)graph in polynomial time; in simpler terms, the method starts with an initial partition of the vertices (resp. edges) of a graph G and refines this partition through several passes, until the partition resulting by a refinement round is equal to the one the round started with; this resulting, final partition, has the property of being equal to or refined by the orbits (resp. orbitals) of the original graph's automorphism group, and we say WL recognizes a graph if the resulting partition is equal to its orbits (resp. orbitals).  
While this is called the Weisfeiler-Lehman algorithm, it's more correct to say family of algorithms, since for any positive *k* a version of WL can be defined which recognizes strictly more graphs than any other, lower order, WL[^CFI].  

As said above, scope of the project was implementing this family of algorithms, or at least part of it: in particular, the idea was implementing a generic, parametric method that could allow to run any order of Weisfeiler-Lehman if at all possible; since it was not possible to determine if such a thing could be done before enough research was done on how to actually implement WL, a fallback plan was prepared, consisting in manually implementing, separately, the first three orders of WL (the choice of restricting it to the first 3 was made due to the results presented in this paper[^planar]).

Lastly, the project provided for the implementation of an isomorphism checking method which could use k-WL to distinguish graphs in a faster way.

# Trac Tickets

SageMath development process is based around git and an issue tracking system called Trac. Specifically, every improvement, bug/bugfix or new functionality must be reported in a ticket on (https://trac.sagemath.org) with a detailed description, where it will be then discussed, possibly implemented/solved and then reviewed, to then be merged if the process went through successfully.

This means that the work I've done has been divided in tickets on the Trac system, and so will be reported here with a similar structure and organized in chronological order.

To access a particular piece of work described, and thus its in-depth description, discussion and code (which is stored in a separate branch for each ticket), it will suffice to click on the title of its subsection.

In one particular instance, the ticket's original associated branch was changed due to a complete rework of the implementation required, which rendered obsolete the previous code. This means that two subsections of this document will reference the same ticket, but since the branch is still online, the subsection relative to the old implementation will link directly to said branch, skipping the ticket altogether. 

# [\#25391 - Issues in compiling SageMath](https://trac.sagemath.org/ticket/25391)
The subject of the first ticket I've worked on, and also the first difficulty I encountered during my project, was getting SageMath to run at all on my system.  
I started working on a PC running Fedora 28 64bit with gcc 8.1, a fairly updated setup, and this caused a few issues in compiling SageMath's source code.  
In particular, as can be seen in the ticket's description, I had troubles with python3, python2 and linbox packages.  
Now, in all honesty, I could have worked around the issue completely by switching to an older version of the distro, or to another distro altogether, but I thought this could be a good first contribution to SageMath, and the perfect way to gain familiarity with the Trac system and Sage's internal structure and workings before I started working on code that was more relevant to my project.

The actual fixes to the issues I encountered were fairly simple, but debugging the system required a lot of effort, and all the help I could get from my mentor, Dmitrii Pasechnik.  
While at first, after a couple of weeks of work, I was able to produce patches to be included in Sage that could solve the problems listed in the ticket, after some time the upstream maintainers of the packages produced updated versions with fixes included; the ticket, even if fairly successful in providing a solution to the issue, was thus closed because not needed once the packages inside Sage had been updated too.

Still, I consider this ticket very important in my journey, since it really helped me understand how the library I was working on was structured, which parts were where and what to modify and how. In a sense, it served as kind of a workshop before starting work on the real thing.


---
[1]: https://www.iti.zcu.cz/wl2018/pdf/wl_paper_translation.pdf
[^CFI]: Jin-yi Cai, Martin Fürer, and Neil Immerman. An optimal lower bound on the number of variables for graph identifications. Combinatorica, 12(4):389–410, 1992
[^planar]: S. Kiefer, I. Ponomarenko and P. Schweitzer, "The Weisfeiler-Leman dimension of planar graphs is at most 3," 2017 32nd Annual ACM/IEEE Symposium on Logic in Computer Science (LICS), Reykjavik, 2017, pp. 1-12. doi: 10.1109/LICS.2017.8005107
