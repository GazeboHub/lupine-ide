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
