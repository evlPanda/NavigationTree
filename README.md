# NavigationTree
WorkCentre Navigation Tree. Replacement for the delivered one.

![Navigation Tree](https://i.imgur.com/FKd6Q8h.png)

The Tree Class is primarily used to generate an HTML tree, but you can use it to create trees of anything. CreateNode() can be overridden.

The Tree Class uses the Model View Control pattern. 

```
:Utilities:Tree:Node  Model
:Utilities:Tree:HTML  View
:Utilities:Tree:Tree  Controller
```

Note that tree branches have a level, while leaves do not. (Node.level)
Leaves will always appear under the previous branch, before other branches.
i.e. Sort your tree!

```
+ branch lev. 1
  - leaf
  - leaf
  + branch lev. 2
    - leaf
    - leaf
    + branch lev. 3 
      - leaf
      - leaf
```

You can add infinite levels.

Example use:

```
import NavigationTree:Tree;

Component NavigationTree:Tree &Tree;

If &Tree <> Null Then
   Return;
End-If;

&Tree = create NavigationTree:Tree();

&node = &Tree.getNewNode("branch", 1);
&node.label = "Australia";
&Tree.addNode(&node);

&node = &Tree.getNewNode("branch", 2);
&node.label = "New South Wales";
&Tree.addNode(&node);

&node = &Tree.getNewNode("leaf", 0);
&node.label = "Sydney";
&node.link = "www.sydney.com";
&Tree.addNode(&node);

&node = &Tree.getNewNode("leaf", 0);
&node.label = "Newcastle";
&node.link = "www.newcastle.com";
&Tree.addNode(&node);

&node = &Tree.getNewNode("branch", 2);
&node.label = "Queensland";
&Tree.addNode(&node);

&node = &Tree.getNewNode("leaf", 0);
&node.label = "Brisbane";
&node.link = "www.brisbane.com";
&Tree.addNode(&node);

A_RECORD.HTMLAREA.Value = &Tree.getHTML();

```

Easy-peasy, lemon squeezy.
