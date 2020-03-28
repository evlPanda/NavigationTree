# NavigationTree
WorkCentre Navigation Tree. Replacement for the delivered one.

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
	import RX_UTILS_PKG:Factory;
	import RX_UTILS_PKG:NavigationTree:Tree;

  Local RX_UTILS_PKG:Factory &Factory;
	Local RX_UTILS_PKG:NavigationTree:Tree &Tree;
	
	&Factory = create RX_UTILS_PKG:Factory();
	&Tree = &Factory.Build("Tree", null);

    &node = &Tree.GetNewNode("branch", 1);
    &node.label = "Australia";             <<< country
    &Tree.AddNode(&node);

    &node = &Tree.GetNewNode("branch", 2);
    &node.label = "New South Wales";       <<< state
    &Tree.AddNode(&node);

    &node = &Tree.GetNewNode("leaf", 0);
    &node.label = "Sydney";                <<< city
    &node.link = "www.sydney.com";
    &Tree.AddNode(&node);

    &node = &Tree.GetNewNode("leaf", 0);
    &node.label = "Newcastle";             <<< city
    &node.link = "www.newcastle.com";
    &Tree.AddNode(&node);

    &node = &Tree.GetNewNode("branch", 2);
    &node.label = "Queensland";            <<< state
    &Tree.AddNode(&node);

    &node = &Tree.GetNewNode("leaf", 0);
    &node.label = "Brisbane";              <<< city
    &node.link = "www.brisbane.com";
    &Tree.AddNode(&node);

    SOME_RECORD.HTML_AREA.Value = &Tree.GetHTML();

```

Easy-peasy, lemon squeezy.
