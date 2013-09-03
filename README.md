lupine-ide
==========

Model-driven IDE Project for the Common Lisp Interface Manager (CLIM)


## Notes

### Concept: Tree-View Pane

#### Summary

Considering the structure of a pouplar IDE platform, such as NetBeans
or the Eclipse IDE, the IDE presents an essentially tree-structured
view of workspace resources, like in a sense of a conventional
filesystem/directory metaphor.

Considering the presentation model of CLIM, by contrast, one may
define a short "tree-view pane" model, in which, _resources_
may be presented in the typical "Folding directory" layout (a
_folding-directory tree_, of a kind) or alternately in a sort of
_"branching tree"_ or _expanded tree layout_, as for a more expanded
view of the resources denoted in the graphical tree.

#### Implementation Plan

1. Define a _tree-pane_ protocol class
2. Define a _folding-directory-tree-pane_ pane class
3. Define an _expanded-tree-pane_ pane class
4. Define a _container-node_ presentation type
5. Define a _leaf-node_ presentation type
6. Define _present_ methods for each of the _container-node_ and
   _leaf-node_ presentation types, on each of the respective _pane
   classes_

Further notes:

* The tree pane must _present_ not only the _nodes_ in a
  tree, but also the (in at least a DAG model) the _relations_ among nodes
  in the tree.

* The protocol should be designed in such a way as that it can easily
  be adapated for presentation of _directory-model resources_, such as
  ASDF sysetm definitions and conventional filesystem directories

* CLIM defines a generic graphing protocol, including the procedure,
  `format-graph-from-roots`, cf. _[CLIM Operators for Graph Formatting](http://www.lispworks.com/documentation/lw60/CLIM/html/climuser-285.htm)_ and  _[Examples of CLIM Graph Formatting](http://www.lispworks.com/documentation/lw44/CLIM/html/climguide-283.htm)_

    * McCLIM defines a function, `class-grapher` in
      file `mcclim:Apps;Listener;dev-commands`, which uses that
      function. That code is a part of the _McCLIM Lisp Listener_, and
      is defined in the ASDF system, `clim-listener` - run with
      `(clim-listener:run-listener)`. Note however that the
      interaction/input model for the class structure display commands
      may be difficult to figure out - that regardless of the name
      entered, even with STANDARD-CLASS, the input is apparently not
      complete, and the class super/subclass structure is never
      displayed. When the name is quoted initially, within the input
      field, the following is output in the Lisp's initial REPL.x


	accepting-values accept condition: Input 'STANDARD-CLASS is not of required type CLASS-NAME
	accepting-values accept condition: Input 'STANDARD-CLAS is not of required type CLASS-NAME
	accepting-values accept condition: Input 'STANDARD-CLA is not of required type CLASS-NAME
	accepting-values accept condition: Input 'STANDARD-CL is not of required type CLASS-NAME
	accepting-values accept condition: Input 'STANDARD-C is not of required type CLASS-NAME
	accepting-values accept condition: Input 'STANDARD- is not of required type CLASS-NAME
	accepting-values accept condition: Input 'STANDARD is not of required type CLASS-NAME
	accepting-values accept condition: Input 'STANDAR is not of required type CLASS-NAME
	accepting-values accept condition: Input 'STANDA is not of required type CLASS-NAME
	accepting-values accept condition: Input 'STAND is not of required type CLASS-NAME
	accepting-values accept condition: Input 'STAN is not of required type CLASS-NAME
	accepting-values accept condition: Input 'STA is not of required type CLASS-NAME
	accepting-values accept condition: Input 'ST is not of required type CLASS-NAME
	accepting-values accept condition: Input 'S is not of required type CLASS-NAME
	accepting-values accept condition: Error parsing "'" for presentation type CLASS-NAME
	accepting-values accept condition: Error parsing "" for presentation type CLASS-NAME
